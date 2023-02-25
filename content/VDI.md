---
title: VDI
aliases: [Virtual Desktop Infrastructure]
---

- サーバ内にクライアントごとの仮想マシンを用意して仮想デスクトップ環境を構築する技術
- 利用者は[[ネットワーク]]を通じてVDIサーバ上の仮想デスクトップ環境に接続し，クライアントPCにはVDIサーバからの操作結果画面のみが転送される仕組みとなっている
- もし利用者の操作により不正なマルウェアをダウンロードしてしまったとしても，それが保存されるのはVDIサーバ上の仮想環境であるため，クライアントPCへの感染を防ぐことができる

[![Image from Gyazo](https://i.gyazo.com/ad16ae951f7d442e3216e2a1cce80102.gif)](https://gyazo.com/ad16ae951f7d442e3216e2a1cce80102)

[[セキュリティ]]