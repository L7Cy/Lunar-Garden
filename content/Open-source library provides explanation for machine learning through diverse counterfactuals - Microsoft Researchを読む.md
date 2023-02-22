---
title: Open-source library provides explanation for machine learning through diverse counterfactuals - Microsoft Researchを読む
tags: [2023/02/13,]
aliases: []
---

source: [Open-source library provides explanation for machine learning through diverse counterfactuals - Microsoft Research](https://www.microsoft.com/en-us/research/blog/open-source-library-provides-explanation-for-machine-learning-through-diverse-counterfactuals/)
author: Alexis Hagen

> ## Excerpt
> Microsoft researchers and collaborators created an open-source library to explore “what-if” scenarios for machine learning models. Learn how their method generates multiple diverse counterfactuals at once and gives insight into ML algorithm decision making.

---
![diagram](https://www.microsoft.com/en-us/research/uploads/prod/2020/01/MSR-Amit_1400x788-v3-1blog.gif)ある金融会社に融資を申し込んだ人が、その金融会社から融資を受ける人を決定するための機械学習アルゴリズムによって、申し込みが却下された場合を考えてみましょう。このような人に、アルゴリズムが下した決断をどのように説明しますか？一つは、収入やクレジットスコアなど、アルゴリズムの判断に寄与した特徴のリストを提供することです。現在の説明方法の多くは、アルゴリズムの特性を分析するか、より単純で解釈しやすいモデルで近似することによって、この情報を提供しています。

しかし、これらの説明は、この人が将来融資を受けられる可能性を高めるために次に何をすべきかを決める助けにはならない。特に、予測に最も重要な特徴を変えても、実際には判断が変わらない可能性があり、場合によっては、年齢など重要な特徴を変えることが不可能な場合もある。同じような議論は、就職希望者の審査、健康保険の決定、政府援助の支出などのシナリオで、意思決定者を支援するためにアルゴリズムが使用される場合にも当てはまります。

従って、アルゴリズムから好ましい結果を得たであろう代替的な特徴入力を示すことも同様に重要である。このような代替例は、仮想的な入力についての推論によってアルゴリズムを説明することから、[_反実仮想的説明と_](https://arxiv.org/abs/1711.00399)呼ばれる。事実上、それらは人が「もしも」の問いに答えるのを助ける。私の特徴のいくつかが異なっていた代替的な[反実仮想世界では](https://www.microsoft.com/en-us/research/blog/dowhy-a-library-for-causal-inference/)何が起こったのだろうか？

スポットライトオンデマンドイベント

[![Abstract image with blue, purple, and orange tiles moving upward](https://www.microsoft.com/en-us/research/uploads/prod/2022/09/WebsiteHero_1400x788_B.jpg)](https://www.microsoft.com/en-us/research/event/microsoft-research-summit-2022/?OCID=msr-researchsummit_Blog_PromoMod)

## マイクロソフトリサーチサミット2022

**オンデマンド**  
今すぐ視聴して、研究コミュニティが直面している最も差し迫った問題について学び、新しい技術が人類に最も広範な利益をもたらすことを確実にする方法について120人以上の研究者との会話に耳を傾けてみてください。

この問題に対して、私たちの研究チームは、有用性と相対的な容易さを考慮した多様な反証を多数生成する方法を提案しています。本研究の詳細は、スペイン・バルセロナで開催される[ACM Conference on Fairness, Accountability, and Transparency (ACM FAT\* 2020](https://fatconference.org/2020/index.html)) で「[Explaining Machine Learning Classifiers through Diverse Counterfactual Explanations](https://www.microsoft.com/en-us/research/publication/explaining-machine-learning-classifiers-through-diverse-counterfactual-examples/)」という論文で発表される予定です。また、私たちの反実仮想説明文生成のフレームワークを実装したライブラリ「[Diverse Counterfactual Explanations（DiCE）](https://github.com/microsoft/dice)」をオープンソースで公開しました。単一の反実仮想の生成は容易ですが、有用な反実仮想を複数生成することが大きな課題であり、それが本手法の根底にある目標です。本研究は、[コロラド大学ボルダー校のChenhao Tan](https://chenhaot.com/)氏、および、現在インドMicrosoft Researchの[SCAIセンターフェロー](https://www.microsoft.com/en-us/research/collaboration/scai/)であるRamaravind Mothilal氏と共同で行われました。

### その課題とはユーザーやシステム構築者にとって有用な複数の反実仮想の生成

特に、_反実仮想的説明とは_、機械学習モデルが異なる判断を行う結果となる、元の特徴量入力に対する摂動を指す。このような説明は、意思決定に直面する人にとって確かに有用であるが、システム構築者や評価者がアルゴリズムをデバッグする際にも有用である。この意味で、反実仮想例は敵対的な例と似ているが、問題となる例は元の入力に近いだけでなく、敏感な属性など結果に影響しないはずの様々なドメイン依存の制限に基づくことを除けば、である。おそらく、反実仮想の最大の利点は、モデルが変わらない限り、常に元のアルゴリズムに忠実であり、反実仮想の説明に従えば、望ましい結果が得られることである。

可能な反実仮想の空間が広いため、どの例がユーザーにとって実用的であるか、あるいはどの例がモデル構築者が関心を持つであろう様々な特性を公開するかは不明である。例えば、ある反実仮想の説明は家賃を変更することを提案するかもしれないが、同じ効果をもたらす他の可能な反実仮想があるかどうか、異なる変更を行うことが相対的に容易であるかどうかは開示されていない。

### 私たちの解決策多くの異なる反実仮想を同時に作成する方法

これらの追加要因を考慮した代替的な反実仮想を見つけるために、我々の手法は多様な反実仮想の集合を一度に生成する。ウェブ検索エンジンのように、多様な選択肢のセットを提供することで、人は最も行動しやすい選択肢を情報に基づき選択することができる。また、アルゴリズム開発者は、結果を変更する複数の方法をテストすることができる。  
我々は、モデルが反実仮想的な例に対して望ましい結果を提供することを保証するだけでなく、多様性と元の入力への近接性の両方を最適化する共同最適化問題を定式化することでこれを実現する。さらに、様々な種類のユーザー固有の要求を追加することもサポートしています。最適化問題に制約を加えることで、どの機能をどれだけ変化させるか、また各機能を変化させる相対的な難易度を指定することができる。図1は、我々の手法を適用して、ある人の収入を予測する機械学習モデルを説明した例である。

![diagram](https://www.microsoft.com/en-us/research/uploads/prod/2020/01/Picture1-5e2b82c0d485b.png)

図1：[成人所得データセットから](https://archive.ics.uci.edu/ml/datasets/Adult)、ある人物の所得を分類する与えられた機械学習モデルに基づく反実仮想の説明。DiCEは最適化関数を構築し、元の入力に近接し、かつ多様な_k=4の_反事実を生成する。反実仮想の例におけるダッシュは、それらの特徴に変化がないことに対応する。

我々は、提案手法が多様な反実仮想の集合を生成する上で、現行の手法を凌駕することを見出した。また、我々は反実仮想の印象的な特性を発見した：ほんの一握りの反実仮想の説明が、単純な_k-nearest_ neighbors分類モデルを用いた機械学習アルゴリズムを局所的に近似することができる。つまり、反実仮想の説明は、[LIMEの](https://github.com/marcotcr/lime)ような目的に特に最適化された手法と同等の精度で、局所的な決定境界を近似することができるのである。

しかし、何をもって有用な反実仮想とするかはアプリケーションドメインによって異なり、実世界のシステムに反実仮想の例を展開するためには多くの課題が残されている。その一つが、特徴量を変更する際の特徴量間の因果関係の扱いである。特徴は真空中に存在するのではなく、データ生成プロセスから生成され、その修正に制約がある。したがって、反実仮想的な説明は特徴を独立して変更することができるが、提案された変更が不可能な場合もある（例えば、老化せずに高い学位を取得するなど）。我々は現在、因果的制約を満たす反実例を生成できる手法を開発しており、[因果的機械学習に関する](http://tripods.cis.cornell.edu/neurips19_causalml/)ワークショップ「NeurIPS 2019」でその[成果を](https://arxiv.org/abs/1912.03277)発表しました。ACM FAT\* 2020カンファレンスで発表される別の[論文では](https://arxiv.org/abs/1912.04930)、私の同僚である[Solon Barocasが](https://www.microsoft.com/en-us/research/people/solon/)、示すべき説明の決定と、アルゴリズムについて明らかにしすぎることの潜在的影響に関するいくつかの他の重要な問題を提議しています。

これらの疑問に対する研究を加速するために、我々は[DiCE（Diverse Counterfactual Explanations）というオープンソースのライブラリを](https://github.com/microsoft/dice)リリースした。これは我々の手法を実装し、他の反実仮想的説明手法をテストするためのフレームワークを提供するものである。私たちは、このライブラリにさらに多くの手法を追加し、機械学習モデルを説明するための広範な[フレームワークであるInterpretMLと](https://github.com/interpretml/interpret-community)統合することを期待しています。多様性、近接性、因果関係の実現可能性という複数の目的を考えると、このライブラリによって、異なる反実仮想説明手法の開発とベンチマークが可能になり、モデル構築者、評価者、エンドユーザの異なるユースケースに反実仮想生成を適応させるための容易な方法を提供できることを期待しています。研究者がこれらの目標を達成できるよう、私たちのチームはライブラリへの追加や新しい手法に関する情報など、GitHubページへの定期的なアップデートを公開していく予定です。
