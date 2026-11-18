#dmv-pattern_mining_with_information_theory

# Algorithme

SQS-SEARCH fouille une base de séquences d'événements par compression sans ensemble de candidats fixé d'avance : les candidats sont fabriqués à partir du modèle courant, examinés un par un, et la table n'est modifiée que si la description totale raccourcit. C'est la transposition aux séquences du principe de l'[[Algorithme SLIM]], lui-même version progressive de l'[[Algorithme KRIMP]].

**Entrée** : une base de séquences $D$.

**Sortie** : un ensemble $\mathcal{P}$ de motifs significatifs.

```text
SQS-SEARCH(D)
entrée : base de séquences D
sortie : motifs significatifs 𝒫

1  𝒫 ← ∅ ; A ← SQS(D, ∅) ;
2  tant que des changements ont lieu faire
3      F ← ∅ ;
4      pour chaque P de CT faire ajouter ESTIMATE(P, A, D) à F ;
5      pour chaque X de F ordonné par l'estimation faire
6          si L(D, 𝒫 ∪ X) < L(D, 𝒫) alors
7              𝒫 ← PRUNE(𝒫 ∪ X, D, faux) ;
8          si X a été ajouté alors tester récursivement X augmenté des événements apparaissant dans les trous ;
9      𝒫 ← PRUNE(𝒫, D, vrai) ;
10 ordonner les motifs X de G par L(D, 𝒫) - L(D, 𝒫 privé de X) ;
11 retourner 𝒫 ;
```

# Interprétation

L'initialisation pose deux choses : l'ensemble $\mathcal{P}$ des motifs retenus part vide, et $A$ reçoit le résultat de l'appel $\text{SQS}(D, \emptyset)$. Ce que cet appel produit n'est pas précisé ; $A$ ne réapparaît ensuite qu'en argument de `ESTIMATE` à la ligne 4, où il sert de modèle de référence pour estimer les candidats sur la base $D$. Le modèle que l'algorithme construit, enrichit et retourne est $\mathcal{P}$.

Chaque passage dans la boucle construit un vivier de candidats à partir des entrées de la table :

- la ligne 4 parcourt les entrées de la [[Table de codes pour séquences d'événements|table de codes]] courante, notée $CT$, et range dans $\mathcal{F}$ l'estimation `ESTIMATE` de chacune, calculée sur le modèle $A$ et la base $D$ ;
- la ligne 5 examine ces candidats dans l'ordre de leur estimation, du plus prometteur au moins prometteur : c'est l'équivalent de l'ordre du gain chez SLIM, qui évite d'essayer les ajouts au hasard ;
- la ligne 6 soumet chaque candidat au test MDL, en comparant la [[Longueur de description d'une base de séquences|longueur de description]] de la base encodée avec la table augmentée à celle de la table courante ;
- la ligne 7 élague la table acceptée, car l'arrivée d'un motif modifie les usages, donc les [[Longueur des codes de motifs et de trous|longueurs de code]], des entrées déjà présentes ; c'est le même mécanisme que l'[[Élagage après acceptation d'une table de codes]] ;
- la ligne 8 exploite la structure propre aux séquences : un motif peut enjamber des positions, et les événements qui occupent ses trous sont autant de prolongements possibles du motif accepté, testés récursivement ;
- la ligne 9 élague de nouveau la table une fois le vivier épuisé, avant de repartir pour un tour si quelque chose a changé.

La comparaison de la ligne 10 mesure ce que coûterait le retrait d'un motif : l'écart $L(D, \mathcal{P}) - L(D, \mathcal{P} \setminus X)$ croît avec l'importance du motif dans la compression, et le tri classe les motifs retenus par ce critère.

# Propriétés

- **Any-time** : le processus peut être interrompu à toute itération et rend le meilleur modèle construit jusque-là, sans attendre l'examen d'un vivier complet.
- **Sans paramètre** : aucun seuil de support minimal n'est requis, la comparaison des longueurs de description jouant le rôle de critère d'acceptation.
- **Génération guidée par le modèle** : les candidats ne sont pas extraits de la base par un algorithme de fouille préalable, ils dérivent des entrées de la table de codes courante.

# Remarque

La ligne 4 emploie le symbole $P$ comme variable de parcours des entrées de $CT$, alors que $\mathcal{P}$ désigne par ailleurs l'ensemble complet des motifs retenus, et l'ensemble $CT$ lui-même n'est introduit nulle part dans l'algorithme : il faut lire la boucle comme un parcours des entrées de la table de codes courante, chacune produisant un candidat estimé, sans que l'algorithme précise ce que cette table contient au premier tour.

La ligne 10 trie les motifs d'un ensemble $G$ que l'algorithme n'introduit nulle part, pas plus que $CT$ : les seules variables qu'il définisse lui-même sont $\mathcal{P}$ et $A$ à la ligne 1, puis $\mathcal{F}$ à la ligne 3. Cet ensemble se lit comme l'ensemble des motifs retenus, et le tri comme un classement par importance qui ne modifie pas l'ensemble retourné.

La différence avec l'[[Algorithme de sélection de candidats de SQS]] est l'origine des candidats : celui-ci reçoit un ensemble $\mathcal{F}$ extrait au préalable et l'examine une fois pour toutes, alors que SQS-SEARCH reconstruit son vivier à chaque tour à partir de la table courante, ce qui lui permet de tenir compte des motifs ajoutés en cours de route et de s'arrêter quand le budget de calcul est épuisé.
