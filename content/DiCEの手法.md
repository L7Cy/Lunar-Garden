---
title:  DiCEの手法
tags: [2023/02/27]
aliases: []
---

- optimization

$$\begin{gathered}
\mathcal{C}(\boldsymbol{x})=\underset{\boldsymbol{c}_1, \ldots, \boldsymbol{c}_k}{\arg \min } \frac{1}{k} \sum_{i=1}^k \operatorname{yloss}\left(f\left(\boldsymbol{c}_i\right), y\right)+\frac{\lambda_1}{k} \sum_{i=1}^k \operatorname{dist}\left(\boldsymbol{c}_i, \boldsymbol{x}\right) \\
-\lambda_2 \text { dpp\_diversity }\left(\boldsymbol{c}_1, \ldots, \boldsymbol{c}_k\right)
\end{gathered}$$