---
title: ReLU
tags: [2023/02/08]
aliases: [Rectified Linear Unit,レルー,ランプ関数]
---

- 計算量が少ない
- 勾配消失を防ぐ
- $$\begin{aligned}
			  f(x)=
			    \left\{
			      \begin{array}{l}
			        0,~x\leq 0 \\
			        x,~x>0
			      \end{array}
			    \right.
			  \end{aligned}$$