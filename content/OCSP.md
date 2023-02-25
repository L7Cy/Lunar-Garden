---
title:  OCSP
tags: [2023/02/25]
aliases: [Online Certificate Status Protocol]
---

- リアルタイムでディジタル証明書の失効情報を検証し、有効性を確認するプロトコル
- OCSPクライアントは、確認対象となるディジタル証明書のシリアル番号等をOCSPレスポンダに送信し、有効性検証の結果を受けとる
	- クライアント自身が[[CRL]]を取得・検証する手間を省くことができる

[![Image from Gyazo](https://i.gyazo.com/f1728f16f018fef2d6798dbe4c3399af.gif)](https://gyazo.com/f1728f16f018fef2d6798dbe4c3399af)

[[情報セキュリティ]]