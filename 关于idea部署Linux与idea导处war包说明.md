##idea导出war包：
- 点击此按钮：

![](https://i.imgur.com/QAlhpse.png)

![](https://i.imgur.com/srq3oqE.png)

- `Type`：必须是Archive的，不然就不是war包
- `Name`：可以自己更换取的名字
- `Output Directory`：这是war包的输出路径
- 然后点击ok。

- 然后我们来到这里：

![](https://i.imgur.com/b81xSsn.png)

- 点击`Bulid`--->`Bulid Artifacts`：

![](https://i.imgur.com/FWjbink.png)

- 点击`bulid`，war包就会生成在你刚刚在`Output Directory`内输入目录下了

![](https://i.imgur.com/n9A9D2h.png)



----------


##war包部署到Linux环境下运行
- 按照上述步骤，我们完成了war包的导出，接下来我们需要部署到Linux上运行
- 前提：
	- Linux必须安装有与你本地一致的jdk版本，如：windows1.8，那么你Linux也要1.8；
	- 如果你本地使用的是servlet规范是3.1的，那么你必须要使用tomcat8版本才可以，否则抛出异常；
	- 本地Windows的tomcat版本如果能保持与Linux上的tomcat版本一致是最好的；
	- 如果你的项目有数据库需要安装数据库并导入sql脚本文件；
- 连接远程工具：我这里以xshell为例子；

- 步骤：
	- 连接你的远程Linux；
	- cd到你的tomcat安装目录下的bin目录内，如：cd /usr/local/soft/tomcat7/bin
	- 启动你的tomcat：./startup.sh
![](https://i.imgur.com/5ajwcJ4.png)
- 随后将你的war包安置到tomcat目录下的webaaps目录内；
	- 安置方式，可以选用图形化界面的FTP，也可以选择命令上传，根据个人喜好；
- 我这里使用FTP上传，上传成功后，我们去到webapps下看看发生了什么：
![](https://i.imgur.com/YzlSkUL.png)
- 我们看到，`mallproject.war`会被tomcat自动解析成一个`mallpriject`目录了，到这一步就已经完成
- 接下来，我们在地址栏输入：你的LinuxIP地址+tomcat端口号+你的项目名：
	- 如：192.168.133.239:8080/mallproject
- 然后按回车即可；


----------
- 一般错误描述：
	- 1、本地windows部署可以访问成功，但放到Linux会发生404错误---找不到资源；
	- 此项错误我本人目前也还没有详细的解决办法，希望大牛们给出指导意见！！
	- 我的解决思路：
		- 先确定访问Linux的tomcat主页是否成功；
		- 检查端口号是否被占用；确定之前我所说的前提，本地jdk版本与Linux版本一致；
		- 内部代码有可能与Linux下的tomcat不能兼容，更换tomcat版本，降或升看情况而定；
		- jdk版本有可能过高或过低，需重新安装；
		- 查看tomcat日志：在tomcat/logs目录下，运行：cat catalina.out查看日志；
	- 2、url地址输入错误等；
	- 3、未完待续....
