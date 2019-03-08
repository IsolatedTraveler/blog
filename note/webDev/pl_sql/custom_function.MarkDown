# 自定义常用函数

[如何自定义函数](#如何自定义函数)

[常用函数](#常用函数)

## 如何自定义函数

## 常用函数

[时间格式化](#时间格式化)

### 时间格式化

to_char(sysdate,format)

sysdate 时间

format  时间格式 (y:年 | m:月 | d:天 | hh:12小时制 | hh24:24小时制 | mi:分钟 | ss:秒)

```sql
CREATE FUNCTION dts(v_datetime IN DATE, f_datetime IN VARCHAR := '1') RETURN VARCHAR2 IS
  /*-------------------------------
  函数名： 日期转yyyy-mm-dd hh24:mi:ss字符串
    功能： select std(sysdate) as datestr from dual
    参数： v_datetime 时间
          f_datetime:0 日期时间格式，1 日期格式 2 时间 || 自定义格式
  --------------------------------*/
BEGIN
  IF f_datetime = '0' THEN
    RETURN to_char(v_datetime, 'yyyy-mm-dd hh24:mi:ss');
  ELSIF f_datetime = '1' THEN
    RETURN to_char(v_datetime, 'yyyy-mm-dd');
  ELSIF f_datetime = '2' THEN
    RETURN to_char(v_datetime, 'hh24:mi:ss');
  ELSE
    RETURN to_char(v_datetime, f_datetime);
  END IF;
EXCEPTION
  WHEN OTHERS THEN
    RETURN NULL;
END dts;
```