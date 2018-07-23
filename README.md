neo4j guide
==========================    
##1.图数据库简介 
* ### <span color=red>What</span> Is a Graph Database

图数据库的实现和应用都是基于图模型,但是学习图数据库并不需要理解复杂的[图论](https://en.wikipedia.org/wiki/Graph_theory) 知识.相较于关系型数据库(RDBMS),图的模型理解起来更加直观.   

简单来说，一个图有两种元素组成:点(node)和边(relationship).一个点代表一个实体(例如在我们的无限漫画项目,node可以是一个topic、comic、comic_image或tag).边代表两个表之间的联系(例如comic表中的topic_id，comic_image表中的comic_id或者topic_tag表).

* ### <span color=red>Why</span> You Should Care about Graph Databases

* ####充分性
 [关系型数据库](https://en.wikipedia.org/wiki/Relational_database_management_system)最初被设计出来是为了处理表格形式的扁平数据，而且它们([MySQL](https://en.wikipedia.org/wiki/MySQL),[Oracle](https://en.wikipedia.org/wiki/Oracle),[Microsoft SQL Server](https://en.wikipedia.org/wiki/Microsoft_SQL_Server)……)目前在这方面的表现依然非常出色.尴尬的是，***关系***型数据库却不擅长处理数据之间的***“关系”***，特别是当这种关系是一种“多对多”的关系的时候(通常的做法是建立一个额外的关联表).而*relationship*作为图数据中的第一要素,恰恰解决了这一痛点.
 
* ####必要性
我们正处于一个“大数据”时代，而且我们的数据量一定会持续增长，但是和数据本身相比，数据之间的关联关系增长的要更快.在传统的数据库系统中，随着关系数量以及关联的深度的增加，关系查询的效率会变得难以接受.与之相比，图数据库的性能却能保持在比较乐观的范围内.![](/assets/20180723150814.png)

* ### <span color=red>How</span> Graph Databases Work
* ####Graph Storage
一些图数据库专门设计一种“原生”的图式结构来存储和分析图形式的数据，还有一些则使用关系型数据库或[面向对象数据库](https://en.wikipedia.org/wiki/Object_database)来代替。通常，非原生存储比原生存储的图数据库处理速度要慢。

* ####Graph Processing Engine
因为图数据库在存储的时候，互相关联的店就是通过引用直接指向与之关联的数据，所以，使用原生的图处理方式是处理图式数据最有效的方法。另外，也有一些图数据库使用其他方式来处理增删改查的操作。
![](/assets/20180723151742.png)

## 2.neo4j的地位

首先，图数据库属于[NoSQL](https://en.wikipedia.org/wiki/NoSQL)的一种，但是它又和其他的NoSQL有很大的不同。简单来说，图数据库和其他NoSQL的差别比其他NoSQL和关系型数据库的差别还要大。Neo4j作为目前最流行的图数据库之一，其社区版可以免费使用，并且开源，近几年在国内的关注度也在逐渐提高。

![](/assets/572343-20151031125529450-1021814796.jpg)

![](/assets/timg.jpeg)

