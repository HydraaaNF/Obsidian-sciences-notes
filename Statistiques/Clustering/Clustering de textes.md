# Définition

Le **clustering de textes** applique le [[Clustering|clustering]] à des documents textuels : il regroupe automatiquement ces documents en thèmes apparentés. C'est l'une des [[Applications du clustering|applications du clustering]].

# Exemple

Une recherche sur **rolling stones** regroupe ses résultats sous un thème racine (« All Topics ») et une série de thèmes :

```mermaid
flowchart TD
    A["All Topics"] --> B["Rolling Stones News"]
    A --> C["Rolling Stones Biography"]
    A --> D["Rolling Stones Lyrics"]
    A --> E["Rolling Stones are an English"]
    A --> F["Mick Jagger"]
    A --> G["Rolling Stone Magazine"]
    A --> H["Rolling Stones Began"]
    A --> I["Rolling Stones Tickets"]
    A --> J["Links"]
    A --> K["MP3 Downloads"]
```

Chaque thème est accompagné du nombre de documents qui lui est associé. Sélectionner un thème (ici « Rolling Stones Biography ») affiche dans un volet les documents qu'il contient, chacun présenté avec son titre, un extrait et son adresse ; un lien « show all » déroule la suite des thèmes.
