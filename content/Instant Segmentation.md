---
title:  Instant Segmentation
tags: [2023/02/21]
aliases: []
---
# 概要
- 画像のピクセルをどの物体クラス(カテゴリー)に属するか，どのインスタンスに属するかで分類
- 物体ごとの領域を分割し，かつ物体の種類を認識すること
- region of interestに対してsegmentationを行う
	- 画像全てのピクセルに対してラベルを振ることはしない
# 代表的なモデル
- Mask  R-CNN
- DeepMask
- FCIS
# 代表的な評価指標
- average precision over different IoU thresholds