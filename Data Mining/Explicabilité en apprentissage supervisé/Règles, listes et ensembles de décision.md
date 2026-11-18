#dmv-xai

# Définition

Les règles if-then sont celles de classifieurs simples tels que OneR : une règle associe une conjonction de conditions sur les variables d'entrée à une décision :

$$
\text{Past-Depression} \land \text{Melancholy} \Rightarrow \text{Depressed}
$$

Une règle m-of-n déclenche sa conclusion dès qu'au moins $m$ des $n$ conditions sont satisfaites :

$$
\text{2-of-}\{\text{Past-Depression}, \neg\text{Melancholy}, \neg\text{Insomnia}\} \Rightarrow \text{Healthy}
$$

# Modèle

Les listes de décision (decision lists) figurent parmi les modèles interprétables ; quelques méthodes : CPAR, Bayesian RL et RIPPER.

CPAR sélectionne les $k$ meilleures règles pour chaque classe et prédit la classe dont l'ensemble de règles a la plus forte exactitude attendue.

Bayesian RL apprend des règles et retient celles de probabilité a posteriori maximale pour une classe.

Une falling rule list est une liste de règles ordonnées dont le risque prédit décroît de la première à la dernière, comme l'illustre la table ci-dessous ; chaque règle est assortie de sa probabilité et de son support.

Un ensemble de décision (decision set) réunit plusieurs règles if-then, plusieurs règles pouvant conclure vers une même classe.

Une règle de régression hiérarchique par motifs (HiPaR) associe à une conjonction de conditions une régression linéaire :

$$
\text{Grape-variety}=\text{Merlot Noir} \land \text{Temp-sum}>2000 \Rightarrow \text{Mildew-intensity}=\alpha+\beta\times\text{dry-days}
$$

# Exemple

Règles if-then de classifieurs boîtes blanches sur trois tâches :

| Tâche | Si | Prédiction |
|---|---|---|
| adult | Pas de gain ni de perte en capital, jamais marié | ≤ 50K |
| adult | Pays = US, marié, heures de travail > 45 | > 50K |
| recidivism | Aucun antécédent, aucune violation de prison et crime non contre la propriété | Not rearrested |
| recidivism | Homme, noir, 1 à 5 antécédents, non marié, crime non contre la propriété | Re-arrested |
| lending | FICO score ≤ 649 | Bad Loan |
| lending | 649 ≤ FICO score ≤ 699 et 5 400 ≤ montant du prêt ≤ 10 000 | Good Loan |

Falling rule list de risque de malignité d'une tumeur :

| Règle | Conditions | Risque de malignité | Support |
|---|---|---|---|
| IF | IrregularShape AND Age ≥ 60 | 85.22 % | 230 |
| ELSE IF | SpiculatedMargin AND Age ≥ 45 | 78.13 % | 64 |
| ELSE IF | IllDefinedMargin AND Age ≥ 60 | 69.23 % | 39 |
| ELSE IF | IrregularShape | 63.40 % | 153 |
| ELSE IF | LobularShape AND Density ≥ 2 | 39.68 % | 63 |
| ELSE IF | RoundShape AND Age ≥ 60 | 26.09 % | 46 |
| ELSE | | 10.38 % | 366 |

Ensemble de décision pour le cancer du poumon, la dépression et le diabète :

- Si Respiratory-Illness=Yes, Smoker=Yes et Age ≥ 50, alors Lung Cancer
- Si Risk-LungCancer=Yes et Blood-Pressure ≥ 0.3, alors Lung Cancer
- Si Risk-Depression=Yes et Past-Depression=Yes, alors Depression
- Si BMI ≥ 0.3, Insurance=None et Blood-Pressure ≥ 0.2, alors Depression
- Si Smoker=Yes, BMI ≥ 0.2 et Age ≥ 60, alors Diabetes
- Si Risk-Diabetes=Yes, BMI ≥ 0.4 et Prob-Infections ≥ 0.2, alors Diabetes
- Si Doctor-Visits ≥ 0.4 et Childhood-Obesity=Yes, alors Diabetes

# Interprétation

Une règle if-then se lit directement dans le vocabulaire des variables d'entrée : la condition énonce un cas et la conclusion donne la décision associée.

Un classifieur à base de règles est donc un modèle boîte blanche : sa prédiction s'explique par les règles qui se déclenchent, sans couche d'interprétation post-hoc. C'est le même statut que celui d'un [[Arbre de décision]], dont les chemins se lisent comme des conjonctions de conditions, ou d'un [[Modèle linéaire]], dont les coefficients s'interprètent directement.

Les règles servent aussi de représentation cible aux [[Substituts globaux par arbre et par règles]], qui approchent un modèle opaque par un ensemble de règles lisibles, et aux [[Règles locales d'explication]], qui restreignent les règles au voisinage d'une instance.

# Remarque

La lisibilité décroît avec le nombre de règles et la longueur des antécédents : une règle m-of-n est moins immédiate à lire qu'une conjonction simple.

Une liste de décision porte de l'information dans l'ordre et la probabilité de ses règles ; une falling rule list ordonne en plus ses règles par risque décroissant, ce qui contraint son expressivité.

Dans un ensemble de décision, plusieurs règles peuvent concerner une même instance et une même classe, si bien que la décision finale dépend de la façon d'agréger les règles déclenchées.

Les deux règles de crédit se recouvrent à la borne 649 : un score de 649 relève à la fois de « FICO ≤ 649 » (Bad Loan) et de « 649 ≤ FICO ≤ 699 » (Good Loan) ; rien ne départage la borne.

Une règle reste une explication partielle : ce qu'elle laisse hors de sa condition, et la compréhension qu'en tire l'utilisateur, relèvent des [[Questions ouvertes de l'explicabilité]].
