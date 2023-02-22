---
title: XAI実現のため考案されている手法や技術について調べる
tags: [2023/02/08]
aliases: []
ends: [[XAIについてまとめる]]
---

[[調べごと]]
# 具体例[^1]
人間が行う説明方法をAIに学習させる
実行されるプロセスの各ステップを可視化
どの入力変数がどういった出力結果に最も寄与するかを明示
不信自体の払拭

# [[XAI]]技術の大別[^2]
- ブラックボックス型
	- 既存の機械学習モデルを説明する技術
	- 研究の進展が著しく，汎用性が高い
- トランスペアレント型
	- 学習過程や構造が人にとって解釈可能な新型の機会学習モデル

# 説明[^3]
- 大域的: モデル全体の振る舞いを説明
	- Feature Importance (Gini Impurity)
	- Permutation Feature Importance
- 局所的: 特定のインプットに対してどうやってアウトプットが出たか説明
	- モデル全体は複雑でも一部の判断基準がわかればよい
	- LIME: 局所的に線形近似
	- SHAP: 協力ゲーム理論

# 代表的な研究がまとめられている[^4]

# [[XAI|EXplainable AI]]の手法[^5]
## ホワイトボックスの手法
モデルの構成が既知
### Integrated Gradients
[[1703.01365] Axiomatic Attribution for Deep Networks](https://arxiv.org/abs/1703.01365)
[[画像分類]]ではピクセル単位で判断の根拠を図示
テキストの種類の分類では単語を強調表示
## ブラックボックスの手法
モデルの構成情報を必要としない
### LIME
[[1602.04938] "Why Should I Trust You?": Explaining the Predictions of Any Classifier](https://arxiv.org/abs/1602.04938)
[[画像分類]]では特定の領域を強調するように判断の根拠を図示
解釈が容易なモデルでの局所的な近似
### SHAP
[[1705.07874] A Unified Approach to Interpreting Model Predictions](https://arxiv.org/abs/1705.07874)
## [[XAI|EXplainable AI]]に対する攻撃
[[1906.07983] Explanations can be manipulated and geometry is to blame](https://arxiv.org/abs/1906.07983)
誤った説明に誘導
AI開発者が予めモデルのパラメータを適切にチューニングしておくことで本攻撃を防ぐことができる
# 私のブックマーク 2019年の記事[^6]

# DARPAは[[XAI]]を大きく3つに分類[^7]
[Explainable Artificial Intelligence](https://www.darpa.mil/program/explainable-artificial-intelligence)
## 特徴量の可視化
LIME
PDP
## 解釈可能なモデルを生成
CORELS
## 解釈可能なモデルで近似
Born Again Tree

## [[XAI]]の応用例
Google Explainable AI
simMachines(isid)
網膜疾患の3次元画像診断(Deep Mind)

# 代表研究[^8]
## 重要特徴の提示
### ほしい追加情報
予測においてモデルが注目した特徴
### 手法
- LIME
	- どの可読特徴が予測に重要だったかをモデルから抽出
	- 方法: 可読特徴を使ってモデルを線形近似する
- SHAP
- Anchor
- Saliency
	- どの特徴(画像領域)が予測に重要だったかを抽出
	- 方法: 入力の微小変化がモデル出力に与える影響を勾配を使って評価
## 重要データの提示
### ほしい追加情報
予測への関連が深いデータ
### 手法
- Influence
	- 予測への影響が大きかった学習データを抽出する
	- 方法: 学習データの有無による影響を評価
	- [[Understanding Black-box Predictions via Influence Functions]]
- ProtoPNet
	- 予測への影響が大きかった学習データのパッチを抽出
	- 方法: 代表的なパッチをモデルに陽に埋め込む
- Concept Vector
	- ユーザの”コンセプト”データと，予測との関連の有無を抽出
	- 方法: 予測対象データを”コンセプト”の方向に微小変化させたときのモデル出力変化を評価

[^1]: [XAI（Explainable AI：説明可能なAI）／解釈可能性（Interpretability）とは？：AI・機械学習の用語辞典 - ＠IT](https://atmarkit.itmedia.co.jp/ait/articles/1908/19/news022.html)
[^2]: [XAI(eXplainable AI)技術の研究動向](https://www.jstage.jst.go.jp/article/jssmjournal/34/1/34_20/_pdf/-char/ja)ブラックボックス型について書かれていそう
[^3]: [XAI (説明可能なAI) の必要性](https://www.slideshare.net/KenichiroNishioka/xai-ai)
[^4]: [【記事更新】私のブックマーク「機械学習における解釈性（Interpretability in Machine Learning）」 – 人工知能学会 (The Japanese Society for Artificial Intelligence)](https://www.ai-gakkai.or.jp/resource/my-bookmark/my-bookmark_vol33-no3/)
[^5]: [そのAIの思考、説明できますか？いま求められるExplainable AI（説明可能なAI）｜ブログ｜NRIセキュア](https://www.nri-secure.co.jp/blog/explainable-ai)
[^6]: [【記事更新】私のブックマーク「説明可能AI」（Explainable AI） – 人工知能学会 (The Japanese Society for Artificial Intelligence)](https://www.ai-gakkai.or.jp/resource/my-bookmark/my-bookmark_vol34-no4/)
[^7]: [Explainable AIに関する技術調査 | ALBERT Official Blog](https://blog.albert2005.co.jp/2020/06/26/sunvey-on-explainable-ai/)
[^8]: [SSII2020TS: 機械学習モデルの判断根拠の説明​ 〜 Explainable AI 研究の近年の展開 〜​](https://www.slideshare.net/SSII_Slides/ssii2020ts-explainable-ai)