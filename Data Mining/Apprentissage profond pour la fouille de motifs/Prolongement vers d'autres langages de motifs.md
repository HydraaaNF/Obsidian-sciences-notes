#dmv-pattern_mining_vs_deep_learning

# Interprétation

L'[[Auto-encodeur de motifs|auto-encodeur de motifs]] établit qu'une descente de gradient peut produire un [[Ensemble de motifs|ensemble de motifs]] sur des transactions binaires. Le prolongement naturel consiste à changer de langage de motifs, c'est-à-dire à viser d'autres formes de régularités que les itemsets :

- les graphes, où la masse de travaux sur les réseaux de neurones de graphes pourrait être mise à contribution ;
- les séquences ;
- des variations plus simples des itemsets, comme les itemsets généralisés.

Ces trois directions sont posées comme des pistes ouvertes, aucune n'est un résultat acquis.

# Remarque

Changer de langage n'est pas une simple réécriture. Les graphes et les séquences décrivent des données plus structurées qu'un ensemble, et la fouille y demande de redéfinir ce qu'est un motif et comment on le repère : c'est l'objet de l'[[Extension de la fouille de motifs aux données structurées|extension de la fouille de motifs aux données structurées]], dont [[Fouille de motifs de graphes]] et [[Motif séquentiel]] traitent deux cas.

La priorité annoncée va aux variations simples des itemsets, avant les séquences et les graphes.
