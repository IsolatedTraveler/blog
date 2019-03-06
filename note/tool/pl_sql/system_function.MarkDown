# 系统函数

## 对空值附加默认值

```sql
	select nvl(null,'a') as name from dual; -- a
```

## 条件判断

```sql
	select decode($col,val1,printVal1,val2,printVal2...valn,printValn,printValn+1) from dual;
	-- eg
		select decode('a','b','b1','c','c1','d1') from dual; -- 'd1'
		select decode('b','b','b1','c','c1','d1') from dual; -- 'b1'
	--
```

## 字符串分割

1. REGEXP_SUBSTR(String, pattern, position, occurrence, modifier)

  __srcstr     ：需要进行正则处理的字符串
  __pattern    ：进行匹配的正则表达式
  __position   ：起始位置，从第几个字符开始正则表达式匹配（默认为1）
  __occurrence ：标识第几个匹配组，默认为1
  __modifier   ：模式（'i'不区分大小写进行检索；'c'区分大小写进行检索。默认为'c'。）

```sql
	select REGEXP_SUBSTR($col,reg,start,index) from table;
	-- eg
		select REGEXP_SUBSTR('1-asd','[^-]+',1,2) from dual; -- 'asd'
		select REGEXP_SUBSTR('1-asd-cd','[^-]+',1,3) from dual; -- 'cd'
		select REGEXP_SUBSTR('1-asd-cd','[^-]+',3,2) from dual; -- 'cd'
	-- 
```

## 日期处理函数

```sql
	-- date to char
	select to_char(sysdate,'yyyy-mm-dd hh:mm:ss') from dual;
```