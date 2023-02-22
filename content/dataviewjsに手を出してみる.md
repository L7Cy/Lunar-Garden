---
title: dataviewjsに手を出してみる
tags: []
aliases: []
estimation: 15
---
# Next Action
# Why
# How
# memo
```dataviewjs
let headers = ["tasks","estimation"]
let filteredTasks = dv.pages(outgoing(""))
	.where(t => !t.completed)
dv.table(
	headers,
	filteredTasks
		.map(p => [
			p.file.name,
			p["estimation"]
		])
)
```

```dataviewjs
let headers = ["tasks","estimation"]
dv.table(
	headers,
	dv.page("journals/2023-01-11").file.outlinks
	.map(p => [
		p,
			p.file.frontmatter.estimation
	])
)
```


```dataviewjs

dv.taskList(
	dv.page("journals/2023-01-11").file.tasks
	.where(t => !t.completed)
	,false
)
```
```
dataviewjs
const now = new Date();
dv.table(
	["tasks"],
	dv.pages("#will")
		.where(t => !t.checked)
		.map(t => [
				t.file.link
			]
		)
)
```
