# Définition
Plusieurs axes classent les méthodes de clustering :

- **exclusif ou non** : un point peut-il appartenir à plusieurs clusters (avec ou sans poids) ?
- **flou ou non** : dans un algorithme flou, un point appartient à tous les clusters avec un poids $\in [0,1]$
- **partiel ou non** : seule une partie des données est regroupée
- **homogène ou non** : les clusters ont-ils des formes très différentes ?

# Remarque
D'autres exigences pratiques interviennent dans le choix d'une méthode : passage à l'échelle (*scalability*), comportement dynamique (données qui évoluent), robustesse au bruit et aux valeurs aberrantes, insensibilité à l'ordre des données en entrée.
