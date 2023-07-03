Linux下本地主机挂载远程服务器文件系统


本机挂载远程服务器文件系统要用到sshfs服务，如果没有，需安装它:
```
sudo apt-get install sshfs

```

---------------------------------------------
  


挂载分两种：临时与永久,这里先暂时使用临时挂载

### 临时

0.第一步，修改 /etc/fuse.conf，在 /etc/fuse.conf 内添加`user_allow_other`，或者取消对应的注释。


1.第二步，执行如下
```

sudo sshfs -o cache=yes,allow_other RemoteName@RometeIP:/home/romete/folder /home/local/sshfs-dir

```

----------------------------------------------------

### 卸载挂载

```

sudo umount -v /home/local/sshfs-dir

```