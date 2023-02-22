---
title: ノートを埋め込むときに2hoplinkが出てきてしまう問題を解決する
tags: [2023/02/08]
aliases: []
---

```css
.markdown-embed .markdown-preview-view > .twohop-links-container{
    display: none;
  }
```
このスニペットを入れて解決した