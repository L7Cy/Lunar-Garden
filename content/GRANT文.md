---
title:  GRANT文
tags: [2023/02/25]
aliases: []
---

- 1人または複数のユーザに表に関する特定の権限を付与するSQL文
```SQL
GRANT 権限名 ON オブジェクト名  
　　　　TO { ユーザ名 | ロール名 | PUBLIC }  
　　　　[ WITH GRANT OPTION ] ;
```

[[データ操作]]