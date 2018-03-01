
--------------------------------------------------------
# 1.将解压版的mysql文件解压

# 2.解压成功，目前新版本的5.7是没有.ini配置文件和data文件夹的，关于data文件夹后续会说明。

#3.在安装目录下新建my.ini配置文件，添加如下内容，并且保存的编码格式必须要是ANSI。
- 如何保存ANSI格式：新建文本文档，将其名字修改为my.ini，添加好内容后，点击左上角文件，点另存为，即可在下方看见编码格式。
- (记得目录要修改成你的目录地址)：

		[mysql]  
		# 设置mysql客户端默认字符集  
		default-character-set=utf8  
		[mysqld]  
		#设置3306端口  
		port = 3306  
		# 设置mysql的安装目录  
		basedir=F:\developer\MySQL5.7.20\mysql-5.7.20-winx64  
		# 设置mysql数据库的数据的存放目录  
		datadir=F:\developer\MySQL5.7.20\mysql-5.7.20-winx64\data  
		# 允许最大连接数  
		max_connections=200  
		# 服务端使用的字符集默认为8比特编码的latin1字符集  
		character-set-server=utf8  
		# 创建新表时将使用的默认存储引擎  
		default-storage-engine=INNODB
	
# 4.以管理员身份运行CMD命令，并进入MySQL安装目录的bin目录下。(注意！必须以管理员身份运行，且必须是bin目录下，否则失败！)

# 5.当以管理员身份进入bin目录后，输入：mysqld install，当跳出“Service successfully installed”后代表安装成功。

# 6.接着再输入：mysqld --initialize-insecure --user=mysql
# (上述步骤是设置用户名为root，密码为空，并且会在根目录下创建data文件夹，并且如果没有这个命令，待会启动mysql服务会失败。)

# 7.完成上述步骤后，输入：net start mysql来启动服务，启动成功后会有字样显示，如果想要停止，就输入：net stop mysql。

# 8.此时，基本上已经完成mysql的所有配置，但是当你关闭CMD再次打开，再次进入的时候还要必须以管理员身份运行才可以登陆，这样很不方便，因此，我们需要配置一下系统的环境变量。
		右键我的电脑----属性---高级系统设置----高级---环境变量
		新建系统变量，变量名：MYSQL_HOME
		变量值：你mysql安装的根目录(如：F:\developer\MySQL5.7.20\mysql-5.7.20-winx64)
		找到path变量，点击编辑，追加：%MYSQL_HOME%\bin;    
		如果结尾部位没有;号，必须先添加分号，而且符号必须是英文模式下的分号！！！

# 9.重新运行cmd后，输入：mysql -u root -p 回车，再回车，登陆成功！

# 10，登陆成功后，因为首次登陆手动配置的mysql是不需要密码的，所以我们需要设置一个初始密码，
		输入：set password for root@localhost = password('你的密码');
		而mysql设置密码的指令有很多种，根据你的选择，需要其他的可以自行百度。
		当提示ok后，输入exit或quit退出mysql，并重新输入登陆命令，再输入密码即可！
