# 设置vmware中的linux系统与主机共享某个文件夹

<hr>


## vmware方面


#### 点击linux虚拟机-->编辑虚拟机设置-->选项-->共享文件夹-->总是启用-->选中主机内某个文件夹



<hr>


## 虚拟机linux方面

- 确保安装了 vmware tools


- 安装了 vmware tools之后,在/mnt创建一个文件夹:

```
sudo mkdir /mnt/hgfs/;

```

文件夹名称必须是**hgfs**.


<hr>


- 查看vmware设置的主机中的共享文件夹名称:

```
vmware-hgfsclient 

```

<hr>


- 临时挂载共享文件夹
```

sudo vmhgfs-fuse .host:/ /mnt/hgfs/;

```

<hr>

- 永久挂载共享文件夹

<br>

```

echo -e "\n" | sudo tee -a /etc/fstab;

echo ".host:/ /mnt/hgfs fuse.vmhgfs-fuse allow_other,defaults 0 0" | sudo tee -a /etc/fstab;

```

<hr>


- 总结:

<br>

```
hg=$(vmware-hgfsclient);

echo $hg;

sudo vmhgfs-fuse .host:/ /mnt/hgfs;

sudo ls -lah /mnt/hgfs/$hg;

sudo cp -r ./*.tar /mnt/hgfs/$hg;

```




<hr>


# 兜底方案

如果
```
vmware-hgfsclient 
```
没有返回值,说明遇到了更底层的棘手障碍,为了效率,请使用网页在线互传来传送文件.
