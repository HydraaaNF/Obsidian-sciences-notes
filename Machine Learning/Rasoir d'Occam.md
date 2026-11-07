#ml-1

# Définition

Le rasoir d'Occam est le principe de parcimonie appliqué au choix d'une explication : parmi les explications possibles d'un même phénomène, on retient celle qui s'appuie sur le plus petit ensemble d'éléments.

Il en découle deux règles de conduite :

- ne pas introduire d'éléments inutiles ;
- garder l'explication aussi simple que possible.

# Exemple

Face à la suite $1, 2, 3, 5, a$, plusieurs règles rendent compte des quatre premiers termes :

- $a = 6$, avec la règle « tous les entiers sauf 4 » ;
- $a = 7$, avec la règle « les nombres premiers » ;
- $a = 8$, avec la règle de Fibonacci.

Les observations sont les mêmes, seule la règle change ; le rasoir d'Occam tranche en faveur de l'explication la plus économe en éléments. Le choix d'une telle règle est l'objet même de l'[[Apprentissage par l'expérience|apprentissage à partir d'exemples]].

# Remarque

Le principe est énoncé sans formalisation : il ne fournit aucune mesure de la complexité d'une explication, et le degré de simplicité à retenir reste à décider au cas par cas.

En apprentissage, il sert de garde-fou contre les modèles inutilement riches, dont le [[Surapprentissage et sous-apprentissage|surapprentissage]] est le symptôme, et il éclaire le partage entre [[Erreur d'approximation et erreur d'estimation|erreur d'approximation et erreur d'estimation]].
