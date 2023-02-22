---
title:  Semantic Segmentation
tags: [2023/02/21]
aliases: []
---

# 概要
- 画像のピクセルをどの物体クラス(カテゴリー)に属するかで分類する方法
- 画像上の全ピクセルをクラスに分類する
- 同クラス間で重なりがある場合，同クラスの領域として認識する
	- 物体ごとの認識・カウントができない
# 代表的なモデル
- [[U-Net]]
- MULTISCALE
- HYBIRD CNN-CRF
# 代表的な評価指標
- IoU and per-pixel accuracy