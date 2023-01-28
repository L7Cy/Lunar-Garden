---
title: macのdockを実質無効にする
tags: [tips,mac]
aliases: []
---

```sh
defaults write com.apple.dock "autohide-delay" -float "10000" && killall Dock
```
これで10000秒以上マウスがあてられたときだけdockが表示されるようになる
# 参考
[MacのDockを完全に消す](https://zenn.dev/dofuta/articles/4938e0f4e9dd15)
