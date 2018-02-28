* ## 数据模型
    Neo4j是图数据库的一种，使用图模型存储数据。有三大要素：Node,Relationship,Property
    * Node即实体，数据的主要载体，用Property描述
    * Relationship表示Node之间的关联关系
    * Property用以增加Node和Relitionship的描述信息
    * Node和Relationship都有“类别”的概念
    * Relationship是有方向的
    ![](/assets/2.png)
* ### Node存储结构
    Node只存储只存储它第一个Property和它的第一个Relationship的指针。Property比较简单，用一个单向链表来存储，遍历这个链表即可找到Node的所有Property(Relationship的Property也是同样的存储结构)。所以，对于同一类型Node，较多被访问的Property应该被放在链表的前面（在时间上先被添加到Node）。
    ![](/assets/3.png)
    
* ### Relationship存储结构
    存储Relationship是一个双向链表。实际上，一个Relationship肯定是连接两个Node的，所以，它会存储2组指针，分别指向2个Node的Relationship。如下图所示，R1是A和B的Relationship，首先它会存储2个Node(A&B)，然后A组的"next"指向与A相连的下一个Relationship(R2)，B组的“next”指向与B相连的下一个Relationship。"prev"同理。
    ![](/assets/4.png)

    
