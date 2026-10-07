# Théorème

Si le support de la [[Échantillon et échantillonnage|loi mère]] ne dépend pas de $\theta$, tout [[Biais d'un estimateur|estimateur sans biais]] $T$ de $\theta$ vérifie

$$\mathbb{V}(T) \geq V_0 \quad \text{avec } V_0 = \frac{1}{I_n(\theta)}.$$

$V_0$ est appelée la borne de Fréchet-Darmois-Cramér-Rao (F.D.C.R.) ; $I_n(\theta)$ désigne l'[[Information de Fisher]] apportée par l'échantillon.

# Interprétation

La borne $V_0$ est un plancher pour la variance : aucun estimateur sans biais de $\theta$ ne peut avoir une variance inférieure. Comme elle est l'inverse de l'information de Fisher apportée par l'échantillon, plus l'échantillon est informatif sur $\theta$, plus cette variance minimale possible est petite.

# Remarque

Un estimateur sans biais dont la variance atteint exactement la borne $V_0$ est un [[Estimateur efficace]]. Pour un [[Estimateur du maximum de vraisemblance]] sans biais, l'efficacité se vérifie ainsi en comparant sa variance à la borne.
