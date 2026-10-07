# Définition

Un [[Modèle de Markov caché|modèle de Markov caché]] de paramètres $\lambda_N(\theta)$ est décrit par $\theta = \{\pi, A, B\}$ :

- $\pi$, distribution initiale des états ;
- $A$, probabilités de transition entre états ;
- $B$, probabilités conditionnelles des observations sachant l'état (cas discret).

L'estimation s'appuie sur $R$ échantillons d'apprentissage, c'est-à-dire $R$ séquences d'observations

$$\mathbf{o}^{(r)} = \{o_1^{(r)}, \ldots, o_{n_r}^{(r)}\} \quad \text{pour} \quad r \in [1, R].$$

Les [[Paramètres d'un modèle de Markov caché|paramètres]] sont obtenus par [[Méthode du maximum de vraisemblance|maximum de vraisemblance]] ; l'[[Estimateur du maximum de vraisemblance|estimateur]] s'écrit

$$\hat{\theta} = \arg \max_{\theta} \prod_{r=1}^{R} \mathbb{P}(\mathbf{o}^{(r)}; \lambda_N(\theta)).$$

# Propriétés

En supposant connues, pour chaque échantillon d'apprentissage, les séquences d'états cachés $s^{(r)} = \{s_1^{(r)}, \ldots, s_{n_r}^{(r)}\}$, on peut utiliser des estimateurs empiriques, construits à partir de [[Moyenne empirique|moyennes empiriques]] d'indicatrices :

$$\hat{\pi}_i = \frac{\sum_r \mathbb{I}_{(s_1^{(r)} = i)}}{R}$$

$$\hat{a}_{i,j} = \frac{\sum_r \sum_{t=2}^{n_r} \mathbb{I}_{(s_{t-1}^{(r)} = i,\, s_t^{(r)} = j)}}{\sum_r \sum_{t=1}^{n_r - 1} \mathbb{I}_{(s_t^{(r)} = i)}}$$

$$\hat{b}_{i,k} = \frac{\sum_r \sum_{t=1}^{n_r} \mathbb{I}_{(s_t^{(r)} = i)} \mathbb{I}_{(o_t^{(r)} = k)}}{\sum_r \sum_{t=1}^{n_r} \mathbb{I}_{(s_t^{(r)} = i)}}$$

Pour des densités conditionnelles continues, on remplace $\hat{b}_{i,k}$ par les estimateurs empiriques adéquats, construits à partir des observations associées à l'état $i$.

# Remarque

Ces estimateurs supposent connues les séquences d'états cachés ; ils constituent le point de départ de l'[[Algorithme de Baum-Welch]].
