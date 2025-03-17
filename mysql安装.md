windows 1.在 mysql 官网下载文档后安装 2.在终端使用 net start mysql80 启动 mysql，使用 net stop mysql80 停止 mysql，note 需要使用管理员身份进行运行终端 3.在终端中可以使用 4.客户端连接 mysql: mysql [-h 127.0.0.1] [-P 3306] -u root -p
<h2>Linux</h2>
在官网上下载完包之后
安装上传程序
apt install lrzsz
rz -E 上传文件
执行安装命令 dpkg -i mysql-apt-config_0.8.33-1_all.deb
更新包信息 apt-get update
执行安装命令 apt-get install mysql-server
<h6>进入数据库</h6>
mysql -uroot -p<br>
在mysql中可以使用setpassword=password('密码')来修改密码
<h6>Linux 启动数据库</h6>
service mysql start<br>
service mysql stop<br>
ps -u mysql 查看数据库是否启动<br>
使用exit退出数据库
