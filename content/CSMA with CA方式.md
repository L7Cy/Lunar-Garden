---
title: CSMA with CA方式
tags: []
aliases: [Carrier Sense Multiple Access with Collision Avoidance]
ends: 
---
無線LANのアクセス制御方式
送信を行うノードは，利用したい周波数帯が使われていないかを確認後，必ずランダムな時間（バックオフ制御時間）だけ待ってから送信を開始する
衝突が発生し，フレームが壊れてしまってもそれを検出できないため，データを受け取ったノードはACKを応答することでデータを正常に受け取ったことを通知する
送信側ノードは，設定時間内にACKを受信できなければ，干渉が発生したと判断して一定時間後に再度送信する