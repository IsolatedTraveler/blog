# 实用操作

[数据恢复](#数据恢复)
[数据锁死](#数据锁死)

## 数据恢复

利用Oracle本身自带的快照功能实现短时间内的数据恢复

```sql
select *
  from TABLE_NAME as of timestamp to_timestamp('2019-03-05 12:28:00', 'YYYY-MM-DD HH24:MI:SS')
 where ...;
```

## 数据锁死

```sql
-- 查询当前被锁数据sid和serial#
select sess.SID,
       sess.SERIAL#,
       lo.ORACLE_USERNAME,
       lo.OS_USER_NAME,
       ao.object_name,
       lo.LOCKED_MODE
  from v$locked_object lo, dba_objects ao, v$session sess
 where ao.object_id = lo.OBJECT_ID
   and lo.SESSION_ID = sess.SID;
-- 通过sid以及serial干掉系统进程解除锁死状态
alter system kill session 'sid,SERIAL#'
```