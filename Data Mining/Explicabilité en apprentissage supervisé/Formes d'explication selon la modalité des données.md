#dmv-xai

# Interprétation

Une [[Explication]] est un énoncé qui caractérise les relations entre les entrées et les sorties d'un modèle. Sa forme concrète dépend de la modalité des données : ce qui se montre sur un texte ne se montre pas de la même façon sur une image ou sur un graphe de connaissances.

- sur un texte, l'explication surligne les mots qui pèsent sur la décision et accompagne la prédiction de ses probabilités par classe ;
- sur une image, elle prend la forme d'une carte de saillance superposée à la photographie, et la réponse se lit avec la région regardée ;
- sur un graphe de connaissances, elle prend la forme d'un masque pondérant les arêtes empruntées pour répondre à une requête.

Le même modèle peut donc recevoir plusieurs formes d'explication, chacune ajustée à ce que l'utilisateur peut lire sur son support : un surlignage se parcourt mot à mot, une carte de saillance se lit en zones, un masque d'arêtes se lit comme un sous-graphe. Ces formes sont des [[Représentation interprétable|représentations interprétables]] de la décision, et non le modèle lui-même.

# Exemple

## Texte

Un classifieur de messages attribue à un message du groupe de discussion portant sur science et créationnisme les probabilités suivantes.

```chart
type: bar
labels: ["atheism", "christian"]
series:
  - title: Probabilité prédite
    data: [0.53, 0.47]
```

La classe atheism l'emporte avec $0{,}53$ contre $0{,}47$ pour christian. L'explication textuelle jointe à cette prédiction surligne les mots du message qui ont conduit au choix : le nom de l'auteur, puis les termes « theories » et « science ».

> From: `salem@pangea.Stanford.EDU` (Bruce **Salem**)
> Subject: Re: Science and **theories**
> Organization: Stanford Univ. Earth Sciences
> Lines: 42
> NNTP-Posting-Host: `pangea.stanford.edu`
>
> In article `lC5u7Bq.J43@news.cso.uiuc.edu`, `cobb@alexia.lis.uiuc.edu` (Mike Cobb) writes:
> As per various threads on **science** and creationism, I've started dabbling into a book called Christianity and the Nature of Science by JP Moreland.
>
> As I don't know this book, I will use your heresay.

L'explication se lit donc sur deux plans : la distribution des probabilités situe la confiance du modèle entre deux classes voisines, le surlignage désigne les appuis textuels de la classe retenue.

## Image

La même démarche s'applique à une image, sous la forme d'une question posée sur la photographie. Une carte de saillance, superposée à l'image, met en évidence la zone sur laquelle le modèle s'appuie pour répondre ; la réponse est ensuite donnée en clair.

| Question | Réponse |
|---|---|
| What is the man doing? | Surfing |
| What is she holding? | Baseball bat |
| What is that? | Elephant |
| What is that? | Zebra |

Sur la première image, la saillance se concentre sur la vague et le surfeur ; sur la deuxième, sur la personne et la batte de baseball qu'elle tient ; sur la troisième, sur l'avant du corps de l'éléphant photographié ; sur la quatrième, sur un zèbre d'arrière-plan situé à gauche, et non sur l'animal photographié au premier plan.

## Graphe de connaissances

Une requête porte sur une entité et une relation dont le second argument est inconnu, et la réponse est l'entité qui complète le triplet.

- requête : `(Kelly, Nationality, ?)` ;
- réponse : Scotland.

Le modèle dispose d'un graphe dont les entités comprennent notamment `PrimeTime_Emmy_Award`, `Gosford_Park`, `James_Wilby`, `Independent_Spirit_Award`, `University_of_Strathclyde`, `Boardwalk_Empire`, `BAFTA_Award`, `Glasgow`, `Scottish`, `United_Kingdom`, `Scotland` et `Greenwich_Time`, et dont les relations comprennent `nominated_for`, `award`, `award_winner`, `actor`, `live_in`, `place_founded`, `country`, `contains`, `time_zones`, `first_level_division_of`, `place_of_birth` et `people`.

L'explication est un masque d'arêtes : chaque arête du voisinage de la requête reçoit un poids, porté par une échelle de couleurs allant de $1{,}00$ à $0{,}00$. Un poids proche de $1$ marque une arête fortement mobilisée par la réponse, un poids proche de $0$ une arête écartée. Le masque dessine ainsi le sous-graphe qui relie l'entité de départ à l'entité répondue, au lieu de laisser l'utilisateur parcourir tout le voisinage.

# Remarque

La forme de l'explication n'est pas seulement une commodité d'affichage : elle fixe ce que l'utilisateur peut vérifier. Un surlignage se contrôle en relisant les mots désignés, une carte de saillance en regardant la zone désignée, un masque d'arêtes en suivant le chemin retenu dans le graphe.

Ces formes sont celles que construisent les méthodes d'[[Explication locale]] : une méthode comme [[LIME]] fabrique une [[Représentation interprétable|représentation interprétable]] propre à la modalité traitée, mots surlignés pour le texte, zones pour l'image, avant d'ajuster un modèle simple sur cette représentation. La [[Taxonomie des techniques d'explicabilité]] situe ces méthodes parmi les explications produites après coup, par opposition aux modèles interprétables par construction.
