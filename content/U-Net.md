# 概要
title: U-Net
- FCN(Fully Convolution Network)の一つ
- 画像のセグメンテーション（物体がどこにあるのか）を推定するためのネットワーク
- 左右対称でアルファベットのUに似ていることから
- Olafらによって生物医学のために開発された
- エンコーダとデコーダから成る
![](https://camo.qiitausercontent.com/3f8dc36390b8034a47ffec327aff9fe642e16607/68747470733a2f2f71696974612d696d6167652d73746f72652e73332e61702d6e6f727468656173742d312e616d617a6f6e6177732e636f6d2f302f3230363731362f36643563633364352d616638662d343739392d616265392d3265653334376236313365322e706e67)
## 画像の説明
## ボックス
- 青ボックス
	- 画像
	- 特徴マップ
- 白ボックス
	- コピーされた特徴マップ
- ボックスの上の数字
	- チャンネル数
## 矢印
- 青矢印
	- kernel size 3×3
	- padding0の畳み込み
	- ReLU
- グレー矢印
	- 特徴マップのコピーをクロップ
- 赤矢印
	- kernel size 2×2のmax-pooling
- 青緑矢印
	- kernel size 1×1の畳み込み
# 論文
[[1505.04597] U-Net: Convolutional Networks for Biomedical Image Segmentation](https://arxiv.org/abs/1505.04597)
# 参考
- [画像セグメンテーションのためのU-net概要紹介](https://www.acceluniverse.com/blog/developers/2019/11/u-net.html)
- [U-Netとは | スキルアップAI | AI人材育成・開発組織の構築支援](https://www.skillupai.com/blog/tech/segmentation2/)
- [tensorflow2.0でU-Netを実装する - Qiita](https://qiita.com/hiro871_/items/871c76bf65b76ebe1dd0)
- [U-netによる画像セグメンテーション(Image segmentation)の解説 – S-Analysis](https://data-analysis-stats.jp/%E6%B7%B1%E5%B1%9E%E5%AD%A6%E7%BF%92/u-net%E3%81%AB%E3%82%88%E3%82%8B%E7%94%BB%E5%83%8F%E3%82%BB%E3%82%B0%E3%83%A1%E3%83%B3%E3%83%86%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3image-segmentation%E3%81%AE%E8%A7%A3%E8%AA%AC/)
# 中で行われている処理
## Semantic segmentation
- 画像のピクセルそれぞれをクラス分類するタスク
- 画像のクラス分類と異なる点
	- 画像全体をクラス分類しない点
## Fully Convolution Network
- 一般的なCNNは畳み込み層と全結合層がある
- FCNはCNNの全結合層を畳み込み層に置き換えたもの
	- これにより，「物体がなにであるか」という出力から「物体がどこにあるか」という出力になる
## deconvolusion
- 逆畳み込み
- 畳み込み処理の逆処理
## skip-conection
- 畳み込み処理を加えていくと，
	- 「物体がなにであるか」についての特徴を抽出する
	- poolingの影響で「物体がどこにあるか」についての特徴が失われていく
	- 物体の位置情報が満足に復元できない場合がある
		- これを解決するもの
- 畳み込みを行った後，特徴マップを保持
- 逆畳み込みをする画像に足し合わせる