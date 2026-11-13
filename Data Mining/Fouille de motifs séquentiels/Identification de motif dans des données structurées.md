#dmv-sequence_mining

# Remarque

Sur une [[Items, itemsets et base de transactions|base de transactions]], identifier un motif se ramène à une inclusion ensembliste : un itemset $X$ est un motif d'un itemset $Y$ lorsque $X \subseteq Y$. Pour les [[Itemset fréquent|itemsets fréquents]], c'est donc l'opération ensembliste simple $\subseteq$ qui décide : sur trois items $A$, $B$ et $C$, les inclusions se lisent directement sur un diagramme de Venn, où $A \cap B$, $A \cap C$, $B \cap C$ et $A \cap B \cap C$ sont les seules intersections non vides à considérer.

Sur des [[Extension de la fouille de motifs aux données structurées|données structurées]] (séquences, arbres, graphes), plusieurs définitions d'inclusion sont possibles, et le calcul de ces inclusions peut être coûteux.

# Exemple

La séquence $A \to D$ est-elle un motif de la séquence $A \to B \to C \to D$ ? La question s'écrit

$$A \to D \subseteq A \to B \to C \to D ?$$

La réponse dépend de la définition d'inclusion retenue :

- avec l'[[Inclusion de sous-séquence]], les éléments du motif peuvent être séparés par des éléments intercalaires, et $A \to D$ est contenu dans $A \to B \to C \to D$ ;
- avec la notion de [[Sous-séquence contiguë]], les éléments du motif doivent se suivre sans interruption, et $A \to D$ n'est pas contenu dans $A \to B \to C \to D$.

# Interprétation

L'identification du motif ne suffit pas à définir la fouille : une fois l'inclusion choisie, deux difficultés subsistent sur des données structurées.

Les occurrences trouvées peuvent se chevaucher, ce qui rend ambigu le [[Chevauchement des occurrences et comptage du support|comptage du support]].

L'[[Espace de recherche des motifs séquentiels|espace de recherche]] est bien plus vaste que celui des itemsets, où il est en $O(2^{\#\text{items}})$ : il croît de façon potentiellement exponentielle, les valeurs exactes dépendant du problème traité.

Le choix de la définition d'inclusion n'est donc pas neutre : il fixe à la fois ce qu'est un motif et le coût de son évaluation.
