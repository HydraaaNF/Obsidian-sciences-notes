#ml-2

# Définition

Les variantes du [[Réseau antagoniste génératif]] conservent les deux réseaux adverses et modifient l'un des éléments du dispositif : l'architecture des réseaux, leurs entrées, les données d'entraînement ou le mode de génération.

- **DCGAN** : générateur et discriminateur convolutifs ; le générateur emploie des convolutions transposées pour passer du vecteur $\mathbf{z}$ à une image, l'opération inverse de la [[Convolution en deux dimensions|convolution]].
- **Conditional GAN** : le générateur et le discriminateur reçoivent en plus une classe $y$, soit $G(\mathbf{z}, y)$ et $D(\mathbf{x}, y)$, ce qui permet de générer une classe choisie.
- **CycleGAN** : traduction d'image à image sans exemples appariés, par exemple cheval vers zèbre ou été vers hiver.
- **StyleGAN** : génération de visages en haute résolution, avec contrôle du style.
- **HiFi-GAN** : vocodeur audio, du même type que celui de [[Tacotron 2]] fondé sur [[Architecture WaveNet|WaveNet]], mais non autorégressif, donc beaucoup plus rapide.

# Interprétation

Chaque variante déplace un élément précis du dispositif adversarial, sans en changer le principe.

- DCGAN adapte les deux réseaux au traitement des images par des couches convolutives, et fait remonter le générateur du vecteur latent vers l'image par convolution transposée.
- Conditional GAN transforme une génération inconditionnelle en génération d'une classe imposée, en injectant l'étiquette $y$ dans les deux réseaux.
- CycleGAN supprime l'exigence de paires d'images correspondantes : deux domaines suffisent, et l'apprentissage porte sur la traduction de l'un vers l'autre.
- StyleGAN ajoute le contrôle d'un attribut global, le style, à la génération de visages de haute résolution.
- HiFi-GAN conserve le rôle de vocodeur décrit pour [[Tacotron 2]] mais remplace la génération autorégressive de [[Architecture WaveNet|WaveNet]] par une génération non autorégressive, d'où un gain de vitesse.

# Remarque

Le conditionnement de Conditional GAN ne modifie pas l'objectif adversarial : il ajoute seulement une entrée aux deux réseaux, si bien que le générateur peut produire un échantillon de la classe demandée plutôt qu'un échantillon quelconque.
