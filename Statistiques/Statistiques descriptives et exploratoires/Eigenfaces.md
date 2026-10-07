# Définition
Application de l'[[Analyse en composantes principales|ACP]] à la reconnaissance faciale : chaque visage est représenté comme un vecteur de pixels, et l'ACP en extrait les composantes/visages principaux (*eigenfaces*).

# Interprétation
Permet de représenter chaque visage comme une combinaison linéaire des eigenfaces, ramenant le problème à l'espace des paramètres (taille $M$) plutôt qu'à l'espace image (taille $N^2$), bien plus grand.
# Remarque

Les composantes principales extraites sont appelées *eigenfaces* ; le nombre de composantes retenues fixe la dimension de l'espace de représentation.
