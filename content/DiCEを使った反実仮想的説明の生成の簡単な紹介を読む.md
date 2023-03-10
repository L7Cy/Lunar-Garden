---
title:  DiCEを使った反実仮想的説明の生成の簡単な紹介を読む
tags: [2023/02/26]
aliases: []
---

what-if "シナリオを探索することは、機械学習（ML）モデルを検査するための重要な方法である。DiCEライブラリは、望ましいモデル出力につながる「what-if」データポイントを生成することで、MLモデルの理解を助けます。形式的には、そのような「what-if」データポイントは、次の質問で記述される_反実仮想として_知られています。

> 入力に対するモデルの出力が 𝑥でございます 𝑦を入力すると、どのような出力になるのでしょうか？ 𝑥に変更されます。 𝑥′?

上記の質問に対する答えは 、𝑥′ を MLモデルに 入力するだけで、得る ことができます。 しかし、多くの場合、我々は逆の質問に興味があります： 𝑥 を変更 すると、モデルの出力はどのように変化するでしょうか？ 例えば、 分類器を検査するとき、我々はしばしば 、𝑥 の変更が 、望ましい予測されたクラスを もたらす かを知ることに興味が あります。 リグレッサーの 場合は、𝑥 の変化で、 希望の出力範囲に なるものに 興味があるかも しれません。 理想的には、これらの変更は 、分類器の局所的な決定ロジックを引き出すために_近接_させ、限られた特徴のセットを強調するために_疎に_し、同じ結果を達成することができる異なる方法を示すために_多様_である べき です。DiCEライブラリは、あらゆるMLモデルに対して、このような反実仮想的な例を生成する簡単なインタフェースを提供します。

近接性（最小限の変更）と多様性に加えて、反実仮想例のもう一つの重要な指標は、その**実現可能性**である。反実仮想例における変化が実現可能でない場合（例えば、特定の特徴の可能な範囲外）、その例はあまり有用ではありません。連続的特徴の可能な範囲（およびカテゴリー的特徴の可能な値）を指定することは、実現可能性の最も単純な形態の1つです。DiCEでは、`permited_range`パラメータにより、特徴の許容値をカスタマイズすることができます。一般に、実現可能性は、ある値が実現可能であるというだけでなく、[反実仮想が示す_変化が_](https://arxiv.org/abs/1912.03277)個人にとって実現可能であるかどうかに基づく複雑な概念です（例えば、20年は年齢特徴の実現可能な値かもしれませんが、人の年齢を22から20に変えることは実現可能ではありません）。DiCE は将来のリリースでこのような制約をサポートする予定です。

DiCE が生成する反実仮想例は、 与えられたモデル出力を 引き起こす**必然**性と**充足性 の** 条件と 密接な関係がある。 必要性と充足性は、モデルの出力を説明する直感的な方法を提供する。入力 𝑥 とモデル出力 ᵆ が あるとき 、特徴量 ↪Ll_1D465 𝑦 𝑖 が モデル出力を変え、他のすべての特徴量は一定 であれば、モデル 出力を引き起こす ために _必要_で あると 言えるでしょう。同様に、 𝑥𝑖 は、ᵆ を変更しても、𝑥𝑖 が一定でモデル出力を変更できない場合、モデル 出力を引き起こすのに _十分_であるとします。 DiCE では`features_to_vary`パラメータを設定することで、 必要性と十分性を検査 することができます。`features_to_vary`を𝑥𝑖 に 設定すると、生成された反実仮想はその特徴の必要 性を示すことになります。`features_to_vary`を𝑥𝑖 以外のすべての特徴に 設定すると 、反実仮想がないことから、その特徴が十分 であることが示される。実際には、単一の機能は十分でも必要でもないかもしれない--形式的な定義と `features_to_vary`パラメータは、機能の集合に簡単に変換される。

最後に、入力データ点に対する反実仮想を使って、各特徴の**局所重要度**スコアを導出することができる。局所的重要度スコアは、生成された反実仮想において変更される頻度によって特徴をランク付けする。すべての特徴の中で、必要な特徴は近接した反実仮想を生成するために変更される頻度が高いので、より高いスコアを受け取ることになる。`features_to_vary`と`permitted_range`パラメータを使用すると、反実仮想の探索空間を絞り込むことができ、結果として局所重要度スコアが向上する。入力点の集合が与えられると、ローカル重要度スコアを集約してグローバル重要度スコアを提供することができる。LIMEやSHAPのような説明手法と比較して、DiCEによって生成された特徴重要度スコアは、より多くの特徴に重要度を与える傾向がある；詳細は[本論文で](https://arxiv.org/abs/2011.04917)述べる。

- 反実仮想値を生成するために、DiCEはモデル不可知論と勾配ベースの2種類の方法を実装している
	-   **モデル非依存的**：これらの手法は，あらゆるブラックボックス分類器やリグレッサに適用されます．近接度（およびオプションでスパース性，多様性，実現可能性）に基づく損失関数を最適化しながら，入力点の近傍点をサンプリングすることに基づいています．このクラスのメソッドは、sklearn モデルに使用します。現在サポートされているメソッドは以下の通りです。
	    -   無作為化探索
	    -   遺伝的探索
	    -   KDツリー探索 (与えられた学習データセットから反実仮想を求める)
	-   **勾配ベース**。この方法は、tensorflowやpytorchのような深層学習ライブラリによって返されるような微分可能なモデルに適用されます。これらは、近接性、多様性、実現可能性に基づく明示的な損失最小化に基づいています。この方法は、この[論文で](https://arxiv.org/abs/1905.07697)説明されています。

![DiCE API](https://github.com/interpretml/DiCE/blob/main/docs/source/notebooks/images/dice_getting_started_api.png?raw=1)

DiCEは、学習データセットと学習済みモデルの2つの入力を必要とします。トレーニングデータセットが不明な場合（例えば、プライバシー上の理由）、完全なデータセットにアクセスしなくても動作します（例として、この[ノートブックを](https://colab.research.google.com/github/interpretml/DiCE/blob/main/docs/source/notebooks/DiCE_with_private_data.ipynb)参照）。以下、簡単な例を示す。

