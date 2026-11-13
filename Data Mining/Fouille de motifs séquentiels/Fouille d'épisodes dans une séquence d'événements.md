#dmv-sequence_mining

# Définition

La fouille d'épisodes consiste à analyser des [[Séquence d'événements|séquences d'événements]] pour découvrir des [[Épisode|épisodes]] récurrents.

Elle prend place parmi les [[Familles de motifs séquentiels]] : la donnée traitée est ici une séquence d'événements unique, et non une base de séquences.

# Exemple

Trois domaines fournissent des séquences d'événements typiques, où les événements se succèdent le long d'un axe de temps.

Alarmes d'un réseau de télécommunication :

- des échecs de lien ;
- des échecs de connexion ;
- ces pannes alternent et se répètent au fil du temps.

Actions sur une interface utilisateur :

- lancer une lecture ;
- sauvegarder ;
- découper un extrait ;
- régler le son ;
- ces actions reviennent dans des ordres variés.

Occurrences de maladies récurrentes :

- des états de santé successifs ;
- un même état de maladie revenant plusieurs fois.

# Remarque

Deux traitements complémentaires du problème existent :

- l'approche par [[Fenêtre glissante de WINEPI|fenêtre glissante]], mise en œuvre par l'[[Algorithme WINEPI]] ;
- l'approche alternative sans fenêtre glissante, qui recherche pour chaque épisode potentiellement intéressant ses occurrences exactes, mise en œuvre par l'[[Algorithme MINEPI]] et fondée sur la notion d'[[Occurrence minimale d'un épisode|occurrence minimale]].
