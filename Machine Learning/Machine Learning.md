# Sommaire

## Fondements de l'apprentissage
- [[Apprentissage automatique et disciplines voisines]]
- [[Apprentissage par l'expérience]]
- [[Rasoir d'Occam]]
- [[Modèle d'apprentissage]]
- [[Régression, classification et clustering]]
- [[Erreur d'approximation et erreur d'estimation]]
- [[Surapprentissage et sous-apprentissage]]
- [[Apprentissage supervisé]]
- [[Apprentissage non supervisé]]
- [[Apprentissage semi-supervisé]]

## Données et tenseurs
- [[Donnée et attributs]]
- [[Données structurées et non structurées]]
- [[Encodage des valeurs symboliques]]
- [[Stockage des données]]
- [[Tenseur]]
- [[Tableaux NumPy et pandas]]
- [[Tracé de graphiques avec Matplotlib]]
- [[Tenseurs PyTorch]]
- [[Opérations sur les tenseurs]]
- [[Forme d'un tenseur]]
- [[Diffusion entre tenseurs]]
- [[Indexation et réductions]]

## Évaluer un modèle
- [[Évaluation d'un modèle d'apprentissage]]
- [[Métrique et fonction de perte]]
- [[Mesures d'erreur en régression]]
- [[Coefficient de détermination]]
- [[Matrice de confusion et exactitude]]
- [[Précision et rappel]]
- [[F-mesure F1]]
- [[Moyennes macro et micro]]
- [[Évaluation d'un clustering]]
- [[Jeux d'entraînement, de développement et de test]]
- [[Évaluer un classifieur avec scikit-learn]]

## Optimisation et entraînement

### Régression linéaire et descente de gradient
- [[Régression linéaire]]
- [[Perte absolue et perte quadratique]]
- [[Forme matricielle de la régression]]
- [[Descente de gradient]]
- [[Entraîner un modèle linéaire pas à pas]]

### Graphe de calcul et rétropropagation
- [[Graphe de calcul]]
- [[Rétropropagation]]
- [[Différenciation automatique]]
- [[Optimiseurs]]

### Entraîner avec PyTorch
- [[Composer un réseau avec PyTorch]]
- [[Boucle d'entraînement et validation]]
- [[Lots, époques et chargement des données]]
- [[Sauvegarde et reprise de l'entraînement]]
- [[Normalisation des entrées]]
- [[Normalisation par lots]]
- [[Connexions résiduelles]]
- [[Planificateurs de taux d'apprentissage]]
- [[Calcul sur GPU]]

## Du neurone aux réseaux multicouches

### Classification binaire et régression logistique
- [[Classification binaire]]
- [[Régression logistique]]
- [[Entropie croisée binaire]]
- [[Apprentissage de la régression logistique]]
- [[Seuil de décision]]
- [[Neurone artificiel]]

### Réseaux de neurones
- [[Problème du ou exclusif]]
- [[Composition de couches linéaires]]
- [[Fonctions d'activation]]
- [[Réseau de neurones]]
- [[Perceptron multicouche]]
- [[Hyper-paramètres]]
- [[Première et dernière couches]]

### Classification à plusieurs classes
- [[Types de classification]]
- [[Fonction softmax]]
- [[Température d'un softmax]]
- [[Entropie croisée multi-classe]]
- [[Gradient du couple softmax et entropie croisée]]
- [[Classification multi-étiquette]]
- [[Entropie croisée multi-classe avec PyTorch]]
- [[Un vecteur par classe]]

## Convolution et réseaux convolutifs

### Convolution en une et deux dimensions
- [[Intérêt de la convolution]]
- [[Couche de convolution]]
- [[Convolution en une dimension]]
- [[Taille de sortie d'une convolution]]
- [[Convolution en deux dimensions]]

### Paramètres et variantes de la convolution
- [[Padding, stride et dilation]]
- [[Convolution dilatée]]
- [[Convolution causale]]
- [[Conservation de la longueur dans une convolution causale]]

### Assembler un réseau convolutif
- [[Max pooling]]
- [[Réseau de neurones convolutif]]
- [[Dropout]]
- [[Réseau convolutif avec PyTorch]]

## Représentations et plongements
- [[Plongement]]
- [[Auto-encodeur]]
- [[Encodeur-décodeur]]
- [[Apprentissage multi-tâches]]
- [[Hypothèse distributionnelle]]
- [[word2vec]]
- [[Analogies dans l'espace des plongements]]
- [[Couche de plongement]]
- [[Réseaux siamois]]

## Séquences et récurrence

### Séquences et modèle récurrent
- [[Données séquentielles]]
- [[Tâches sur les séquences]]
- [[Longueur variable des séquences]]
- [[Réseau récurrent]]
- [[Cellule d'Elman]]

### Entraîner et stabiliser la récurrence
- [[Rétropropagation dans le temps]]
- [[Disparition et explosion du gradient]]
- [[Mémoire à long et court terme]]
- [[Unité récurrente à portes]]
- [[Couches récurrentes avec PyTorch]]

### Encoder, décoder et générer
- [[Encodage d'une séquence]]
- [[Encodeur bidirectionnel et causalité]]
- [[Génération d'une séquence]]
- [[Teacher forcing]]
- [[Encodeur-décodeur pour les séquences]]

## Modèles génératifs

### Fondements des modèles génératifs
- [[Modèle génératif]]
- [[Décodeur génératif]]
- [[Décomposition autorégressive d'une densité]]
- [[Panorama des modèles génératifs]]

### Audio et représentation du son
- [[Audio numérique]]
- [[Compression mu-law]]
- [[Spectrogramme mel]]
- [[Tacotron 2]]

### WaveNet
- [[Architecture WaveNet]]
- [[Unité résiduelle de WaveNet]]
- [[Dilatation des convolutions de WaveNet]]
- [[Champ récepteur d'une pile de convolutions]]
- [[Entraînement de WaveNet]]
- [[Inférence autorégressive]]
- [[Conditionnement de WaveNet]]

### Auto-encodeur variationnel et représentations
- [[Auto-encodeur variationnel]]
- [[Astuce de reparamétrisation]]
- [[Désenchevêtrement des représentations]]

### Réseaux antagonistes génératifs
- [[Réseau antagoniste génératif]]
- [[Entraînement d'un réseau antagoniste génératif]]
- [[Variantes de réseaux antagonistes génératifs]]

### Diffusion et bilan
- [[Modèle de diffusion]]
- [[Diffusion latente]]
- [[Modèle neuronal, architecture et fonction de coût]]
