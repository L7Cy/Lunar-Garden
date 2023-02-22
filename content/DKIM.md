---
title: DKIM
tags: []
aliases: [DomainKeys Identified Mail]
---
ディジタル署名を利用した送信ドメイン認証
予め公開鍵をDNSサーバに公開しておき，メールのヘッダにディジタル署名を付与して送信する
受信側メールサーバは，送信ドメインのDNSサーバから公開鍵を入手し，署名の検証を行う