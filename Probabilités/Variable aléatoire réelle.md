# Définition

Soit $(\Omega, \mathcal{F}, p)$ un [[Espace probabilisé|espace probabilisé]] modélisant une certaine expérience aléatoire. La valeur d'une variable aléatoire réelle $X$ définie via cette expérience est obtenue à partir du résultat $\omega \in \Omega$ de l'expérience aléatoire. $X$ est donc une application définie sur $\Omega$ et à valeurs dans $\mathbb{R}$, puisque la valeur de la v.a. est une fonction de $\omega$ :

$$X : \Omega \longrightarrow \mathbb{R}$$

$$\omega \longmapsto X(\omega) = \text{valeur de la v.a. } X \text{ pour le résultat } \omega \text{ de l'expérience aléatoire}$$

Autrement dit, une variable aléatoire réelle est le cas particulier d'une [[Variable aléatoire]] à valeurs dans $\mathbb{R}$.

On munit alors $\mathbb{R}$ de la [[Tribu borélienne|tribu borélienne]] $\mathcal{B}(\mathbb{R})$. Pour tout borélien $B$, l'ensemble

$$[X \in B] = \{\omega \in \Omega \mid X(\omega) \in B\} = X^{-1}(B)$$

doit être un [[Évènement|évènement]], donc un élément de la [[Tribu|tribu]] fondamentale $\mathcal{F}$ dont on a postulé l'existence : on dit que $X$ est *mesurable*.

Soit $(\Omega, \mathcal{F}, \mathbb{P})$ un espace probabilisé. Une **variable aléatoire réelle** $X$ est une application mesurable de $\Omega$ dans $\mathbb{R}$, i.e.

$$X : \Omega \longrightarrow \mathbb{R}, \qquad \omega \longmapsto X(\omega)$$

telle que

$$\forall B \in \mathcal{B}(\mathbb{R}) \quad [X \in B] \in \mathcal{F}.$$

# Interprétation

Si le résultat de l'expérience est un réel $\omega$, et que ce réel est justement la valeur de la v.a. considérée, alors il est naturel de prendre pour $\Omega$ la partie de $\mathbb{R}$ égale à l'ensemble des valeurs prises par la v.a. ; dans ce cas $X$ n'est rien d'autre que l'identité de $\Omega$ :

$$X : \Omega \longrightarrow \Omega$$

$$\omega \longmapsto \omega$$

C'est ce qui se passe lorsque aucun calcul n'est nécessaire, le résultat $\omega$ de l'expérience donnant directement la valeur de la v.a., *i.e.* $X = \text{Id}_{\Omega}$. Dans d'autres cas, il y a vraiment un calcul à faire à partir de $\omega$, qui n'est pas forcément un réel, pour déterminer la valeur $X(\omega)$.

À partir du moment où on ne s'intéresse plus aux résultats $\omega$ de l'expérience mais seulement aux valeurs $X(\omega)$ prises par la v.a., c'est-à-dire à sa [[Loi d'une variable aléatoire|loi]], la façon dont on a défini l'espace $\Omega$ devient secondaire. De plus il est important de pouvoir effectuer des opérations (somme, produit, ...) sur les v.a.r. Pour cela il est nécessaire que ces v.a.r. soient définies sur le même espace $\Omega$. Donc, plutôt que de définir précisément un espace $\Omega$ pour chaque nouvelle v.a. que nous aurons à considérer, il sera souvent utile de *postuler* l'existence d'un espace probabilisé fondamental $(\Omega, \mathcal{F}, \mathbb{P})$ qui modélise le hasard (un élément $\omega$ de $\Omega$ sera une *instance* du hasard), et toutes nos v.a.r. seront alors supposées définies sur $\Omega$.

# Remarque

La condition de mesurabilité n'est pas un obstacle en pratique. En effet, comme on ne définit pas explicitement $\Omega$ et $\mathcal{F}$, on doit supposer que $\mathcal{F}$ est assez grosse pour contenir tous les ensembles $[X \in B]$ (quel que soit le borélien $B$), de sorte que l'application $X$ (définie via le résultat d'une expérience aléatoire quelconque) est considérée mesurable.

La tribu $\mathcal{P}(\mathbb{R})$ de toutes les parties de $\mathbb{R}$ est trop grosse pour être munie de mesures de probabilité « intéressantes » : c'est ce qui justifie de choisir la tribu des boréliens $\mathcal{B}(\mathbb{R})$.

La [[Fonction de répartition]] d'une variable aléatoire réelle, définie par $F_X(t) = \mathbb{P}(X \leq t)$, caractérise sa loi.
