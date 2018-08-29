<!-- GFM-TOC -->
* [一、一些约定](#一一些约定)
* [二、更新已存在的表](#二更新已存在的表)
* [三、将事务处理写到数据库](#三将事务处理写到数据库)
* [四、创建索引](#四创建索引)
* [五、创建索引过程](#五创建索引过程)
* [六、创建新的数据库表](#六创建新的数据库表)
* [七、向系统中添加新的用户账户](#七向系统中添加新的用户账户)
* [八、创建一个或多个表上的新视图](#八创建一个或多个表上的新视图)
* [九、删除一行或多行](#九、删除一行或多行)
* [十、永远的删除数据库对象（表/视图/索引等）](#十永远的删除数据库对象（表/视图/索引等）)
* [十一、给表增加一行](#十一给表增加一行)
* [十二、撤销一个事务处理块](#十二撤销一个事务处理块)
* [十三、用rollback语句设立保留点](#十三用rollback语句设立保留点)
* [十四、从一个或多个表（视图）中检索数据](#十四从一个或多个表（视图）中检索数据)
* [十五、start transaction表示一个新的事务处理块的开始](#十五start transaction表示一个新的事务处理块的开始)
* [十六、update更新一个表中一行或多行](#十六update更新一个表中一行或多行)
<!-- GFM-TOC -->

# 一、一些约定
NULL|NOT NULL表示或者给出null或者给出not null;
[like this]包含在方括号中的关键字或子句是可选的
# 二、更新已存在的表
```java
alter table tablename(
          add column datatype [null|not null] [constraints],
          change column datatype [null|not null][constraints],
          drop column,
          ....
      );
```
# 三、将事务处理写到数据库
comomit;
# 四、创建索引
```java
create index indexname on tablename (column [asc|desc],...);在一个或多个列上创建索引
```
# 五、创建索引过程
```java
create procedure procedurename([parameters])
begin
...
end;
```
# 六、创建新的数据库表
```java
create table tablename(
       column datatype [null|not null] [constraints],
       column datatype [null|not null] [constraints],
       ...
     );
```
# 七、向系统中添加新的用户账户
```java
create user username[@hostname][idectified by [password] 'password'];
```
# 八、创建一个或多个表上的新视图
```java
create [or replace] view viewname as select ...;
```
# 九、删除一行或多行
```java
delete from tablename [where...];
```
# 十、永远的删除数据库对象（表/视图/索引等）
```java
drop datebase|index|procedure|talbe|trigger|user|view itemname;
```
# 十一、给表增加一行
```java
insert into tablename [(columns,...)] values(values,...];
```
# 十二、撤销一个事务处理块
```java
rollback [to savepointname];
```
# 十三、用rollback语句设立保留点
savepoint sp1;
# 十四、从一个或多个表（视图）中检索数据
```java
select columnname,...
from talbename,...
[where ...][union...][group by..][having...][order by..]
```
# 十五、start transaction表示一个新的事务处理块的开始
start transaction;
# 十六、update更新一个表中一行或多行
```java
update talbename set columnname=value,..[where ...
```
(误删了几行）
