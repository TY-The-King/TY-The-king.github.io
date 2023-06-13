---
title: oracleFunction
date: 2023-03-09 20:53:02
categories:
- 日常记录
tags: oracle函数日常记录
comment: false
excerpt: 在日常后端开发工作中，写SQL语句是家常便饭，SQL中有时可能需要加入一些业务的处理，因此使用到函数的频率还是挺高的，以下是我工作中使用频率较高的一些Oracle函数，自己整理出来记一下，也方便供大家参考使用。
---

## 前言：
> 在日常后端开发工作中，写SQL语句是家常便饭，SQL中有时可能需要加入一些业务的处理，因此使用到函数的频率还是挺高的，以下是我工作中使用频率较高的一些Oracle函数，自己整理出来记一下，也方便供大家参考使用。
>
### 一、函数
#### 1、NVL()
> NVL()函数用于判断一个字段的值是否为NULL，如NVL(A,B),若是A为NULL，则取B的值，若是不为NULL，则仍取A的值。
> ```sql
> --if A is null return B else return A
> select nvl(A,B) from dual; 
> ```

#### 2、NVL2()
> NVL2()函数的作用同样是判断字段值是否为NULL，但是Oracle在NVL()函数的基础上新增了一个参数，如NVL(A,B,C),若是A为NULL,则取C的值，不为NULL则是取B的值，不再取A的值，A作为一个判断条件。
>```sql
> --if A is null return C else return B
> select nvl2(A, B, C) from dual;
> ```

#### 3、REPLACE()
> REPLACE()函数的作用是替换字段中的字符串，如：字段A = "HelloWorld"，REPLACE(A,"World","ZhangSan")的执行结果为""HelloZhangSan。
> ```sql
> --return 'DBC'
> select replace('ABC', 'A', 'D') from dual; 
>
> ```

#### 4、LENGTH()
> LENGTH()函数作用是获取字段的长度，如：字段A =  "ABC"，LENGTH(A)的执行结果为"3"。
> ```sql
> --return 3
> select length('ABC') from dual;
> ```

#### 5、SUBSTR()
> SUBSTR()函数的作用是截取字符串，如：字段A="Hello"，SUBSTR(A,0,2)的执行结果为"He",其中A为被截取的字符串，“0”代表开始截取的位置下标（注意Oracle中的SUBSTR()函数，下标0和1是一样的，都是第一个字符开始截取，若是负数，则是从字符串尾部往前数），“2”代表截取的字符个数。
> ```sql
> --return 'AB'
> select subter('ABC', 0, 2) from dual;
> ```

#### 6、DECODE()
> DECODE()函数的作用是判断字段值是否为某个值，若为某个值则进行替换，可以对一对或多对值进行比较。
格式为：DECODE(A,S1,R1,S2,R2...,Defult)，其中A为目标字段，S1为比较字段，R1为结果字段，default为默认结果，把字段A与所有比较字段进行值的比较，若是相等，则输出结果字段，如果全部都不相等，则输出默认字段，若是没有指定默认字段，则默认输出NULL。
如：字段A = "ZhangSan"，DECODE(A,'ZhangSan','张三','LiSi','李四',NULL)的执行结果为："张三"。
> ```sql
> --if A is B return b else if C return c else return null
> select decode(A, 'B', 'b', 'C', 'c' default null) from dual;
> ```  

#### 7、TO_DATE()
> TO_DATE()函数为时间转换函数，格式为：TO_DATE('2022-06-30 00:00:00', 'YYYY-MM-DD HH24:MI:SS')，其中第一个参数为需要转换为时间的字符串，第二个参数为转换成的时间格式，可以自定义，需要注意的是在Oracle中，小时对应“HH24”,分对应“MI”。
> ```sql
> --return date type 2023-06-10 23:00:00 
> select to_date('2023-06-10 23:00:00', 'yyyy-mm-dd HH24:MI:SS') date from dual;
> ```

#### 8、TO_CHAR()
> TO_CHAR()函数为转换字符串，可以将时间转换为字符串，如：TO_CHAR(SYSDATE,'YYYYMMDD')，执行结果为“20220630”形式，可以按需要的格式将时间转换为字符串形式。
> ```sql
> --return string type 2023-06-10 23:00:00 
> select to_char(sysdate, 'yyyy-mm-dd HH24:MI:SS') date from dual;
> ```

#### 9、ROUND()
> ROUND()函数为计算精度函数，可以选择保留小数位数，如：字段A = '32.123456'，ROUND(A,3)的执行结果为“32.123”。
> ```sql
> --reruen 123.45
> select round(123.456, 2) from dual;
> ```

#### 10、CONCAT()
> CONCAT()函数的作用是字符串拼接，如：字段A = “Hellow”，B = “World”，CONCAT(A,B)的结果为“HelloWorld”。
> ```sql
> --return 'HelloWorld'
> select concat('Hello', 'World') from dual;
> ```

#### 11、ROW_NUMBER() OVER()
> ROW_NUMBER() OVER()函数的作用是按指定字段分组并排序，多用于取一组值中的最大或最小值。
> ```sql
> --return the table first record
> select * from (select id, row_number() over(order by id desc) rn from dual) where rn = 1;
> ```


#### 12、FULL OUTER JOIN
> FULL OUTER JOIN为两个表的并集，INNER JOIN则是交集。
> ```sql
> select * from A left outer join B;
> ```

#### 13、INSTR()
> INSTR(S1,S2,[N1,N2])表示获取指定一个子字符串S2在主字符串S1中的位置，N1表示从主串的那个位置开始查找，N2表示第几个子串出现的位置（N1,N2为可选参数，不填默认为1，从左到右查找，第一个出现的位置，N1为负数则是从右到左查找）
>```sql
> --return 1
>select instr('ABC', 'B') from dual;
>```

#### 14、CAST()
> 字符类型转换函数，可以将string转成integer类型
> ```sql
> --return int type 123
> select cast('123') from dual;
> ```

### 二、语法
```sql
--1、新增字段
alter table tableName add column columnName columnType;

--2、增加或修改字段注释
comment on column tableName.columnName is '字段注释';

--3、增加或修改表注释
comment on table tableName is '表注释';

--4、排序
--在排序中可使用case when语句为某个字段的值指定不同的排序，如下，就是将ID不为空的记录指定排序顺序为0，即不为空的记录在最前面，
--后续可以再按其他规则进行排序,如按创建时间进行排序
select * from dual order by case when id is not null then 0 else 1 end, createTime desc;
```