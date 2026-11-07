#ml-1

# Définition

Une **donnée** est un ensemble de valeurs, appelées **attributs** (en anglais *features*).

On distingue les données brutes de leurs attributs :

- les **données brutes** sont la donnée telle qu'elle est enregistrée, par exemple une matrice de pixels ;
- les **attributs** sont les valeurs qui décrivent la donnée, par exemple taille, poids, âge et genre pour une personne.

Les valeurs d'un attribut sont de deux types :

- **numériques** : taille, niveau de gris, poids, âge, rouge, vert, bleu ;
- **symboliques** : genre, mot.

Chaque attribut prend ses valeurs dans un domaine :

- taille : $\mathbb{R}^+$ ;
- niveau de gris : $[0, 1]$ ;
- vert : $\{0, \dots, 255\}$ ;
- genre : $\{M, F, NB\}$, ensemble fini ;
- mot : $\{a, \text{apricot}, \dots, \text{zebra}\}$.

Dans un problème d'apprentissage, les attributs se répartissent entre entrée et sortie :

- l'**entrée** est ce que l'on connaît de la donnée ;
- la **sortie** est ce que l'on cherche à prédire.

# Exemple

- Un oiseau : $(\text{taille}, \text{niveau de gris})$ ;
- une personne : $(\text{taille}, \text{poids}, \text{âge}, \text{genre})$ ;
- un pixel : $(\text{rouge}, \text{vert}, \text{bleu})$ ;
- une image en noir et blanc : matrice de niveaux de gris ;
- une image en couleur : matrice de triplets $(\text{rouge}, \text{vert}, \text{bleu})$ ;
- un texte : liste, vecteur ou séquence de mots.

# Remarque

Les attributs d'une donnée sont les [[Population statistique et caractère|caractères]] d'un individu au sens statistique : le genre et le mot sont des [[Caractère qualitatif|caractères qualitatifs]], la taille et le niveau de gris des [[Caractère quantitatif continu|caractères quantitatifs continus]].

Une image en couleur est une matrice et un texte un vecteur : ces données se représentent par des [[Tenseur|tenseurs]].
