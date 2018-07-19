neo4j guide
==========================    
##1.图数据库简介 
* ### <span color=red>What</span> is a Graph Database

图数据库的实现和应用都是基于图模型,但是学习图数据库并不需要理解复杂的[图论](https://en.wikipedia.org/wiki/Graph_theory) 知识.相较于关系型数据库(RDBMS),图的模型理解起来更加直观.
简单来说，一个图有两种元素组成:点(node)和边(relationship).一个点代表一个实体(例如在我们的无限漫画项目,node可以是一个topic、comic、comic_image或tag).边代表两个表之间的联系(例如comic表中的topic_id，comic_image表中的comic_id或者topic_tag表).

## 1.neo4j的地位

![](/assets/572343-20151031125529450-1021814796.jpg)
![](/assets/d6b9809e4baa4df088e875cb5c29289d.jpg)




![](/assets/timg.jpeg)

