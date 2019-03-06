# 表格信息查询

[查询表格基础信息](#查询表格基础信息)

[查询列信息](#查询列信息)

## 查询表格基础信息

查询指定用户所管理的表格以及表格注释

```sql
select tab.table_name, comm.comments
  from dba_tables tab, user_tab_comments comm
 where tab.table_name = comm.table_name
   and tab.owner = upper('OWNER')
```

## 查询列信息

查询指定表格的列名、数据类型以及列注释

```sql
select a.column_name, b.data_type, comments
  from user_tab_columns b, user_col_comments a
 where a.column_name = b.column_name
   and a.table_name = b.table_name
   and a.table_name = upper('TABLE_NAME')
```