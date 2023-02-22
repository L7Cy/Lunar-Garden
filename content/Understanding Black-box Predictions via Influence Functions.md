---
title: Understanding Black-box Predictions via Influence Functions
tags: []
aliases: []
estimation: 15
---
# 原論文
[[1703.04730] Understanding Black-box Predictions via Influence Functions](https://arxiv.org/abs/1703.04730)
ICML 2017 best paper
[[1703.04730.pdf]]
[[ja-170304730pdf.pdf]]
[[al-170304730pdf.pdf]]
# 概要[^1]
- 影響関数を用いて，個々の学習データの有無や摂動が予測結果に与える影響を定式化
- 効率的な計算手法の提案
- 4つのユースケースの紹介
	- ネットワーク挙動の分析
	- ネットワークを混乱させる摂動の計算
	- ドメイン不適合の検知
	- ノイズラベルの検出
# 背景[^2]
![[influenceの背景]]
[[影響関数]]
[[影響関数の計算量削減方法について書く]]
[[Influensc Functionsの実験方法]]
# 関連研究[^2]
- あるdata点周りのみを考慮してよりsimpleなmodelでfittingさせて解析[^3]
- data点にノイズを加えて予測がどう変化するか[^4] [^5]
これらの研究は与えられたモデルがどう予測を変化させるかを解析したもの
本研究は「なぜこのモデルに至ったのか」について考察するアプローチ
# memo
## 参考になるかも
[影響関数について. こんにちは！カラクリ株式会社 R&D チームの北村です。… | by Takuma Kitamura | KARAKURI Techblog | Medium](https://medium.com/karakuri/影響関数について-18215944f8ad)
[予測モデルを理解するための技術](https://www.nims.go.jp/MII-I/event/d53p8f0000006hds-att/d53p8f0000007j9o.pdf)
[Influence functionをロジスティック回帰に適用する - Qiita](https://qiita.com/futakuchi0117/items/7aa62b155f8a94c86217)
[6.4 Influential Instances | Interpretable Machine Learning](https://hacarus.github.io/interpretable-ml-book-ja/influential.html#%E5%BD%B1%E9%9F%BF%E9%96%A2%E6%95%B0-influence-functions)
[Influence Functionでインスタンスの重要度を解釈する - Dropout](https://dropout009.hatenablog.com/entry/2021/07/19/223929)
[influence/main.ipynb at main · dropout009/influence · GitHub](http://colab.research.google.com/github/dropout009/influence/blob/main/main.ipynb)
## 実装
### influence-release
[GitHub - kohpangwei/influence-release](https://github.com/kohpangwei/influence-release)
### Qiitaの記事[^1]のやつ
[GitHub - yuzupepper/inf_func: implementation of influence function](https://github.com/yuzupepper/inf_func)
[[inf_funcを実行してみる]]
### PyTorch
[GitHub - nimarb/pytorch_influence_functions: This is a PyTorch reimplementation of Influence Functions from the ICML2017 best paper: Understanding Black-box Predictions via Influence Functions by Pang Wei Koh and Percy Liang.](https://github.com/nimarb/pytorch_influence_functions)
[[InfluenceのPyTorch実装を実行してみる]]

[^1]: [論文メモ：Understanding Black-box Predictions via Influence Functions - Qiita](https://qiita.com/crab/items/52261633c9678e2e0aa0)
[^2]: [[DL輪読会]Understanding Black-box Predictions via Influence Functions](https://www.slideshare.net/DeepLearningJP2016/dlunderstanding-blackbox-predictions-via-influence-functions)
[^3]: [[1602.04938] "Why Should I Trust You?": Explaining the Predictions of Any Classifier](https://arxiv.org/abs/1602.04938)
[^4]: [[1312.6034] Deep Inside Convolutional Networks: Visualising Image Classification Models and Saliency Maps](https://arxiv.org/abs/1312.6034)
[^5]: [[1602.07043] Auditing Black-box Models for Indirect Influence](https://arxiv.org/abs/1602.07043)