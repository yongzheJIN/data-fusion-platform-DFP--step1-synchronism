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

## 声明本人只是通过整合不同框架为大家提供一套适合异构数据的融合的框架，如有侵权请告知。
