#ml-3

# Définition

Un **pipeline Hugging Face** est la chaîne complète qui applique un modèle pré-entraîné à une entrée textuelle. Il réalise une fonction $f$ du texte vers du texte, pour une génération, ou du texte vers une classe, pour une classification.

Le pipeline réunit trois étapes : l'encodage du texte, le chargement du modèle, puis le passage des identifiants au modèle.

# Algorithme

1. Encoder le texte avec la classe `Tokenizer` : découper en mots ou en morceaux de mots, convertir chaque unité en identifiant, puis appliquer le *padding* pour égaliser les longueurs d'un lot.
2. Charger le modèle avec la classe `AutoModelForXXX`, où `XXX` désigne la tâche à accomplir, par exemple `AutoModelForCausalLM` pour une génération de texte. La méthode `from_pretrained()` fournit les poids du modèle.
3. Passer les identifiants au modèle et lire sa sortie : une suite d'identifiants à décoder en texte, ou une classe.

# Remarque

Les entrées du modèle sont ses sorties décalées d'un token. En pratique, on ne construit pas ce décalage soi-même : on passe `labels = input_ids`, et le décalage est fait à l'intérieur du modèle. C'est la même convention que le [[Teacher forcing]], où la cible à chaque position est l'élément suivant de la séquence.
