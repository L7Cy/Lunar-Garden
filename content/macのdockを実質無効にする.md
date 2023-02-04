---
title: macのdockを実質無効にする
tags: [tips,mac]
aliases: []
---

私はmacでアプリを切り替えるのにraycastを使っているため，dockは一切使わない．設定画面から一応隠すように設定はできるが，マウスカーソルを端に持っていくとdockが出てきてしまう．出てこない方法を探したところ，擬似的にdockを非表示する方法を見つけた．

```sh
defaults write com.apple.dock "autohide-delay" -float "10000" && killall Dock
```

これで10000秒以上マウスがあてられたときだけdockが表示されるようになる

# 参考
[MacのDockを完全に消す](https://zenn.dev/dofuta/articles/4938e0f4e9dd15)
