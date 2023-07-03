下载的是mysql-glibc压缩包
===

----------------------------------------------

#### 前置配置

+ 使用 "tar xvf" 解压 mysql-linux-glibc-x86_64.tar.xz 至某个文件夹，如 **/home/user/myself/mysql**

+ 创建mysql用户：adduser mysql

+ 将mysql所在安装目录持有者改为 mysql ：`chown -R mysql:mysql /home/user/myself/mysql`

+ 赋予权限 ： chmod -R 775 /home/user/myself/mysql

+ 创建配置文件并编辑自定义参数：touch /etc/my.cnf

``````

[mysql]
#auto-rehash是自动补全的意思
auto-rehash

#默认连接端口　　　　　　　　　　　　　　　　　
port = 3306

#用于本地连接的socket套接字
socket = /tmp/mysqlx.sock

#编码
default-character-set = UTF8MB4

[mysqld] 
#skip-name-resolve 

# 指定默认编码格式
character-set-server=utf8

# 设置3306端口
port = 3306  
socket=/tmp/mysqlx.sock

# 设置mysql的安装目录 
basedir=/home/user/myself/mysql/mysql-linux-glibc-x86_64

# 指定pid文件
pid-file=/home/user/myself/mysql/pid/3306/mysql.pid

# 设置mysql数据库的数据的存放目录 
datadir=/home/user/myself/mysql/data

# 指定错误日志
log-error=/home/user/myself/mysql/log/err.log

# 允许最大连接数 
max_connections=200

# 服务端使用的字符集默认为8比特编码的拉丁字符集 
character-set-server=utf8 

# 创建新表时将使用的默认存储引擎 
default-storage-engine=INNODB 
#lower_case_table_name=1 
max_allowed_packet=16M



``````
  

+ 添加系统变量：vi /etc/profile,把以下内容粘贴在末尾：

``````
# mysql
MYSQL_HOME=/home/user/myself/mysql/mysql-linux-glibc-x86_64
PATH=$PATH:$MYSQL_HOME/bin
export PATH MYSQL_HOME


``````

source /etc/profile ，即时生效

---------------------------------------

### 初始化and启动and登录

+ 初始化，进入安装路径bin目录，执行：**`./mysqld --initialize --user=mysql`**

	如果报缺少 libaio 依赖错误，
	centos ：yum install libaio
	ubuntu ：sudo apt-get install libaio1

+ 根据my.cnf中的日志路径,得到初始的临时密码

``````

[Server] A temporary password is generated for root@localhost: 9Pdvi0ifts^c


``````

+ 启动并登录

 进入support-fils目录，执行：` sudo ./mysql.server start ` 或者 ` sudo ./mysql.server start --user=mysql `

（也还有另一种本地启动方法：./bin/mysqld_safe,此方法是`./mysql.server start`的底层脚本方式）

 在新窗口，输入：mysql -uroot -p，然后提示输入密码，把初始密码输入进去，便可看到：

``````

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 8
Server version: 8.0.20

Copyright (c) 2000, 2020, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.


``````

success.

----------------------------

+ 改密码：` alter user 'root'@'localhost' identified by 'newPassword'; `

+ 查看用户host地址： ` select user,host from mysql.user; `

-----------------------

#### 服务端启动与停止之命令

如果懒得配置系统自启服务列表,可以配置软链接或在bashrc设alias,就是麻烦点,每次启停都需要手动操作

````````````

# mysql-start
sudo /home/user/myself/mysql/8.0.20/mysql-linux-glibc-x86_64/support-files/mysql.server start --user=mysql


# mysql-stop
sudo /home/user/myself/mysql/8.0.20/mysql-linux-glibc-x86_64/support-files/mysql.server stop --user=mysql

````````````
