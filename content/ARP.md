---
title: ARP
tags: [ ]
aliases: [Address Resolution Protocol]
---
[[IPアドレス]]から対応する機器の[[MACアドレス]]を取得するプロトコル
以下の手順で取得する
1. ARP要求フレームに送信元の[[IPアドレス]]・[[MACアドレス]]と[[MACアドレス]]を得たいノードの[[IPアドレス]]を格納して，イーサネットネットワークにブロードキャストする
2. ARP要求フレームを受け取った各ノードは，フレーム内の解決対象[[IPアドレス]]が自身の[[IPアドレス]]と一致すれば，ARP応答フレームに自身の[[MACアドレス]]を格納して送信元にユニキャストで送信する
[![Image from Gyazo](https://i.gyazo.com/a9f18c7e1e4d4a551d55755c820a8417.png)](https://gyazo.com/a9f18c7e1e4d4a551d55755c820a8417)