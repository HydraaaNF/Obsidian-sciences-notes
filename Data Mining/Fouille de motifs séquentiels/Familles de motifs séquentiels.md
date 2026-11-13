#dmv-sequence_mining

# Exemple

Une même chaîne d'items illustre cinq familles de motifs :

```text
ABCBDADBBCBAAABBCBDBABDABA
```

- **Sous-chaînes** : le motif $B \to C \to B$ y apparaît de façon contiguë, aux positions 2 à 4, 9 à 11 et 16 à 18.
- **Séquences avec trous** : le motif $B \to C \to B \to A$ y apparaît en laissant des items quelconques s'intercaler entre ses items.
- **Expressions régulières** : le motif $B \to \neg C \to A \mid B$ impose qu'après un $B$ vienne un item différent de $C$, puis un $A$ ou un $B$.
- **Séquences d'itemsets** : le motif $\{B\} \to \{C\} \to \{A,D\}$ se lit sur une séquence dont chaque position est un ensemble d'items simultanés.
- **Épisodes** : les motifs $A \to B$ et $D \to C$ sont deux contraintes d'ordre posées simultanément sur les événements.

La séquence d'itemsets qui porte la quatrième famille est :

$$\{A,B\} \to \{C,B\} \to \{A,B,D\} \to \{A\} \to \{B,D\} \to \{D\} \to \{B,D\} \to \{C,D\} \to \{A,C,D\} \to \{A\}$$

Le motif $\{B\} \to \{C\} \to \{A,D\}$ y est inclus : $\{B\}$ est contenu dans $\{A,B\}$, $\{C\}$ dans $\{C,B\}$ et $\{A,D\}$ dans $\{A,B,D\}$.

# Interprétation

Les familles se distinguent par ce qu'elles autorisent entre deux items consécutifs du motif :

- la sous-chaîne exige la contiguïté stricte ;
- la séquence avec trous tolère des items intercalés, ce qui correspond à une [[Contrainte d'écart temporel|contrainte d'écart]] relâchée ;
- l'expression régulière remplace un item du motif par un ensemble d'items acceptables ;
- la séquence d'itemsets regroupe des items simultanés en une seule position ;
- l'[[Épisode|épisode]] remplace l'ordre total de la séquence par un ordre partiel.

Un même jeu de données admet donc plusieurs lectures, et le choix de la famille fixe la forme du motif recherché.

# Remarque

Le [[Motif séquentiel|motif séquentiel]] au sens d'une suite d'itemsets correspond à la quatrième famille ; les autres familles en sont des variantes plus contraintes ou plus générales.
