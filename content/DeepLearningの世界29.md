---
title: DeepLearningの世界29
tags: [2022/11/07]
aliases: []
---

# 忙しい人のためのTransformer
## 全体像
- Transformerは機械翻訳のモデル
- Multi-Head Attentionが一番重要
	- 注目すべき情報を上手く選べる
	- 並列処理との相性が良い
$$\text{Multi-Head}(Q,K,V)=\text{concat}({head}_i)W^o$$
$${head}_i=\text{Attention}(QW^Q_i,KW^K_i,VW^v_i)$$
$$\text{Attention}(Q,K,V)=\text{softmax}\left(\frac{Q^t\!K}{\sqrt{d}}\right)V$$
## Scaled Dot-Product Attention
- 入力$q$に対して，$k$達との類似度を計算して，似ているkeyに対応するvalueを重み付けて足す
$$\text{Attention}(\vec{q},k,v)=\text{softmax}\left(\frac{\vec{q}^t\!K}{\sqrt{d}}\right)V$$
$$\vec{q}^t\!K=\vec{q}(\vec{k_1},\vec{k_2},\cdots,\vec{k_m})$$
$$=(\vec{q}\cdot\vec{k_1},\vec{q}\cdot\vec{k_2},\cdots,\vec{q}\cdot\vec{k_m})$$
## Multi-Head Attention
- 行列かけて，Attentionして，つなげて，行列かける
- 行列で回転させることによって，いろんな角度からXを比較してやって，どれに注目すべきか決めて情報処理する