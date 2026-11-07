#ml-1

# Définition

Pour une classe $C$, la [[Matrice de confusion et exactitude|matrice de confusion]] restreinte à cette classe range chaque prédiction dans l'une de quatre cases :

| | prédit $C$ | prédit $\neg C$ |
| --- | --- | --- |
| réel $C$ | TP | FN |
| réel $\neg C$ | FP | TN |

- un vrai positif (TP) est un échantillon de classe $C$ prédit $C$ ;
- un faux positif (FP) est un échantillon étiqueté à tort $C$ ;
- un faux négatif (FN) est un échantillon de classe $C$ étiqueté à tort $\neg C$ ;
- un vrai négatif (TN) est un échantillon hors de $C$ prédit $\neg C$.

La précision de la classe $C$ est la proportion de prédictions $C$ qui sont correctes :

$$\text{Prec}(C) = \frac{TP}{TP + FP}$$

Le rappel de la classe $C$ est la proportion des échantillons de classe $C$ qui sont détectés :

$$\text{Rec}(C) = \frac{TP}{TP + FN}$$

# Interprétation

- La précision répond à la question : de ce que j'ai signalé, combien était juste ?
- Le rappel répond à la question : de ce qui existait, combien ai-je trouvé ?

# Remarque

- Prise seule, chacune des deux mesures est facile à tromper : annoncer $C$ pour tout échantillon donne un rappel de $1$, et n'annoncer $C$ que pour les cas les plus sûrs peut donner une précision très élevée. Les deux mesures se lisent donc ensemble, voir [[F-mesure F1]].
- La précision et le rappel sont définis par classe ; leur agrégation sur plusieurs classes est traitée dans [[Moyennes macro et micro]].
- Le compromis entre précision et rappel se règle par le [[Seuil de décision|seuil de décision]].
