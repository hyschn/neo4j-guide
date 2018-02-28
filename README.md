# neo4j-guide
* ## 下载 
    https://neo4j.com/download/
* ## 文档 
    https://neo4j.com/docs/
* ## 安装
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
![](/assets/20180104120040176.jpg)


