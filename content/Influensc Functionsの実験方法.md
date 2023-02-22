---
title: Influensc Functionsの実験方法
tags: [ ]
aliases: []
estimation: 15
---
Influence FunctionsのPyTorch実装[^1]を使用したリポジトリ[^2]を使って実験を行った
MNISTをscikit-learnのロジスティック回帰モデルを使って学習を行い，影響関数を用いて計算したときのlossの変化と一つずつ抜いて計算したときのlossの変化を比較した
つまり，影響関数が学習データの貢献度合いを正しく近似できているかを検証した

[^1]: [GitHub - nimarb/pytorch_influence_functions: This is a PyTorch reimplementation of Influence Functions from the ICML2017 best paper: Understanding Black-box Predictions via Influence Functions by Pang Wei Koh and Percy Liang.](https://github.com/nimarb/pytorch_influence_functions)
[^2]: [GitHub - mkirchhof/pytorch_influence_functions_stable: This is a [Stable] PyTorch reimplementation of Influence Functions from the ICML2017 best paper: Understanding Black-box Predictions via Influence Functions by Pang Wei Koh and Percy Liang.](https://github.com/mkirchhof/pytorch_influence_functions_stable)