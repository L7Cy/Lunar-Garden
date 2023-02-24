---
title:  Software-Defined Networking
tags: [2023/02/23]
aliases: [SDN]
---

- ソフトウェア制御によって物理的なネットワーク構成にとらわれない動的で柔軟なネットワークを実現する技術全般  
  
- SDNを実現するための技術標準が[[OpenFlow]]
- 既存のネットワーク機器がもつ制御処理(コントロールプレーン)と転送処理(データプレーン)を分離することで、[[OpenFlow]]コントローラが中央集権的に複数のスイッチの転送制御を管理
- [[OpenFlow]]ではパケットやフレームをフローとして扱い、フローの様々な情報を使って柔軟に転送制御できるようになっています。
- スイッチはOpenFlowコントローラと通信を行いながら、OpenFlowコントローラから提供されるフローテーブルや直接の転送指示により転送先を判断します。

[![Image from Gyazo](https://i.gyazo.com/f50ff9f6391fabc10ef77d9ddf7eb97f.gif)](https://gyazo.com/f50ff9f6391fabc10ef77d9ddf7eb97f)

[[ネットワーク]]