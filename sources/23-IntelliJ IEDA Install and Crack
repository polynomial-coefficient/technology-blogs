# 下载
```

git clone https://github.com/libin9iOak/ja-netfilter-all.git

```


或者,前往 https://3.jetbra.in/ , 选择其中一个可访问的节点网址, 进入后看见 `Download jetbra.zip`, 点击 `jetbra.zip`.
复制相应IDE的激活码.

把 `jetbra.zip` 和 `clion2022` 放在同一个父级文件夹之下,解压`jetbra.zip`.

<br><hr>

# 清理残余

首先,要在根目录下清理干净所有与Jetbrains有关的文件.
``````
find ~/ -iname '*jetbrains*'
``````
把与jetbrains相关的文件夹和文件删除或者移动到别的目录.

<br><hr>

# 运行脚本
 
```
bash jetbra/scripts/uninstall.sh; bash jetbra/scripts/install.sh;

```

脚本会给 `jetbra/vmoptions/` 目录下的 `clion.vmoptions` 添加一些内容

<br><hr>

# vmoptions
删除或移走 `clion-2022.2.4/bin/` 下的`clion64.vmoptions`, 而将`jetbra/vmoptions/` 目录下的 `clion.vmoptions` 粘贴到`clion-2022.2.4/bin/`并更名为`clion64.vmoptions`.

```
mv ./clion-2022.2.4/bin/clion64.vmoptions  ~/past-version.clion64.vmoptions;

cp ./jetbra/vmoptions/clion.vmoptions  ./clion-2022.2.4/bin/clion64.vmoptions;
```


<br><hr>

# 启动

运行 `./clion-2022.2.4/bin/clion.sh`, 若是出现以下内容, 就说明成功加载了破解包 `ja-netfilter.jar` :

``````

============================================================================  

    ja-netfilter 2022.2.0

    A javaagent framework :)

    https://github.com/ja-netfilter/ja-netfilter

============================================================================

``````

将之前复制到的激活码, 粘贴在 `Activation code` 窗口内, 点击 Activate.

<br><hr>

# 第四步

建立软链接:
```
sudo ln -s /yours/path/clion-2022.2.4/bin/clion.sh /usr/local/games/clion
```
