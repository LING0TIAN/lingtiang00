MyCli 是一个 MySQL 命令行工具，支持自动补全和语法高亮
#尝试过使用–auto-rehash配置，效果不佳。

一、安装
	1、安装pip
		解压pip-9.0.1.tar.gz
		使用python setup.py install 安装(若失败则先执行python setup.py build)。
	2、安装mycli
		进入mycli目录
		执行pip install *
	3、执行mycli看是否弹出命令提示信息。
二、基本环境
	两台机器：
		master: 192.168.111.130		-->修改主机hosts文件，增加 192.168.111.128 slave
		slave : 192.168.111.128		-->修改主机hosts文件，增加 192.168.111.130 master
	分别安装mariadb，并授权：
		master:
			grant all on *.* to 'root'@'%' identified by '123456';
		slave :
			grant all on *.* to 'root'@'%' identified by '123456';
三、远程连接
	master连接slave:
		[root@real Downloads]# mycli -u root  -h slave
		Password: 
		Version: 1.15.0
		Chat: https://gitter.im/dbcli/mycli
		Mail: https://groups.google.com/forum/#!forum/mycli-users
		Home: http://mycli.net
		Thanks to the contributor - orpharion bestheneme
		mariadb root@slave:(none)> 
		
	slave连接master：
		[root@cl ~]# mycli -u root  -h master
		Password: 
		Version: 1.15.0
		Chat: https://gitter.im/dbcli/mycli
		Mail: https://groups.google.com/forum/#!forum/mycli-users
		Home: http://mycli.net
		Thanks to the contributor - www.mysqlfanboy.com
		mariadb root@master:(none)> 


