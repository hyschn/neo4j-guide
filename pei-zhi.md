#配置

## 文件目录
<span color=#0000ff>.</span>  
├── <span color=#0000ff>bin</span>  
├── <span color=#0000ff>certificates</span>  
├── <span color=#0000ff>conf</span>  
├── <span color=#0000ff>data</span>  
├── <span color=#0000ff>import</span>  
├── <span color=#0000ff>lib</span>  
├── LICENSES.txt  
├── LICENSE.txt  
├── <span color=#0000ff>logs</span>  
├── NOTICE.txt  
├── <span color=#0000ff>plugins</span>  
├── README.txt  
├── <span color=#0000ff>run</span>  
└── UPGRADE.txt  

### 日志文件
日志文件位于 &lt;neo4j-home>/logs

|文件| 描述|
|- | :-: |
|neo4j.log | 最主要的日志，记录Neo4j的主要信息|
|debug.log | 记录对debugging有用的信息 |
|http.log | http请求日志 |
|gc.log| 垃圾回收日志 |
|query.log| 查询时间超过指定阈值的时候会记录的日志(企业版独有) |
|security.log|加密活动的日志(企业版独有)|
|service-error.log|运行Windows service的日志(Windows版独有)|

### 配置文件
Neo4j的主目录和配置文件目录可以在环境变量配置，变量名分别是<span color=red>NEO4J_HOME</span>、<span color=red>NEO4J_CONF</span>.在没有配置环境变量的情况下，Neo4j的主目录默认是*bin*目录的父级目录，配置文件目录是${NEO4J_HOME}/conf.

### 权限
运行Neo4j的用户需要以下权限：
读权限
    * conf
    * import
    * bin
    * lib
    * plugins
    
读写权限
    * data
    * logs
    * metrics
    
执行权限
    * bin