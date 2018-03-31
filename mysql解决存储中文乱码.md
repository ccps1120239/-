1、首先打开cmd，登陆MySQL。
输入：show variables like 'character%';

	
	+--------------------------+----------------------------+
	
	| Variable_name | Value |
	
	+--------------------------+----------------------------+
	
	| character_set_client | latin1 |
	
	| character_set_connection | latin1 |
	
	| character_set_database |latin1 |
	
	| character_set_filesystem | binary |
	
	| character_set_results |latin1 |
	
	| character_set_server | latin1 |
	
	| character_set_system |utf8 |
	
	| character_sets_dir | /usr/share/mysql/charsets/ |
	
	+--------------------------+----------------------------+

从以上信息可知数据库的编码为latin1，需要修改为gbk或者是utf8（先以utf8为例）；

其中，`character_set_client`为客户端编码方式；

`character_set_connection`为建立连接使用的编码；

`character_set_database`数据库的编码；

`character_set_results`结果集的编码；

`character_set_server`数据库服务器的编码；

 

现将这几种编码方式全部改为"utf-8":

本文仅仅介绍一种最根本的方法：

（1）中止MySQL服务

（2）在MySQL的安装目录下找到`my.ini`，如果没有就把`my-medium.ini`复制为一个`my.ini`即可

（3）打开`my.ini`以后，在`[client]`和`[mysqld]`下面均加上`default-character-set=utf8`，保存并关闭

（4）启动MySQL服务并查询此时编码方式：

 `mysql> show variables like 'character%';` #执行编码显示

	+--------------------------+----------------------------+
	
	| Variable_name | Value |
	
	+--------------------------+----------------------------+
	
	| character_set_client |utf8 |
	
	| character_set_connection | utf8|
	
	| character_set_database | utf8 |
	
	| character_set_filesystem | binary |
	
	| character_set_results |utf8 |
	
	| character_set_server |utf8 |
	
	| character_set_system | utf8 |
	
	| character_sets_dir | /usr/share/mysql/charsets/ |
	
当这八种编码方式编程utf-8的时候，此时mysql数据库即可插入中文。

