#ml-1

# Définition

`model.state_dict()` renvoie un dictionnaire qui associe à chaque nom de paramètre le tenseur correspondant. C'est ce que l'on sauvegarde : ce qui a été **appris**, pas le code.

Recharger ces poids demande deux étapes : reconstruire le modèle avec la même architecture, puis y charger le dictionnaire.

# Exemple

Sauvegarde des poids d'un modèle déjà entraîné :

```python
torch.save(model.state_dict(), "model.pt")
```

Reconstruction du modèle avec la classe définie dans [[Composer un réseau avec PyTorch]], puis chargement :

```python
model = MLP(2, 8, 1)                  # untrained
model.load_state_dict(torch.load("model.pt"))
model.eval()                          # ready to predict
```

Le modèle est instancié non entraîné, puis ses poids sont remplacés par ceux du fichier ; `model.eval()` le place en mode évaluation, prêt à prédire.

# Remarque

Reprendre un entraînement interrompu ne se limite pas aux poids : l'optimiseur possède un état propre, qu'il faut sauvegarder aussi, avec le numéro d'époque.

```python
torch.save({"model": model.state_dict(),
            "optimizer": optimizer.state_dict(),
            "epoch": epoch}, "checkpoint.pt")
```

Le checkpoint rassemble les trois dans un même dictionnaire : le modèle, l'[[Optimiseurs|optimiseur]] et l'époque atteinte. L'époque enregistrée permet de repartir au bon endroit dans la boucle d'entraînement décrite dans [[Boucle d'entraînement et validation]].

Les poids seuls suffisent pour prédire, mais pas pour continuer l'entraînement : l'état de l'optimiseur est nécessaire en plus. Inversement, un dictionnaire de poids ne contient pas le code du modèle, d'où la reconstruction préalable avant le chargement.
