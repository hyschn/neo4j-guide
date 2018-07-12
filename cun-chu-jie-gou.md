# 存储结构

## 数据模型

Neo4j是图数据库的一种，使用图模型存储数据。有三大要素：Node,Relationship,Property

* Node即实体，数据的主要载体，用Property描述
* Relationship表示Node之间的关联关系
* Property用以增加Node和Relitionship的描述信息
* Node和Relationship都有“类别”的概念
* Relationship是有方向的

  ![](/assets/2.png)

### Node存储结构

Node只存储只存储它第一个Property和它的第一个Relationship的指针。Property比较简单，用一个单向链表来存储，遍历这个链表即可找到Node的所有Property\(Relationship的Property也是同样的存储结构\)。所以，对于同一类型Node，较多被访问的Property应该被放在链表的前面（在时间上先被添加到Node）。

![](/assets/3.png)

### Relationship存储结构

存储Relationship是一个双向链表。实际上，一个Relationship肯定是连接两个Node的，所以，它会存储2组指针，分别指向2个Node的Relationship。如下图所示，R1是A和B的Relationship，首先它会存储2个Node\(A&B\)，然后A组的"next"指向与A相连的下一个Relationship\(R2\)，B组的“next”指向与B相连的下一个Relationship。"prev"同理。  
  ![](/assets/4.png)

## graph.db存储文件

Neo4j的数据文件存放在$NEO4J\_HOME/data/databases/graph.db下面

### 存储 node 的文件

* 存储节点数据及其序列Id      
  neostore.nodestore.db:  存储节点数组，数组的下标即是该节点的ID  
  neostore.nodestore.db.id  ：存储最大的ID 及已经free的ID
* 存储节点label及其序列Id  
  neostore.nodestore.db.labels  ：存储节点label数组数据，数组的下标即是该节点label的ID  
  neostore.nodestore.db.labels.id

### 存储 relationship 的文件

* 存储关系数据及其序列Id  
  neostore.relationshipstore.db 存储关系 record 数组数据  
  neostore.relationshipstore.db.id

* 存储关系组数据及其序列Id  
  neostore.relationshipgroupstore.db  存储关系 group数组数据  
  neostore.relationshipgroupstore.db.id

* 存储关系类型及其序列Id  
  neostore.relationshiptypestore.db  存储关系类型数组数据  
  neostore.relationshiptypestore.db.id

* 存储关系类型的名称及其序列Id  
  neostore.relationshiptypestore.db.names存储关系类型 token 数组数据  
  neostore.relationshiptypestore.db.names.id

### 存储 label 的文件

* 存储label token数据及其序列Id  
  neostore.labeltokenstore.db  存储lable token 数组数据  
  neostore.labeltokenstore.db.id
* 存储label token名字数据及其序列Id  
  neostore.labeltokenstore.db.names  存储 label token 的 names 数据  
  neostore.labeltokenstore.db.names.id

### 存储 property 的文件

* 存储属性数据及其序列Id  
  neostore.propertystore.db  存储 property 数据  
  neostore.propertystore.db.id

* 存储属性数据中的数组类型数据及其序列Id  
  neostore.propertystore.db.arrays  存储 property \(key-value 结构\)的Value值是数组的数据。  
  neostore.propertystore.db.arrays.id

* 属性数据为长字符串类型的存储文件及其序列Id  
  neostore.propertystore.db.strings     存储 property \(key-value 结构\)的Value值是字符串的数据。  
  neostore.propertystore.db.strings.id

* 属性数据的索引数据文件及其序列Id  
  neostore.propertystore.db.index       存储 property \(key-value 结构\)的key 的索引数据。  
  neostore.propertystore.db.index.id

* 属性数据的键值数据存储文件及其序列Id  
  neostore.propertystore.db.index.keys     存储 property \(key-value 结构\)的key 的字符串值。  
  neostore.propertystore.db.index.keys.id

### 其他的文件

* 存储版本信息  
  neostore  
  neostore.id

* 存储 schema 数据  
  neostore.schemastore.db  
  neostore.schemastore.db.id

* 活动的逻辑日志  
  nioneo\_logical.log.active

* 记录当前活动的日志文件名称  
  active\_tx\_log



