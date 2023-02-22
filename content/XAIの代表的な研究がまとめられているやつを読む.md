---
title: XAIの代表的な研究がまとめられているやつを読む
tags: []
aliases: []
estimation: 15
---
# Next Action
# Why
# How

# memo
情報が少し古いかもしれない
もう少し調べて，かぶったら見るみたいなアプローチがいい気がする
# Reference
[【記事更新】私のブックマーク「機械学習における解釈性（Interpretability in Machine Learning）」 – 人工知能学会 (The Japanese Society for Artificial Intelligence)](https://www.ai-gakkai.or.jp/resource/my-bookmark/my-bookmark_vol33-no3/)
2018年3月の記事

## 動向把握に有用な文献
[https://beenkim.github.io/slides/DLSS2018Vector_Been.pdf](https://beenkim.github.io/slides/DLSS2018Vector_Been.pdf)
[Interpretable Machine Learning](https://christophm.github.io/interpretable-ml-book/index.html)
[[1802.01933] A Survey Of Methods For Explaining Black Box Models](https://arxiv.org/abs/1802.01933)
[Workshop on Human Interpretability in Machine Learning (WHI)](https://arxiv.org/html/1607.02531)
[Proceedings of NIPS 2016 Workshop on Interpretable Machine Learning for Complex Systems](https://arxiv.org/html/1611.09139v1)
[Workshop on Human Interpretability in Machine Learning (WHI)](https://arxiv.org/html/1708.02666)
[Proceedings of NIPS 2017 Symposium on Interpretable Machine Learning](https://arxiv.org/html/1711.09889)

## 代表的な研究

### 大域的な説明
複雑なブラックボックスモデルを可読性の高い解釈可能なモデルで表現することで説明とする方法
深層学習モデルやランダムフォレストのような決定木のアンサンブルなど複雑なモデルを可読性の高いモデル，例えば単一の決定木やルールモデルで近似的に表現することでモデルの説明とする
[https://www.stat.berkeley.edu/users/breiman/BAtrees.pdf](https://www.stat.berkeley.edu/users/breiman/BAtrees.pdf)
[[1408.5456] Interpreting Tree Ensembles with inTrees](https://arxiv.org/abs/1408.5456)
[Node harvest](https://projecteuclid.org/journals/annals-of-applied-statistics/volume-4/issue-4/Node-harvest/10.1214/10-AOAS367.full)
[[1606.09066] Making Tree Ensembles Interpretable: A Bayesian Model Selection Approach](https://arxiv.org/abs/1606.09066)

### 局所的な説明
特定の入力に対するブラックボックスモデルの予測の根拠を提示することで説明とする方法
ある入力xをモデルがyと予測したときに，その予測の根拠を説明として提示する

["Why Should I Trust You?" | Proceedings of the 22nd ACM SIGKDD International Conference on Knowledge Discovery and Data Mining](https://dl.acm.org/doi/10.1145/2939672.2939778)
[A Unified Approach to Interpreting Model Predictions](https://papers.nips.cc/paper/2017/hash/8a20a8621978632d76c43dfd28b67767-Abstract.html)
[Understanding Black-box Predictions via Influence Functions](http://proceedings.mlr.press/v70/koh17a.html)

### 説明可能なモデルの設計
そもそも最初から可読性の高い解釈可能なモデルを作ってしまう方法

[Site Unreachable](https://www.kdd.org/kdd2017/papers/view/learning-certifiably-optimal-rule-lists-for-categorical-data)
[Interpretable Decision Sets: A Joint Framework for Description and Prediction](https://www.kdd.org/kdd2016/subtopic/view/interpretable-decision-sets-a-joint-framework-for-description-and-predictio)
[Prototype selection for interpretable classification](https://projecteuclid.org/journals/annals-of-applied-statistics/volume-5/issue-4/Prototype-selection-for-interpretable-classification/10.1214/11-AOAS495.full)
[Examples are not enough, learn to criticize! Criticism for Interpretability](https://papers.nips.cc/paper/2016/hash/5680522b8e2bb01943234bce7bf84534-Abstract.html)

深層学習モデルの説明
深層学習モデル，特に画像認識モデルの説明法
基本的には，モデルが画像内のどの部分を認識しているかを特定してハイライトすることで説明とする

[GitHub - marcoancona/DeepExplain: A unified framework of perturbation and gradient-based attribution methods for Deep Neural Networks interpretability. DeepExplain also includes support for Shapley Values sampling. (ICLR 2018)](https://github.com/marcoancona/DeepExplain)
[[1412.6806] Striving for Simplicity: The All Convolutional Net](https://arxiv.org/abs/1412.6806)
[On Pixel-Wise Explanations for Non-Linear Classifier Decisions by Layer-Wise Relevance Propagation | PLOS ONE](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0130140)
[[1703.01365] Axiomatic Attribution for Deep Networks](https://arxiv.org/abs/1703.01365)
[[1706.03825] SmoothGrad: removing noise by adding noise](https://arxiv.org/abs/1706.03825)
[Learning Important Features Through Propagating Activation Differences](http://proceedings.mlr.press/v70/shrikumar17a.html)

## 実応用に基づく研究の必要性
現時点では「こういった解釈・説明ができると便利だろう」という研究者の仮説に基づく

[[1702.08608] Towards A Rigorous Science of Interpretable Machine Learning](https://arxiv.org/abs/1702.08608)
[[1606.03490] The Mythos of Model Interpretability](https://arxiv.org/abs/1606.03490)

## 解釈性・説明性への過度な信頼/期待への注意
生成される説明を意図的にミスリードするよう変化
[[1711.00867] The (Un)reliability of saliency methods](https://arxiv.org/abs/1711.00867)