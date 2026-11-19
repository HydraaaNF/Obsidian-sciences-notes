#ml-2

# Définition

Un **modèle génératif** est un modèle qui apprend la loi de probabilité $p(\mathbf{x})$ des données d'entraînement, puis échantillonne dans cette loi pour produire de nouvelles données semblables à celles de l'entraînement : texte, images, audio, vidéos.

# Modèle

Le cadre de travail est le suivant :

- les données sont un objet $\mathbf{x}$, par exemple du texte, une image, de l'audio ou une vidéo ;
- le modèle apprend la loi $p(\mathbf{x})$ de ces objets ;
- générer consiste ensuite à tirer un nouvel objet $\mathbf{x}$ selon cette loi.

Apprendre $p(\mathbf{x})$ revient à rendre les données d'entraînement probables sous le modèle : l'ajustement se fait par maximisation de la vraisemblance de ces données, ou de façon équivalente de leur log-vraisemblance.

# Propriétés

Plusieurs familles de modèles génératifs répondent à ce cadre.

- **Modèles autorégressifs** : la loi jointe se factorise en un produit de lois conditionnelles, chaque élément étant conditionné par tous les précédents :
  $$
  p(\mathbf{x}) = \prod_{t} p\left(x_t \mid x_1, \dots, x_{t-1}\right)
  $$
  C'est le principe de la [[Décomposition autorégressive d'une densité]], utilisé par WaveNet pour l'audio et par GPT pour le texte.
- **Modèles à variables latentes** : les [[Auto-encodeur|auto-encodeurs]] et les [[Auto-encodeur variationnel|VAEs]] en font partie.
- **Modèles adversariaux** : le [[Réseau antagoniste génératif]] oppose un générateur à un discriminateur.
- **Modèles de diffusion** : le [[Modèle de diffusion]] apprend à inverser un processus de bruitage progressif.
- **Flux normalisants** (*normalizing flows*) : autre famille, citée mais non traitée.

# Remarque

Un modèle génératif modélise la loi jointe $p(\mathbf{x})$ des observations, alors qu'un modèle discriminant modélise directement la loi conditionnelle $p(y \mid \mathbf{x})$ de l'étiquette étant donné l'entrée. Le premier permet de simuler de nouvelles données, le second seulement de prédire une étiquette ; un classifieur comme la régression logistique est donc discriminant, pas génératif.

En principe, tout modèle déjà étudié peut servir de modèle génératif. Les exemples usuels sont les décodeurs fondés sur un RNN ou un Transformer, qui relèvent de la famille des [[Décodeur génératif|décodeurs génératifs]], et les réseaux antagonistes génératifs.

Les familles se distinguent par leur façon de produire un échantillon : un passage depuis un vecteur aléatoire $\mathbf{z}$ pour les VAE et les GAN, un débruitage pas à pas pour les modèles de diffusion, un pas par échantillon pour les modèles autorégressifs. La comparaison figure dans le [[Panorama des modèles génératifs]].
