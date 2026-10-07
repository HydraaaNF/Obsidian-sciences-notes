# Propriétés

Par rapport à [[DBSCAN]], le [[Clustering spectral|clustering spectral]] présente les avantages et inconvénients suivants.

**Avantages**

- **personnalisation de la matrice d'affinité** : l'utilisateur peut adapter la matrice d'affinité d'après sa connaissance du domaine ;
  - **moins sensible aux paramètres de localité** : davantage de connexions sont conservées et le [[k-means]] écarte les moins importantes ;
- **gère plus robustement des clusters de densités variables**.

**Inconvénients**

- **sensibilité au réglage des paramètres** (y compris le choix de la matrice d'affinité) ;
- **complexité computationnelle plus élevée** ;
- **ne gère pas le bruit et les outliers** ;
- **exige de spécifier le [[Choix du nombre de clusters|nombre de clusters]]**.

# Remarque

Voir aussi les avantages et inconvénients du [[Avantages et inconvénients du k-means|k-means]] et ceux de [[Avantages et inconvénients de DBSCAN|DBSCAN]].
