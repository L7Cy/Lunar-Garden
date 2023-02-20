---
title: templaterのテンプレートのタグをタグから除外する方法
tags: [2023/02/14]
aliases: []
---

以下のように，ハイフンを<%%>で囲んでしまえばいい
```
<%"---"%>
tags: [<% tp.file.creation_date("YYYY/MM/DD") %>]
aliases: [<% tp.file.cursor() %>]
<%"---"%>
```

[[obsidianのプラグイン]]
