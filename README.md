# GeeORM
对象关系映射（Object Relational Mapping，简称ORM）是通过使用描述对象和数据库之间映射的元数据，将面向对象语言程序中的对象自动持久化到关系数据库中。
ORM 框架相当于对象和数据库中间的一个桥梁，借助 ORM 可以避免写繁琐的 SQL 语言，仅仅通过操作具体的对象，就能够完成对关系型数据库的操作。

GeeORM目前支持的特性有：
表的创建、删除、迁移。
记录的增删查改，查询条件的链式操作。
单一主键的设置(primary key)。
钩子(在创建/更新/删除/查找之前或之后)
事务(transaction)。

本项目是对geektutu的"7天用Go从零实现ORM框架GeeORM"教程的复现.
通过该项目的练习可以学习到对SQL语句的封装以及如何使用reflect和interface{}实现多态的知识.

reference:
github.com/geektutu/7days-golang/tree/master/gee-orm
