# 介绍
## 下载 
    https://neo4j.com/download/
## 文档 
    https://neo4j.com/docs/
## 安装
(安装方式有很多种，这里仅介绍其一)
    解压
```
cd /neo4j-community-3.2.2/bin
(sudo) ./neo4j start 
./neo4j stop
./neo4j status
./cypher-shell	(进入命令行)
username:neo4j
password:neo4j
(退出)	:exit
控制台http://127.0.0.1:7474（在此修改初始密码）
允许远程连接：vim /neo4j-community-3.2.2/conf/neo4j.conf
dbms.connectors![.default_listen_address=0.0.0.0(去掉注释)
```

## 优势
    * 自带一套易于学习的查询语言（名为Cypher）
    * 不使用schema，因此可以满足你的任何形式的需求
    * 与关系型数据库相比，对于高度关联的数据（图形数据）的查询快速要快上许多
    * 它的实体与关系结构非常自然地切合人类的直观感受
    * 支持兼容ACID的事务操作
    * 提供了一个高可用性模型，以支持大规模数据量的查询，支持备份、数据局部性以及冗余
    * 提供了一个可视化的查询控制台，你不会对它感到厌倦的
![](/assets/20180104120040176.jpg)


