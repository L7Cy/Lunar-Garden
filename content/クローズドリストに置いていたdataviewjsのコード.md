---
title: クローズドリストに置いていたdataviewjsのコード
tags: [2023/02/07]
aliases: []
---

```dataviewjs
let headers = ["タスク","見積","終わり"]
let thisLinks = "[[" + dv.current().file.path + "]]"
let outlinks = dv.pages("outgoing(" + thisLinks + ")")
const now = dv.func.date('now')
let sum = 0
dv.table(
	headers,
	outlinks
		.map(p => [
			p.file.link,
			p.estimation,
			DateTime.now().plus(sum += luxon.Duration.fromMillis(p.estimation*1000*60)).toFormat('HH:mm')
		])
)
```
