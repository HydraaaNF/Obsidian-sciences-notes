#ml-3

# Définition

Le parallélisme d'entraînement à l'échelle répartit un entraînement sur un ensemble de GPU organisés selon plusieurs axes, chaque axe découpant une dimension différente du calcul.

# Modèle

L'ensemble des GPU se lit comme un empilement tridimensionnel de blocs, chaque direction portant un parallélisme.

| Axe | Parallélisme | Organisation |
| --- | --- | --- |
| Vertical | ZeRO Data Parallel | rangée avant : GPU 0, GPU 8, GPU 16, GPU 24 ; rangée arrière : GPU 4, GPU 12, GPU 20, GPU 28 |
| Horizontal | Pipeline Parallel | étages successifs de blocs |
| Profondeur | Model Parallel | couches empilées vers l'arrière |

Chaque bloc de l'empilement est un [[Calcul sur GPU|GPU]]. Sur l'axe vertical, le parallélisme de données ZeRO regroupe les blocs par colonne : la rangée avant porte les GPU 0, 8, 16 et 24, la rangée arrière les GPU 4, 12, 20 et 28.

Sur l'axe horizontal, le parallélisme de pipeline découpe le modèle en étages successifs de blocs. En profondeur, le parallélisme de modèle empile les couches vers l'arrière.

Un même entraînement combine ces axes : chaque GPU se repère par sa position le long de chacun d'eux. Cette étape intervient dans le [[Cycle de vie d'un grand modèle de langage]], au moment de l'entraînement.

# Remarque

Deux autres axes complètent cette organisation sans apparaître sur l'empilement : le parallélisme de tenseurs et le parallélisme de séquences, cités aux côtés du parallélisme de données, du découpage de modèle et du parallélisme de pipeline.
