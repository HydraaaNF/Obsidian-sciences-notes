#ml-1

# Définition

Un jeu de données se conserve dans un format qui range chaque [[Donnée et attributs|échantillon et chaque attribut]] à une place déterminée. Deux formats usuels :

- **CSV** (*Comma Separated Values*) : un échantillon par ligne, un attribut par colonne, la première ligne contenant éventuellement le nom des attributs ;
- **JSON** (*JavaScript Object Notation*) : un échantillon par dictionnaire, un dictionnaire étant un ensemble de couples clé-valeur, une valeur étant un littéral, une liste ou un dictionnaire.

Un jeu de données au format JSON est donc une liste d'échantillons, c'est-à-dire une liste de dictionnaires. Le format **XML** appartient à la même famille que JSON.

# Exemple

Un jeu de données CSV, dont la première ligne donne le nom des attributs :

```text
size,weight,age,gender
180,65,20,M
160,45,35,F
200,100,45,M
165,65,60,M
175,50,50,F
170,60,25,F
```

Le même premier échantillon au format JSON :

```json
[
  {
    "size": 180,
    "weight": 65,
    "age": 20,
    "gender": "M"
  },
  ...
]
```

# Remarque

Le CSV est efficace, mais malcommode à manipuler : il ne porte ni types, ni imbrication, ni standard.

Le JSON est verbeux, mais facile à traiter dans du code, grâce aux dictionnaires qu'il expose directement.

La structure des valeurs conditionne le format retenu : un texte, un arbre ou un graphe se prêtent mal à une ligne de CSV, voir [[Données structurées et non structurées]].

# Interprétation

Dès que le jeu de données ne tient plus en mémoire, le stockage devient un problème en soi, avec trois préoccupations :

- **l'efficacité du stockage** : formats binaires et compressés, comme HDF5 (`.h5`), Pickle (`.pkl`, `.p`) et PyTorch (`.pt`), ce dernier conservant les [[Tenseurs PyTorch|tenseurs]] PyTorch ;
- **la distribution des données** : répartition sur plusieurs machines, avec Hadoop et HDFS ;
- **l'accessibilité** : consultation par des bases de données ou par Hadoop.

Ces préoccupations relèvent du traitement du **big data**.
