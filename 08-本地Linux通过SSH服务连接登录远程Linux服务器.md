### 本机Linux通过SSH服务连接登录远程Linux服务器

查看IP:
+ 方式1: `ifconfig`
+ 方式2: `ip addr`

<hr>


登录命令格式:  **ssh 远程服务器用户名@远程服务器IP**

命令启动ssh服务:  
```  

#其他参数还有 stop/status
/etc/init.d/ssh start  

#第二种方式, 其他参数还有 restart/stop/status
service sshd start

```  

侦听端口(一般为22): ` netstat -na | grep 22 `
  


-----------------------------
  


### 使用scp命令来通过ssh传输文件

+ 下载远程服务器上的文件
```
#把远程服务器上的 /remote/file.txt 下载到本地的 ./local

scp 远程服务器用户名@远程服务器IP:/remote/file.txt ./local
```

+ 上传本地文件到服务器
``````
#把本机上的 ./local/file.txt 上传到远程服务器上的/remote/dir 文件夹

scp ./local/file.txt 远程服务器用户名@远程服务器IP:/remote/dir

``````


+ 从服务器下载文件夹至本地
``````

#把远程服务器上的 /remote/dir1 目录下载到本地的 ./local/dir2

scp -r 远程服务器用户名@远程服务器IP:/remote/dir1 ./local/dir2

``````


+ 自本地上传文件夹到远程服务器
``````

#把本地的 ./local/folder 目录上传到远程服务器的 /remote/folder2 目录

scp -r ./local/folder 远程服务器用户名@远程服务器IP:/remote/folder2
 
``````


