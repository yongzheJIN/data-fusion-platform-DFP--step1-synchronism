# canal-realtime_catch_data-
本文档针对的是windows系统。（linux系统也是可以，如果有需要的朋友可以留言）
实例代码会在后续补上
利用canal server和canal adopter实现mysql数据库的实时同步
# 简介（description）
本文档讲解的是通过使用canal-server和canal deployer实现了mysql到mysql的实时映射同步，原理是利用mysql的binlog的书写，来记录文档的操作，canal模拟为slave来记载mysql的操作，然后通过adopter来完成数据的同步。
## 1：开启mysql的binlog
找到mysql的配置文件my.ini配置
log_bin = mysql_bin
binlog-format = Row
#### row是一种特殊格式，这里千万不要写成mixed和statement，具体原因可去查binlog模式的不同
## 2: 配置canal_server
canal中有两个文件是需要人为去配置的，这里我们针对canal自带的adopter来配置（也支持自己编写java程序以及使用kafka消费信息【依赖Kafka的ETL消费进程会在后期推出】）</br>
conf/canal.properties </br>
![image](https://user-images.githubusercontent.com/52804241/127943049-63b0f70f-b44b-4d12-970b-754331f13a1a.png)</br>
配置消费方式 </br>
conf/example/instance.prperties</br>
![image](https://user-images.githubusercontent.com/52804241/127943116-32e1cdc0-0100-4d2f-949a-7210954e5334.png)</br>
配置账户密码</br>

##3:配置canal_adopter(消息消费端)</br>
conf/application.yml</br>
conf/rdb/test.yml</br>
这里的内容有点复杂，可以下载我的代码自己看一下这两个文档，不懂的可以后续询问</br>

<hr>
这里只讲解简单的同步配置，如果有其他需求请告知我会持续更新。
## 声明本人只是通过整合不同框架为大家提供一套适合异构数据的融合的框架，如有侵权请告知。
