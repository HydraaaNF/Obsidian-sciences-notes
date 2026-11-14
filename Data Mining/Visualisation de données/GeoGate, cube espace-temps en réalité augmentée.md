#dmv-visualization

# Modèle

GeoGate est un cube espace-temps en réalité augmentée à interactions tangibles, destiné à mettre en relation des jeux de données géographiques et temporels. Ses composants et annotations sont les suivants :

- Time Scale : l'échelle de temps du cube
- Light Data : les données légères, les points projetés
- STC Template : le gabarit du cube espace-temps
- Trajectory : la trajectoire d'une entité
- Time Slider : le curseur temporel
- Information Board : le panneau d'information
- Selection : la sélection d'un élément
- Inner Map : la carte intérieure

# Interprétation

Le dispositif transpose le principe du [[Cube espace-temps pour l'exploration de trajectoires|cube espace-temps]] dans un contexte de réalité augmentée : le cube est vu en superposition du monde réel, la position horizontale portant la localisation et la hauteur portant le temps, si bien qu'une trajectoire se lit comme une courbe qui monte.

Les interactions sont tangibles : le dispositif repose sur une table couverte d'une carte projetée, au-dessus de laquelle le cube apparaît ; l'utilisateur manipule à la main un anneau physique posé sur cette carte, muni de boutons et de graduations, dont les mouvements pilotent le cube et la sélection. La carte intérieure rapporte les éléments sélectionnés dans le cube à leur position géographique, et le panneau d'information en donne le détail. Le curseur temporel fait avancer ou reculer l'instant courant, ce qui anime la trajectoire et les points de données.

# Remarque

GeoGate relève de l'[[Analytique immersive]] : l'immersion y sert à corréler deux jeux de données de natures différentes, l'un géographique, l'autre temporel, plutôt qu'à augmenter le réalisme de la scène. Il s'appuie sur des composants de construction décrits dans les [[Outils de construction pour l'analytique immersive|outils de construction pour l'analytique immersive]].
