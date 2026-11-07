#ml-1

# Définition

L'**apprentissage semi-supervisé**, aussi appelé apprentissage **faiblement supervisé** (*weak supervised*), est le cadre d'apprentissage qui combine des **données étiquetées** et des **données non étiquetées**.

# Exemple

Un nuage de points mélange deux populations :

- quelques points étiquetés, repérés par un carré, un triangle ou un cercle ;
- de nombreux points non étiquetés, repérés par une croix.

L'apprentissage produit une fonction $f(x) = y$, où la sortie $y$ appartient à l'ensemble des étiquettes connues, $\{\text{carré}, \text{triangle}, \text{cercle}\}$.

# Remarque

Le recours aux données non étiquetées répond au coût de l'annotation : acquérir des données étiquetées coûte cher, en argent comme en temps.

La quantité de données reste déterminante pour la précision du modèle : davantage de données donnent un modèle plus précis (*« There is no data like more data »*).

L'apprentissage semi-supervisé donne les meilleurs résultats, mais il demande de la prudence : les données non étiquetées ne portent pas la réponse attendue.

Il se situe entre l'[[Apprentissage supervisé]], où toutes les données sont étiquetées, et l'[[Apprentissage non supervisé]], où aucune ne l'est.

Les [[Auto-encodeur|auto-encodeurs]] offrent un cadre d'apprentissage sur des données non étiquetées, exploitable en amont d'un modèle semi-supervisé.
