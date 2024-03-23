# GeeORM
对象关系映射（Object Relational Mapping，简称ORM）是通过使用描述对象和数据库之间映射的元数据，将面向对象语言程序中的对象自动持久化到关系数据库中。
ORM 框架相当于对象和数据库中间的一个桥梁，借助 ORM 可以避免写繁琐的 SQL 语言，仅仅通过操作具体的对象，就能够完成对关系型数据库的操作。

GeeORM目前支持的特性有：
表的创建、删除、迁移。
记录的增删查改，查询条件的链式操作。
单一主键的设置(primary key)。
钩子(在创建/更新/删除/查找之前或之后)
事务(transaction)。

各模块及其功能：
 * clause包 ：子句(clause) 构成。
    * 1)clause.go :负责生成特定的子句并拼接各个子句。
    * 2)generator.go :实现各个子句的生成规则。
 * dialect包
    * 1)dialect.go :将Go 语言的类型映射为数据库中的类型。隔离不同数据库之间的差异，便于扩展
    * 2)sqlite3.go :注册新数据库，实现Dialect接口中的方法：DataTypeOf，TableExistSQL。
 * log包 :支持日志分级（Info、Error、Disabled）。不同层级日志显示时使用不同的颜色区分。显示打印日志代码对应的文件名和行号。
 * schema包 :对象(object)和表(table)的转换。实现 Parse 函数，将任意的对象解析为 Schema 实例。将对象各字段的value平铺，以便传入sql语句
 * session包 :用于实现与数据库的交互。
    * 1)hooks.go :实现钩子
    * 2)raw.go :包含Session结构体，可调用原生 SQL 语句与数据库交互，为record.go提供Exec，QueryRow等执行函数
    * 3)record.go :实现记录增删查改相关的代码。根据查找结果构造对象。链式调用子句，以执行完整的 SQL 语句。
    * 4)table.go :放置操作数据库表相关的代码。Model调用Parse生成表，以便执行表的增删
    * 5)transaction.go :支持事务
 * geeorm.go :包含GeeORM 与用户交互的入口---Engine，负责交互前的准备工作（比如连接/测试数据库，创建session），交互后的收尾工作（关闭连接）。数据库表的Migrate

本项目是对geektutu的"7天用Go从零实现ORM框架GeeORM"教程的复现.
通过该项目的练习可以学习到对SQL语句的封装以及如何使用reflect和interface{}实现多态的知识.

reference:
github.com/geektutu/7days-golang/tree/master/gee-orm
