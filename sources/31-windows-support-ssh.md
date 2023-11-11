# 前提：

Windows必须事先设置好密码，否则届时登录Windows时会报密码错误

------------------------------------------

# 获取所需的 OpenSSH 文件

安装文件可以在 github 的 powershell 团队项目下进行下载。

下载地址： 

- https://github.com/PowerShell/Win32-OpenSSH/releases

<br>

- https://gitee.com/through-git/through-blogs/raw/master/packages/OpenSSH-Win64.zip


<hr>


# 安装 OpenSSH 

这一步非常简单，只用把下载好的压缩文件解压出来即可。
首先已经下载好 OpenSSH，并且进行解压
把 OpenSSH 整个目录进行复制到 E:\Program Files (其实哪个目录都可以)

<hr>

# 配置参数
单击计算机，右键 --> 属性 --> 高级系统设置 --> 环境变量–系统变量，在此框里面找到 Path 进行编辑，windows7 系统编辑时候是以文本形式，所以就需要在最后先添加 “；” 英文分号，再把你安装路径如 E:\Program Files\OpenSSH-Win64 粘贴进去。

----------------------------------------------


# ssh 测试

使用 cmd 命令打开 dos 命令行，或者打开 windows 的 PowerShell，直接输入ssh命令，可以得到如下显示:

```
usage: ssh ...

```


<hr>


# 让 SSH 进入系统服务

打开cmd，移动到E盘:`e:`

然后 cd 到 openssh 安装文件夹，在CMD界面依次执行以下命令:

## 1）安装 sshd 服务

```
powershell.exe -ExecutionPolicy Bypass -File install-sshd.ps1

```

## 2）开放 22 号端口

（如果 windows 已经关闭了防火墙,并配置了入站规则,可以不执行如下命令，但额外执行亦不影响）

```

netsh advfirewall firewall add rule name=sshd dir=in action=allow protocol=TCP localport=22

```

## 3）设置 sshd 服务开机自启 
```
sc config sshd start = auto
```

## 4) 启动服务

```
net start sshd
```

第一次安装完服务之后还需要手动打开一下服务，后面配置过自启之后就不用管了。

## 5）检查端口

查看本机的 22 端口是否被监听
```
netstat -ano | findstr "22"

```

## 6）检查服务运行状态

```
sc query sshd
```

<hr>


# 查看本机ip地址：
```

ipconfig /all | findstr "192.168."

```
其中的 `IPv4 Address` 就是目标


# 查看当前用户名：
```
echo %username%
```

# 登录:
```
ssh %username%@IPv4Address
```