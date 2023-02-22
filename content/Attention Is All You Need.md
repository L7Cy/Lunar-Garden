---
title: Attention Is All You Need
tags: []
aliases: []
---
[https://arxiv.org/pdf/1706.03762.pdf](https://arxiv.org/pdf/1706.03762.pdf)
## どんなもの？
[[RNN]]や[[CNN]]を用いない
Attention機構を使ったモデル
encoder・decoderモデル
## 先行研究と比べてどこがすごい？
並列処理が可能なため，学習時間を大幅に短縮できた

## 技術や手法のキモはどこ？
Multi-Head Attention
Positional Encoding
## どうやって有効だと検証した？
翻訳タスクにおいて，SoTAよりも高いBLEUスコアを叩き出した
## 議論はある？
Attentionにより翻訳以外のタスクやドメインへの適用も期待できるのではないか
## 次に読むべき論文は？
[[An Image is Worth 16x16 Words Transformers for Image Recognition at Scale]]