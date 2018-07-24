Cypher
===================
Neo4j使用一种名为[Cypher](https://neo4j.com/developer/cypher/?ref=beginners-ebook)的图查询语言.Cypher的核心在于模式匹配，一个“模式/pattern”对应整个图数据库的一个子图。定义一个模式，在图数据库中匹配出符合条件的点和边，组成一个子图，再对这个子图进行各种操作。

## 1.Cypher的优势
和[SQL](https://en.wikipedia.org/wiki/SQL)不同，Cypher是简洁、易懂，且易于学习的，即使没有经过专门学习也可以很容易读懂Cypher语句的含义。举个例子，在无限漫画数据库中，查一部漫画的所有图片，我需要这样写：
```sql
select comic_image.id,comic_image.app_id,comic_image.comic_id,comic_image.created_at,comic_image.height,
comic_image.`order`,comic_image.source_image,comic_image.topic_source,comic_image.updated_at,
comic_image.url,comic_image.width from topic 
join comic on topic.id=comic.topic_id 
join comic_image on comic.id=comic_image.comic_id 
where topic.title='生存日';
```
但是在Neo4j中，只需要这样
```sql
match (topic:Topic{title:"生存日"})-[:Contains]->(comic:Comic)-[:Contains]->(comicImage:ComicImage) 
return comicImage;
```
而且，两者查询消耗的时间差距也很明显。

|SQL|Cypher|
|- | :-: |
|![](/assets/20180724171744.png) | ![](/assets/20180724171537.png)|

## 2.基本语法
#### MATCH
match是最常用的一个子句。
Cypher用一对小括号("(",")")来构造“点”，下面这些写法都是正确的

```sql
(topic:Topic{title:"生存日"})
(:Topic)
(topic)
```
使用一对短横线("-")和大于号(">")或小于号("< ")来构造“边”,箭头代表边的方向。在两条短横线中间可以用中括号来包围边的类型，类型名下面加上冒号，e.g.

```sql
-[:Contains]->
-[c:Contains]->
-->
```

点和边的属性用一对大括号包围的键值对来表示，e.g.

```sql
(topic:Topic{title:"生存日",used_source:2})
```

#### RETUEN
return制定匹配的模式中，那些表达式，点，边或属性需要被返回，在上面的例子中，我们return的是comicImage点的信息，当然也可以return  comicImage.url,count(comicImage.id)……

#### WHERE
后面跟用来过滤模式匹配的条件。

#### CREATE
用来创建点或边

#### MERGE
根据match提供的模式，如果库中存在的点或边则直接使用，不存在则创建，最终需要满足模式

#### DELETE/REMOVE
删除点、边、属性

#### SET
给点或边设置属性值或标签

#### ORDER BY
对return的结果进行排序

#### SKIP LIMIT
返回结果时跳过前面一定行数以及限制返回的总行数

#### UNION
合并多个查询的结果

#### WITH
链接前一个查询的结果和后一个查询，类似于Unix中的管道。例如我们在统计“至少一个章节只有一张图片的作品”的时候，可以这样查询：

```sql
match (topic:Topic)-[:Contains]->(comic:Comic)-[:Contains]->(comicImage:ComicImage)
where topic.used_source=comicImage.topic_source and topic.used_source=1 
with count(distinct comic) as comicCount, count(distinct comicImage) as imageCount,topic as topic,comic as comic
where comicCount>=imageCount 
return distinct topic.title,count(comic.id),comicCount,imageCount 
order by topic.title asc
```

上面这个查询和使用SQL来查并没有什么优化的地方，因为Cypher没有*having*和*group by*，所以在分组统计的时候会比较麻烦。在cypher中不用显式的写group by分组字段，由解释器自动决定：即未加聚合函数的字段自动决定为分组字段.例如在查询topic的时候想根据来源统计，可以return topic.used_source,count(id)

  


