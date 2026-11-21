#ml-3

# Remarque

La tendance des grands modèles de langage tient en trois mouvements : des modèles plus grands, entraînés sur plus de données, obtiennent de meilleures performances. Les modèles de pointe atteignent environ 1000 milliards de paramètres, les modèles extrêmes américains et chinois occupant le haut de cette échelle. Ce constat prolonge les [[Loi d'échelle|lois d'échelle]] et la [[Loi de Chinchilla]], qui quantifient le compromis entre taille du modèle, volume de données et performance, et il se lit à chaque étape du [[Cycle de vie d'un grand modèle de langage]].

Un graphique compare les scores MMLU (5-shot) des modèles à poids fermés et des modèles à poids ouverts, du printemps 2022 à l'été 2024 :

- les modèles à poids fermés (PaLM, Chinchilla, GPT-4, Claude, Gemini) forment la courbe supérieure, partie d'environ 70 % pour atteindre le haut du graphique, autour de 88 % ;
- les modèles à poids ouverts (Flan-T5, LLaMA, Llama 2, Mistral, Llama 3.1) forment la courbe inférieure, partie un peu sous 50 % et progressant plus vite ;
- l'écart entre les deux courbes se réduit au fil du temps, jusqu'à pratiquement disparaître à l'été 2024, où les meilleurs modèles ouverts rejoignent les modèles fermés de tête.

Les libellés du graphique sont peu lisibles : seule la tendance d'ensemble est retenue ici, sans reproduction des points.

Une réserve accompagne ce constat : la capacité de construire un tel modèle n'est pas considérée comme acquise en France.

- La croissance de la taille des modèles pèse sur l'[[Empreinte environnementale de l'intelligence artificielle]], dont l'évolution suit celle des moyens de calcul engagés.
