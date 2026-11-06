# Définition

Un **test d'hypothèse** est une démarche qui consiste à prendre une décision sur la véracité d'une assertion à partir de preuves expérimentales, tout en connaissant le risque attaché à cette décision.

# Interprétation

Le test ne démontre pas qu'une assertion est vraie : il fournit une règle de décision que l'on applique aux données observées, et dont l'issue est soit de retenir l'assertion, soit de la rejeter. Le risque de se tromper n'est pas subi après coup, il est posé dès le départ et fait partie de la règle de décision.

Les erreurs possibles d'une telle décision sont décrites par le [[Risque de première espèce|risque de première espèce]] et le risque de seconde espèce, et la capacité du test à détecter une différence réelle est sa [[Puissance d'un test|puissance]].

# Exemple

Les assertions que l'on cherche typiquement à tester sont de nature variée :

- la durée de vie moyenne d'un système dépasse un seuil $\theta_0$ (ou non) ;
- le taux d'arrivée des tâches dans un système de files d'attente est égal à $\lambda_0$ (ou non) ;
- la distribution d'un échantillon est gaussienne (ou non) ;
- deux moyennes estimées correspondent à une même moyenne (ou non) ;
- un processus d'arrivée observé est poissonnien (ou non).

Ces situations relèvent de familles de tests différentes, recensées dans [[Familles de tests statistiques]].

# Remarque

Chaque assertion testée se présente comme une alternative : elle est vraie, ou elle ne l'est pas. Formaliser ce couple de façon à ce qu'une seule des deux réponses soit retenue est l'objet de la note [[Hypothèse nulle et hypothèse alternative]], et la conduite complète du test est décrite dans la [[Méthodologie d'un test d'hypothèse|méthodologie d'un test d'hypothèse]].
