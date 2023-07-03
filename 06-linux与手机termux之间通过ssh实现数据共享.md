		
### 充分必要前提: 
0.必须位于同一个网络内(无公网IP情况下)

1.手机端和电脑端必须都安装了ssh服务,且都同时开启了ssh服务,不然会报"拒绝连接"的错误

2.TermuxUname: 手机Termux端的用户名,可通过`whoami`查看

3.Termux.IP: 手机Termux端的IP地址,可通过`ifconfig`查看

4.LinuxUserName@Linux.ip: Linux用户名@Linux的IP地址

5.默认端口是8022


<hr>


## 在linux操作


### 将Linux上的文件发送到手机:
```

scp -r -P 默认端口 ./File TermuxUname@Termux.IP:~/

```

<hr>


###  复制liunx上的文件夹到手机：

``````

scp -r -P 默认端口 ~/Folder TermuxUname@Termux.IP:~/

``````   



<hr>

### 复制手机上的文件至本地linux:

```

scp -r -P 默认端口 TermuxUname@Termux.IP:~/File.zip ./

```



<hr><hr>
  



## 在Termux操作

### 复制手机里的文件到Linux：

```

scp -r -P 默认端口 ～/File LinuxUserName@Linux.ip:~/


```  

<hr>


### 复制手机中的文件夹到Linux：

```

scp -r -P 默认端口 ~/DirName LinuxUserName@Linux.ip:~/


```


