#ml-2

# Définition

Les familles de [[Modèle génératif|modèles génératifs]] apprennent toutes la loi $p(\mathbf{x})$ des données pour en tirer de nouveaux échantillons, mais elles se distinguent par la forme sous laquelle elles écrivent cette loi et par la manière dont elles produisent un échantillon :

- les modèles autorégressifs, dont WaveNet est l'exemple audio ;
- les [[Auto-encodeur variationnel|auto-encodeurs variationnels]] et les [[Réseau antagoniste génératif|réseaux antagonistes génératifs]] ;
- les [[Modèle de diffusion|modèles de diffusion]].

# Propriétés

**Famille autorégressive.** La loi jointe se factorise en un produit de lois conditionnelles, chaque échantillon $x_t$ étant conditionné par tous les précédents :
$$
p(\mathbf{x}) = \prod_t p\left(x_t \mid x_1, \dots, x_{t-1}\right)
$$
La génération est séquentielle : tirer $x_t$, l'ajouter à l'entrée, recommencer, selon le principe de l'[[Inférence autorégressive|inférence autorégressive]] et de la [[Décomposition autorégressive d'une densité]].

**Famille à variables latentes et famille antagoniste.** Un [[Auto-encodeur variationnel]] et un [[Réseau antagoniste génératif]] partent d'un vecteur aléatoire $\mathbf{z}$ et produisent l'échantillon en un seul passage.

**Famille par débruitage.** Un [[Modèle de diffusion]] obtient l'échantillon en retirant le bruit pas à pas.

# Exemple

Sur de l'audio, WaveNet illustre le coût du schéma autorégressif : un pas par échantillon, soit $16\,000$ pas pour une seconde d'audio, là où un VAE ou un GAN ne demande qu'un passage à partir de $\mathbf{z}$.
