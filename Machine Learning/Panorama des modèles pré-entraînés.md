#ml-3

# Interprétation

Le traitement automatique du langage naturel s'appuie sur quelques modèles pré-entraînés devenus des références, tous déclinés du [[Variantes du Transformer|Transformer]]. Trois familles se distinguent par la pile de blocs qu'elles conservent :

- encodeur-décodeur : l'architecture d'origine, dont BART et T5 sont les représentants pré-entraînés
- encodeur : la famille de BERT
- décodeur : la famille de GPT

| Famille | Pile de blocs conservée | Modèles pré-entraînés cités |
|---|---|---|
| encodeur-décodeur | encodage complet puis décodage | architecture d'origine, BART, T5 |
| encodeur | encodage seul | BERT et ses variantes |
| décodeur | décodage seul | GPT et ses variantes |

Les modèles pré-entraînés les plus connus sont BERT, GPT, BART et T5, soit au moins un représentant par famille. La bibliothèque Python `transformers` de Hugging Face rassemble ces modèles pré-entraînés, voir [[Pipeline Hugging Face]].

# Remarque

Les noms se répartissent par famille, et chaque famille possède sa note :

- [[BERT et le modèle de langage masqué|BERT]] pour l'encodeur seul
- [[Transformer décodeur seul|GPT]] pour le décodeur seul
- [[T5 et l'apprentissage multi-tâche|T5]] et [[Résumé automatique avec BART|BART]] pour l'encodeur-décodeur, dont [[Architecture du Transformer|l'architecture d'origine]] est le premier exemplaire

La famille décodeur, causale, produit le texte jeton après jeton, selon la [[Génération d'une séquence|génération autorégressive]]. Les autres familles de modèles génératifs sont comparées dans le [[Panorama des modèles génératifs]].
