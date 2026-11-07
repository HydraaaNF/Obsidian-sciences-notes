#ml-1

# Définition

En classification multi-étiquette, un exemple peut recevoir plusieurs classes à la fois : les classes ne se concurrencent pas.

Le problème se traite comme $K$ problèmes binaires indépendants, un par classe, et le type de classification auquel il appartient est décrit dans [[Types de classification]].

# Modèle

- Sortie : $K$ probabilités, une par classe, sans softmax ; chaque sortie est sa propre régression logistique, obtenue par une sigmoïde.
- Cible : un $0$ ou un $1$ par classe, par exemple $y = (1, 1, 0)$ pour un chat photographié avec un chien.
- Perte : l'[[Entropie croisée binaire]] de chaque sortie, moyennée sur les $K$ sorties.
- Décision : un [[Seuil de décision]] par sortie ; chaque seuil peut être réglé sur le jeu de validation, comme en [[Régression logistique]].

# Exemple

Trois classes, chat, chien et oiseau : les probabilités de sortie valent $\mathbb{P}(\text{chat}) = 0.90$, $\mathbb{P}(\text{chien}) = 0.80$ et $\mathbb{P}(\text{oiseau}) = 0.05$.

Aucune contrainte de somme à $1$ ne s'applique : ces trois valeurs sont acceptables telles quelles.

Avec un seuil par sortie, la décision retient ici $\{\text{chat}, \text{chien}\}$ : l'oiseau, à $0.05$, reste sous son seuil.

# Remarque

- Rien de nouveau par rapport au cas binaire : une classification multi-étiquette est $K$ régressions logistiques qui partagent les mêmes couches cachées.
- Le softmax est absent précisément parce que les classes ne se concurrencent pas ; il n'a de sens que lorsque les probabilités doivent sommer à $1$.
