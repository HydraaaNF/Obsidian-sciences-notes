#dmv-sequence_mining

# Interprétation

MINEPI est une approche alternative de la [[Fouille d'épisodes dans une séquence d'événements|fouille d'épisodes]] qui se passe de [[Fenêtre glissante de WINEPI|fenêtre glissante]].

Au lieu de découper la [[Séquence d'événements|séquence d'événements]] en instantanés, la méthode part des épisodes : pour chaque [[Épisode|épisode]] potentiellement intéressant, elle recherche ses occurrences exactes.

Cette recherche s'appuie sur la notion d'[[Occurrence minimale d'un épisode|occurrence minimale]] : le décompte ne porte plus sur des fenêtres, mais sur les occurrences minimales trouvées pour chaque épisode candidat, ce qui distingue la méthode de l'[[Algorithme WINEPI]].

# Algorithme

La fouille porte sur les épisodes série, sous une borne temporelle maximale de 40 s et une fréquence minimale $\mathit{min\_fr} = 1$.

1. Créer les singletons, c'est-à-dire les épisodes de taille 1 : A, B, C, D.
2. Construire une table d'occurrences, sous forme de tables inversées : A : 30, 60 ; B : 40, 70 ; C : 20, 80 ; D : 10, 50.
3. Reconnaître les singletons fréquents ; ici tous le sont.
4. À partir des épisodes fréquents de taille 1, engendrer les candidats de taille 2 : AB, BA, AC, CA, AD, DA, BC, CB, BD, DB, CD, DC.
5. Créer les occurrences minimales des candidats à l'aide de la table inversée.
6. Reconnaître les épisodes fréquents de taille 2 ; ici presque tous le sont.
7. À partir des épisodes fréquents de taille 2, engendrer les candidats de taille 3, et ainsi de suite.

# Exemple

Occurrences minimales du candidat AB, lues dans la table inversée : on lit la première occurrence de A (30, 30), puis on cherche la première occurrence suivante de B (40, 40) ; on lit ensuite la deuxième occurrence de A (60, 60), puis la première occurrence suivante de B (70, 70).

$$Mo(AB) = \{[30, 40], [60, 70]\}$$

Le même mécanisme s'applique ensuite à BA, AC, etc.

# Remarque

MINEPI ne construit aucune base de séquences : la séquence d'événements est exploitée directement par les tables inversées, alors que l'approche par [[Fenêtre glissante de WINEPI|fenêtres glissantes]] transforme la séquence en une collection d'instantanés avant tout comptage.

La borne temporelle maximale fixe l'étendue au-delà de laquelle deux événements ne peuvent plus appartenir à une même occurrence.

Le comptage porte sur les occurrences minimales, et c'est leur nombre qui fournit la [[Fréquence d'un épisode|fréquence de l'épisode]].
