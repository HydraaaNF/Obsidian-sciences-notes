#dmv-sequence_mining

# Interprétation

Un [[Motif séquentiel|motif séquentiel]] s'écrit en groupant entre parenthèses les items achetés ensemble, par exemple

$$\langle (A\ B)\ C\ (D\ E)\rangle$$

Il se lit : « des clients qui achètent A et B, puis achètent C, puis achètent D et E, en un mois ».

La même information se note plus lisiblement

$$A,B \rightarrow C \rightarrow D,E$$

où chaque flèche marque le passage d'un itemset au suivant, dans l'ordre chronologique.

# Remarque

La mention « en un mois » borne l'écart temporel entre les itemsets du motif : les achats doivent tenir dans un mois pour constituer une occurrence. C'est une [[Contrainte d'écart temporel]] ; sans borne, un client qui achèterait A et B, puis C, puis D et E sur plusieurs mois fournirait lui aussi une occurrence.

Cette borne ne se confond pas avec une [[Fenêtre de repliement des événements]] : celle-ci fixe, lors de la préparation des données, l'atomicité des transactions simultanées sur un intervalle (les ventes d'une semaine pour une épicerie, les voyages d'une année pour une agence), alors qu'ici l'ordre des itemsets est conservé et seule leur distance maximale est bornée.

Cette lecture ne prend son sens que relativement aux séquences d'une [[Base de séquences]] : c'est en parcourant les séquences datées qu'on décide si un motif y apparaît.
