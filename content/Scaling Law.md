---
title: Scaling Law
tags: 
aliases: [べき乗則]
---
- 概要
	- Transformerの性能はパラメータ数$N$・データ数$D$・計算量$C$を変数としたべき乗則に従う
	- $$L\propto N^{-\alpha_N}$$
	- $$L\propto D^{-\alpha_D}$$
	- $$L\propto C^{-\alpha_C}$$
	- $L$: cross-entropy
- Scaling Law(べき乗則)とは
	- $$f(x)=ax^k$$
	- 両辺で対数をとると
	- $$\log(f(x))=k\log(x)+\log(a)$$
	- となり，直線関係の式となる
- 画像
	- [![Image from Gyazo](https://i.gyazo.com/4b7f8a51e1df718982302de5f6e51f42.png)](https://gyazo.com/4b7f8a51e1df718982302de5f6e51f42)
		- 
	- [![Image from Gyazo](https://i.gyazo.com/d92a2eac91d2189a1c9857b80ab68388.png)](https://gyazo.com/d92a2eac91d2189a1c9857b80ab68388)
		- 
	- [![Image from Gyazo](https://i.gyazo.com/b691e54d8d4ea5c16db04d98adfbc555.png)](https://gyazo.com/b691e54d8d4ea5c16db04d98adfbc555)
		- 
- Scaling Lawの有効範囲には上限がない可能性がある
	- 理論上は3つの変数を上げ続ければTransformerの性能は無限に上がり続ける
- Scaling Lawがあらゆるドメインに適用される可能性がある
- 背景
	- べき乗則
- 課題・目的
	- 自己回帰型言語モデル
	- 性能はモデルアーキテクチャ，モデルのサイズ，モデルを訓練するために使用される計算能力，およびこの訓練プロセスで利用可能なデータに依存するのでは？
- 方法・実験
	- Transformer言語モデルにおける損失をモデルアーキテクチャ，モデルのサイズ，モデルを訓練するための計算能力，及びこの訓練プロセスで利用可能なデータへの依存性を様々な条件で変えて検証
	- 主要なパラメータ
		- $L$: テストデータにおける言語モデルのクロスエントロピー損失
		- $N$: 語彙とPositional Embeddingを除くパラメータ数
		- $B$: バッチサイズ
		- $S$: ステップ数
		- $C\approx 6NBS$: embedding以外の計算能力の推定値
		- $D$: トークン単位のデータセットサイズ
	- デコーダのみのTransformerモデルで1024トークンのコンテキストで平均化されたクロスエントロピー損失をAdamオプティマイザを用いて最適化
	- 1024トークンの512シーケンスのバッチサイズで，$2.5\times10^5$ステップでモデルを学習
	- モデルサイズ$N$，データセットサイズ$D$，形状（深さ，幅，Attention Head，フィードフォワード次元等）を変化させ，様々なモデルを訓練
- 結果
	- 言語モデルの性能はスケールに大きく依存
		- モデルサイズ$N$に大きく依存
		- 同様に計算リソース$C$，データセットサイズ$D$にも性能は依存
	- モデル形状に弱く依存
		- モデルの形状はそれほど性能に影響を与えない
	- 他の2つにボトルネックがない場合，学習のための計算能力C，データセットのサイズD，モデルのパラメータ数N（embedding除く）と性能の間でべき乗則が観測された
- 考察
	- 言語モデルにおけるLossの下限値は存在するため，その点に到達する前までにべき乗則は崩壊するはず
		- しかし，その計算量とモデルサイズまでは現時点では何桁も離れている
- まとめ
- 課題
# 論文
[Scaling Laws for Neural Language Models](https://arxiv.org/abs/2001.08361)
[[ja-Scaling Laws for Neural Language Models.pdf]]
[[al-Scaling Laws for Neural Language Models.pdf]]
[Scaling Laws for Autoregressive Generative Modeling](https://arxiv.org/abs/2010.14701)
[[ja-Scaling Laws for Autoregressive Generative Modeling.pdf]]
[[al-Scaling Laws for Autoregressive Generative Modeling.pdf]]
# 参考
- [【DL輪読会】Scaling Laws for Neural Language Models](https://www.slideshare.net/DeepLearningJP2016/dlscaling-laws-for-neural-language-models)
	- [OpenAIが発見したScaling Lawの秘密 - ディープラーニングブログ](https://deeplearning.hatenablog.com/entry/scaling_law)