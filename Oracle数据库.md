

## 数据库

**1.数据库的基本概念**

> DataBase简称DB，用来存储和管理数据的仓库

- 数据库的特点

  ```
  1.持久化储存数据的，其实是一个文件系统
  2.方便存储和管理数据
  3.使用了统一的方式操作数据库--SQL
  ```

**2.Mysql的学习**

> 1.Mysql安装

**3.SQL**



#### Oracle学习

**创建表空间**

```shell
create tablespace waterboss		//起重waterboss为表空间名
datafile 'c:\waterboss.dbf'		//''中存放的内容是表空间的存放位置
size 100m		//定义表空间的大小'm'表示兆
autoextend on		//当表空间中存放的内容超过制定的大小则自动扩展
next 10m		//每次自动扩展10
```

**创建用户**

```shell
creat user wateruser		//wateruser为创建的用户名
identified by josengit		//josengit为用户名所对应的密码
default tablespace waterboss		//创建的用户默认的表空间是waterboss
```

**用户赋权**

```shell
grant dba to wateruser		//给wateruser赋予权限，dba的权限非常高
```



> 表的创建、修改与删除

**创建表**

```shell
create table 表名称（
字段名 类型（长度）primary key,
字段名 类型（长度），
...
）
```

**修改表**

```shell
alter table 表名称 add(列名1 类型 [deafault 默认值]，列名2 类型...)		//增加字段语法
alter table 表名称 modify(列名1 类型 [deafault 默认值]，列名2 类型...)		//修改字段语法
alter table 表名称 rename column 原列名 to 新列名		//修改字段名语法
```









**数据类型**

- 字符型

  ```shell
  char:固定长度的字符类型，最多可以存储2000字节
  varchar2:可变长度的字符类型，最多可以存储4000字节
  long:大文本类型，最大可以存储2G
  ```

- 数据型

  ```shell
  number:数值类型		  //number（5）最大可以表示99999
  					//number（5，2）最大可以表示999.99
  ```

- 日期型

```shell
date:日期时间型，精确到秒
timestamp：精确到秒的小数点后9位
```

- 二进制型（大数据类型）

```shell
clob:存储字符，最大可存放4G
blob:存储图像、声音、视频等二进制数据，最多可存放4G
```



**创建业主表**

```shell 
create table t_owners
(
id number primary key,
name varchar2(30),
addressid number,
housenumber varchar2(30),
watermeter varchar2(30),
adddate date,
ownertypeid number
);
```

**删除表**

```shell
drop table 表名称		//删除整个表
alter table 表名称 drop column 列名		//删除某一列（一个字段）
alter table 表名称 drop（列名1，列名2...）		//删除多个字段
```



> 数据增删改

**插入数据**

```
insert into 表名[(列名1，列名2，...)]values(值1，值2，...)
```

**修改数据**

```
update 表名 set 列名1=值1，列名2=值2，...where 修改条件;
```

**删除数据**

```
delete from 表名 where 删除条件;		//delete删除不完全，可以rollback回滚
truncate table 表名称		//彻底删除 
```

