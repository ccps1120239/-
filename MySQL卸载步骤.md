## MySQL的完整卸载步骤：

说明：

**此步骤的目的是，不仅仅是在控制面板卸载了MySQL的安装软件，**

**还需要去删除MySQL原有的一些存储数据(包括原本的初始化设置的配置)，和注册表的删除；**

- 控制面板卸载MySQL；
- 将安装目录下的`MySQL`文件夹删除(有就删，没有就跳过)；
- 将C盘中的`programdata`文件夹下的`MySQL`文件夹删除(有就删，没有就跳过)；
	- 此步骤有一个前提：首先，`programdata`内的MySQL文件夹存放的是`data`文件夹，此文件内存放的是你建立表的数据与表的结构；
	- 如果你在安装的时候选择了更换了此文件夹的路径(系统默认在C:\ProgramData\MySQL内)，
	- 则需要去找到你当时选择安装的路径下去进行删除；
- 将C盘中`program file`下`MySQL`文件夹删除(有就删，没有就跳过)；
	- 此路径存放的是你MySQL服务安装的路径，一般也是默认在C盘，如果你更换了位置则去手动删除即可；
- 打开cmd，输入：`regedit`；
- 删除`HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\Eventlog\Application\MySQL`文件夹；(有- 就删，没有就跳过)；
- 删除`HKEY_LOCAL_MACHINE\SYSTEM\ControlSet002\Services\Eventlog\Application\MySQL`文件夹；(有就删，没有就跳过)；
- 删除`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Eventlog\Application\MySQL`的文件夹；(有就删，没有就跳过)；
- 执行完上述步骤后，打开cmd运行services.msc，查看是否有MySQL服务，
	- 如果有：再次打开cmd(以管理员身份运行)，输入：`sc delete 服务名`(如：`sc delete MySQL`)，即可删除服务。