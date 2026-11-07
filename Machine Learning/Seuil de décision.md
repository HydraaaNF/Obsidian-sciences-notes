#ml-1

# Définition

Un classifieur probabiliste, comme la [[Régression logistique|régression logistique]], ne sort pas une classe mais une probabilité $\hat{y}$, estimée d'appartenance à la classe positive. La décision binaire s'obtient par binarisation à un seuil de décision $t$ :

- si $\hat{y} \le t$, prédire $0$ ;
- sinon, prédire $1$.

Le seuil usuel est $t = 0.5$.

# Interprétation

Le seuil n'appartient pas au modèle : le modèle fournit une probabilité, et le seuil transforme cette probabilité en étiquette.

- Le seuil $0.5$ est un choix, pas une loi.
- Abaisser le seuil donne plus de prédictions positives : le rappel augmente, la précision diminue.
- Relever le seuil produit l'effet inverse : moins de positifs prédits, davantage de précision et moins de rappel.

Voir [[Précision et rappel]] pour la lecture conjointe de ces deux mesures.

# Remarque

- Le seuil se règle sur le [[Jeux d'entraînement, de développement et de test|jeu de développement]], pour la métrique qui compte réellement dans l'application visée, et non sur le jeu de test.
- À modèle entraîné identique, des seuils différents définissent des points de fonctionnement différents : le seuil est un réglage d'exploitation, pas une étape d'apprentissage supplémentaire.
- La même logique de seuil s'étend à la [[Classification multi-étiquette]], où chaque étiquette peut recevoir son propre seuil.

# Exemple

Sur un tenseur de probabilités `x`, les opérations PyTorch usuelles de filtrage au seuil sont :

```python
x > 0.5
x[x > 0.5]
torch.where(cond, val_true, val_false)
```

La première produit un masque booléen, la deuxième ne conserve que les probabilités supérieures au seuil, la troisième choisit entre deux valeurs selon un masque.
