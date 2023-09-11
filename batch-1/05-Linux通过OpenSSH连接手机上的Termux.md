**充分必要前提: 必须位于同一个网络内(无公网IP情况下)**

<HR>


- termux 运行 
```
#可以在添加国内清华镜像源后执行
pkg update
```

<br>

- termux 安装ssh套件: 
```
pkg install openssh
```

<br>

- termux执行 `passwd` 给手机Tmux设置一个密码，不然Linux可能会被拒绝连接 

<br>

- termux 执行 ssh 查看是否安装成功，成功后输入` sshd ` 开启 ssh 服务

<br>

- termux 查看手机Tmux端IP地址: `ifconfig | grep -i inet`

<br>

- 登录手机Tmux端:
  - ssh 手机Tmux端IP地址 -p 8022
  <br>
  - ssh -p 8022 手机Tmux端IP地址 


```


- 会询问你是否想要连接,yes. 然后请输入之前设置的密码,连接成功
