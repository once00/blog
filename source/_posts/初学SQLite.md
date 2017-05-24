title: 初学SQLite
date: 2015-01-16 18:28:51
tags:
---
SQLite 是一个开源的嵌入式关系数据库，实现自包容、零配置、支持事务的SQL数据库引擎。 其特点是高度便携、使用方便、结构紧凑、高效、可靠。 与其他数据库管理系统不同，SQLite 的安装和运行非常简单，在大多数情况下 - 只要确保SQLite的二进制文件存在即可开始创建、连接和使用数据库。如果您正在寻找一个嵌入式数据库项目或解决方案，SQLite是绝对值得考虑。

##SQLite on Mac OS X如果你正在使用 Mac OS 雪豹或者更新版本的系统，那么系统上已经装有 SQLite 了。
####创建首个 SQLite 数据库现在你已经安装了 SQLite 数据库，接下来我们创建首个数据库。在命令行窗口中输入如下命令来创建一个名为  test.db 的数据库(如果数据库存在则进入数据库).
<!-- more -->```
$ sqlite3 test.db```
进入了sqlite3之后，会看到以下文字：
```
SQLite version 3.7.12 2012-04-03 19:43:07Enter ".help" for instructionsEnter SQL statements terminated with a ";"sqlite>```
* 这时如果使用.help可以取得求助，.quit则是离开
####创建表

```$ sqlite> create table mytable(id integer primary key, value text);
```
* 该表包含一个名为 id 的主键字段和一个名为 value 的文本字段。
####往表里中写入一些数据```
sqlite> insert into mytable(id, value) values(1, 'Micheal');sqlite> insert into mytable(id, value) values(2, 'Jenny');sqlite> insert into mytable(value) values('Francis');sqlite> insert into mytable(value) values('Kerk');
```
####查询数据
```
sqlite> select * from test;```
* 结果显示如下:
```
1|Micheal2|Jenny3|Francis4|Kerk```
**设置格式化查询结果:**

```
sqlite> .mode columnsqlite> .header onsqlite> select * from test;
```显示结果如下
```
id          value----------- -------------1           Micheal2           Jenny3           Francis4           Kerk
```
* .mode column 将设置为列显示模式，.header on将显示列名####修改表
* 修改表结构，增加列
```
sqlite> alter table mytable add column email text not null '' collate nocase;;```
####创建视图
```
sqlite> create view nameview as select * from mytable;```
####创建索引
```
sqlite> create index test_idx on mytable(value);```
####一些有用的 SQLite 命令(命令最后不用加分号)
* 显示表结构
```
$　sqlite> .schema [tablename]```
* 获取所有表和视图

```
$ sqlite> .schema [tablename]
```
* 获取指定表的索引列表```
$ sqlite > .indices [table ]```
* 导出数据库到 SQL 文件
```
$ sqlite > .output [filename ] $ sqlite > .dump $ sqlite > .output stdout
```
* 从 SQL 文件导入数据库
```
$ sqlite > .read [filename ]
```
* 格式化输出数据到 CSV 格式
```
$ sqlite >.output [filename.csv ] 
$ sqlite >.separator
$ sqlite > select * from test; 
$ sqlite >.output stdout
```
* 从 CSV 文件导入数据到表中
```
$ sqlite >create table newtable ( id integer primary key, value text ); 
$ sqlite >.import [filename.csv ] newtable
```
* 备份数据库
```$ sqlite3 mytable.db .dump > backup.sql```
* 恢复数据库
```$ sqlite3 mytable.db < backup.sql
```