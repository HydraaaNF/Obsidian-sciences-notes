# Exemple

On cherche à traduire le mot anglais *in* vers le français. Les données rassemblées associent au mot *in* ses traductions observées, dont l'ensemble est

$$\{\text{dans}, \text{en}, \text{à}, \text{au cours de}, \text{pendant}\} .$$

Un modèle de traduction probabiliste simple attribue une probabilité à chacune de ces traductions, éventuellement conditionnellement au contexte dans lequel le mot apparaît. La distribution retenue est celle d'entropie maximale parmi celles qui respectent les faits connus, conformément au [[Principe du maximum d'entropie]].

## Cas 1 : aucune information

Aucune information n'est disponible en dehors de la liste des traductions possibles, et la seule contrainte est que les probabilités somment à un :

$$p(\text{dans}) + p(\text{en}) + p(\text{à}) + p(\text{au cours de}) + p(\text{pendant}) = 1 .$$

Le meilleur modèle, celui d'[[Entropie d'une variable aléatoire discrète|entropie]] maximale, est la [[Loi uniforme discrète|distribution uniforme]] sur les cinq traductions :

$$p(\text{dans}) = p(\text{en}) = p(\text{à}) = p(\text{au cours de}) = p(\text{pendant}) = \frac{1}{5} .$$

## Cas 2 : une contrainte empirique

L'observation empirique des données fournit un fait supplémentaire :

$$p(\text{dans}) + p(\text{en}) = \frac{3}{10} .$$

Le meilleur modèle tenant compte de ce fait, en plus de la contrainte de somme à un, est une distribution uniforme par morceaux :

$$p(\text{dans}) = p(\text{en}) = \frac{3}{20} ,$$

$$p(\text{à}) = p(\text{au cours de}) = p(\text{pendant}) = \frac{7}{30} .$$

Les deux traductions privilégiées par le fait observé se partagent la masse $3/10$, soit $\frac{3}{20}$ chacune ; les trois autres se partagent le reste, soit $7/10$, donc $\frac{1 - 3/10}{3} = \frac{7}{30}$ chacune.

# Remarque

Une distribution par morceaux est bien celle d'entropie maximale sous une contrainte portant sur la masse totale d'un groupe de traductions :

- à l'intérieur de chaque groupe, les probabilités sont égales, car toute inégalité entre deux traductions du même groupe pourrait être égalisée en augmentant l'entropie sans changer la masse du groupe ;
- entre les groupes, les masses sont entièrement déterminées par les faits observés.

Pour les trois traductions hors du groupe observé, la valeur $7/20$ est une erreur fréquente : elle ne respecte pas la contrainte de somme à un, puisque $2 \times \frac{3}{20} + 3 \times \frac{7}{20} = \frac{27}{20} \neq 1$. Chacune reçoit le tiers de la masse restante, soit $\frac{1 - 3/10}{3} = \frac{7}{30}$.

Le principe s'étend à des faits contextuels, par exemple une fréquence empirique de *en* conditionnellement au mot qui suit *in*. La formulation générale de ces contraintes, exprimées comme des espérances de fonctions de traits, est décrite dans [[Contraintes d'espérance sur les fonctions de traits]] ; l'écriture concrète des fonctions de traits sur cet exemple est donnée dans [[Fonctions de traits d'un exemple de traduction]].
