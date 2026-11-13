#dmv-sequence_mining

# Définition

La **durée des séquences** est la taille du découpage appliqué aux séquences cibles : la suite d'événements est découpée en tranches temporelles, et chaque tranche forme une [[Base de séquences|séquence]] soumise à la fouille.

Ce choix relève du prétraitement : il se fixe avant l'extraction des motifs, en même temps que les autres réglages de la base.

# Exemple

- **Séquences complètes** : chaque séquence est conservée dans son entier, sans découpage.
- **Intervalle de temps spécifié** : chaque séquence couvre une plage de dates choisie.
- **Découpage par années, par mois, etc.** : chaque période fournit une séquence distincte.

# Remarque

Le découpage périodique donne accès aux motifs séquentiels périodiques, ceux qui se répètent d'une période à l'autre : « chaque année, un printemps humide entraîne plus de réservations de voyages à l'étranger en été ». La comparaison des périodes fait apparaître la régularité, qu'une séquence unique et continue masquerait.

La durée des séquences se règle avant l'extraction, contrairement à la [[Contrainte d'écart temporel]], qui s'applique pendant la fouille, et elle se combine avec la [[Fenêtre de repliement des événements]], qui fixe l'atomicité des transactions à l'intérieur de chaque tranche. L'ensemble de ces réglages constitue les [[Contraintes temporelles en fouille de motifs séquentiels]].
