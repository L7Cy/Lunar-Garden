---
title:  YAMLにtitleの項目を作った
tags: [2023/02/21]
aliases: []
---

```sh
for f in * ; do; gsed -e "2i title: ${f%.*}" ${f};done
```


[[やれたらやる]]