---
title:  Network Functions Virtualisation
tags: [2023/02/24]
aliases: [NFV,ネットワーク機能の仮想化]
---

- 従来は[[ルータ]]、スイッチ、[[ファイアウォール]]、ロードバランサなどの専用機器で行われていた機能を、汎用サーバ内の仮想マシン上で動く[[ソフトウェア]]として実装するアーキテクチャ
	- 仮想化技術を利用
- コスト削減・信頼性向上
	- 複数のネットワーク機器の機能を1つの物理サーバに集約できるため

- [[Software-Defined Networking|SDN]]は
	- ネットワーク機器の機能のうち制御部だけを[[ソフトウェア]]化
- するが，NFVは
	- 機器ごと仮想化
- する

[![Image from Gyazo](https://i.gyazo.com/50d384e0342b13ec0a78f476938fae33.gif)](https://gyazo.com/50d384e0342b13ec0a78f476938fae33)

[[ネットワーク方式]]