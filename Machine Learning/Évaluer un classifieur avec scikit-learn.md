#ml-1

# Définition

scikit-learn calcule directement les métriques d'un classifieur, dans `sklearn.metrics`.

- `confusion_matrix` : renvoie la [[Matrice de confusion et exactitude|matrice de confusion]], dont les lignes sont la vérité et les colonnes la prédiction, les classes étant rangées par ordre croissant (la classe 0 en premier) ; en binaire, elle se lit `[[TN, FP], [FN, TP]]`.
- `precision_score`, `recall_score` et `f1_score` : reçoivent la vérité en premier argument, la prédiction en second.
- `classification_report` : donne toutes ces mesures à la fois, pour chaque classe.

# Algorithme

```python
from sklearn.metrics import confusion_matrix
from sklearn.metrics import precision_score, recall_score
from sklearn.metrics import classification_report

cm = confusion_matrix(y_test, y_pred)
tn, fp, fn, tp = cm.ravel()          # binary case
precision_score(y_test, y_pred)     # truth first!
print(classification_report(y_test, y_pred))
```

# Interprétation

Pour un problème à $K$ classes, les mêmes mesures s'appliquent :

- la [[Matrice de confusion et exactitude|matrice de confusion]] est de taille $K \times K$, et l'exactitude reste la part d'échantillons bien classés ;
- la [[Précision et rappel|précision et le rappel]], ainsi que le [[F-mesure F1|F1]], se calculent par classe, en opposant cette classe à toutes les autres ;
- pour résumer le classifieur en un seul nombre, on prend la [[Moyennes macro et micro|moyenne macro ou micro]].

`classification_report` traite les $K$ classes, moyennes comprises.

# Remarque

En classification multi-étiquette, chaque classe est son propre problème binaire (voir [[Classification multi-étiquette]]) : on calcule la précision, le rappel et le F1 par classe, puis une moyenne macro ou micro.

L'exactitude y trompe dans les deux sens :

- exigée sur toutes les étiquettes à la fois, elle est trop sévère : une seule étiquette manquée sur dix et la photo est comptée fausse ;
- comptée étiquette par étiquette, elle est trop facile : la plupart des étiquettes sont absentes.
