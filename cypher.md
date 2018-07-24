Cypher
===================
Neo4j使用一种名为[Cypher](https://neo4j.com/developer/cypher/?ref=beginners-ebook)的图查询语言.Cypher的核心在于模式匹配，一个“模式/pattern”对应整个图数据库的一个子图。定义一个模式，在图数据库中匹配出符合条件的点和边，组成一个子图，再对这个子图进行各种操作。

## 1.Cypher的优势
和[SQL](https://en.wikipedia.org/wiki/SQL)不同，Cypher是简洁、易懂，且易于学习的，即使没有经过专门学习也可以很容易读懂Cypher语句的含义。举个例子，在无限漫画数据库中，查一部漫画的所有图片，我需要这样写：
```sql
select comic_image.id,comic_image.app_id,comic_image.comic_id,comic_image.created_at,comic_image.height,
comic_image.`order`,comic_image.source_image,comic_image.topic_source,comic_image.updated_at,
comic_image.url,comic_image.width from topic join comic on topic.id=comic.topic_id join comic_image on
comic.id=comic_image.comic_id where topic.title='生存日';
```