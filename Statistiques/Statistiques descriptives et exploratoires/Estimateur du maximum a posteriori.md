# Définition

L'**estimateur du maximum a posteriori** (MAP) est donné par

$$\hat{\theta} = \operatorname*{argmax}_{\theta} p(\theta \mid x) = \operatorname*{argmax}_{\theta} p(x \mid \theta)p(\theta)$$

# Interprétation

- L'[[Estimateur du maximum de vraisemblance|estimateur du maximum de vraisemblance]] peut conduire à de mauvaises solutions : par exemple, des variances très petites pour des gaussiennes lorsque la quantité de données d'entraînement est faible.
- L'estimateur du maximum a posteriori agit comme un estimateur du maximum de vraisemblance régularisé : il se place entre l'a priori et l'[[Estimateur du maximum de vraisemblance|estimation du maximum de vraisemblance]].

# Remarque

Le maximum a posteriori est l'un des estimateurs de l'[[Estimation bayésienne]], aux côtés de l'[[Estimateur du minimum d'erreur quadratique moyenne]].

Lorsque la loi a priori $p(\theta)$ est uniforme, il coïncide avec l'[[Estimateur du maximum de vraisemblance|estimateur du maximum de vraisemblance]] : la maximisation de $p(x \mid \theta)p(\theta)$ se réduit alors à celle de $p(x \mid \theta)$.
