# 常用shell方法汇集

<hr>

## 批量给文本内容的每行首尾加上前后缀
<br>

-i 表示直接在其中修改

```
sed -i 's/^/head&-/g' file.log;  sed -i 's/$/-&tail/g' file.log;

```

<hr>

## 批量更改文件的扩展后缀名(以mp4为例)
```
number=0;

for i in *.mp4; do
	
	number=$((number+1));
	echo $number-$i;
	mv $i 'enormous-'$number-$i;

done
```

<hr>

## 获取统计文件或文件夹的数量
<br>

counting files amount:
```
dir -l -a -h ././ | grep -i '^-' | wc -l 
```

<br>

counting directoies amount:
```
ls -l ././ | grep -i '^d' | wc -l 
```

<hr>

## 给系统安装自定义字体

显示所有已安装的字体列表
```
fc-list
```

正式安装
```
sudo mkfontscale;sudo mkfontdir;sudo fc-cache -fv

```

<hr>


## 注释系统网络代理端口的设置

```
sed -i 's/^/#&/' ~/.ssh/config;

```

<hr>

## ssh服务的启动与状态查看
```
sudo service sshd start;
service sshd status;
```

<hr>

## 管理员模式下vimrc配置不起作用
<br>
出现以下情况：
<br>

直接使用` vi file `打开文件时一切正常，配置也生效.
<br>
但当你使用` sudo vi file `打开文件时，配置文件并没有生效.

<br>

出现这种情况的原因是：当你使用 `sudo` 命令的时候，用户的身份切换了(默认是root),此时你的环境变量也被重置了，系统当然就找不到你的配置文件。

<br>

解决的方案：
使用` sudo -E vi file `打开文件 (最快速的方法，不过每次都需要加上 -E, 有点麻烦)
<br>

具体的参考这篇文章：https://cloud.tencent.com/developer/article/1650340
<br>
如果链接失效了就自己搜索一下"sudo 命令找不到环境变量"相关关键字

<hr>

## Termux
```
scp -r -P 8022 FILENAME ux_xxx@192.168.xxx.xxx:~/storage/shared/Alarms/
```

<hr>




## xrandr

* `xrandr --listmonitors`

* `xrandr --output HDMI-1 --auto --output eDP-1 --off`

* `xrandr --output HDMI-1 --primary --left-of eDP-1`

* `xrandr --output eDP-1 --off`




<hr>


## open edge without proxy
```
microsoft-edge --no-proxy-server

```

<hr>


## 将指定目录导入至环境变量
```
export PATH=$PATH:/specify/directory/;
```

<br>

或者:
```
export PATH=/specify/directory/:$PATH;
```

<hr>

# 查看当前目录下各文件夹大小命令

```
du -h --max-depth=1 ./

```

<hr>


# sed html

```
#使用正则表达式将 LAST_MODIFIED="内容" 替换为空字符串
sed -i 's/LAST_MODIFIED="[^"]*"//g' *.html;
sed -i 's/ICON="[^"]*"//g' *.html;
sed -i 's/ICON_URI="[^"]*"//g' *.html;

#将 HREF=" 替换为 TARGET="_BLANK" HREF="
sed -i 's/HREF="/TARGET="_BLANK" HREF="/g' *.html;
```

<hr>


# WebP转换为JPEG

+ 安装ImageMagick：
```
sudo apt-get install imagemagick
```


+ 转换为JPEG格式：
```
convert input.webp output.jpg
```

<hr>


# 遍历某种类型文件并添入数组之中

```
# 初始化存储文件名的数组
TXT_files=()

# 遍历当前目录下的所有TXT文件
for file in *.TXT; do
    # 检查文件是否存在
    if [ -e "$file" ]; then
        # 添加文件名到数组
        TXT_files+=("$file")
    fi
done

# 打印数组中的文件名
echo "TXT文件列表:"
for TXT_file in "${TXT_files[@]}"; do
    echo "$TXT_file"
done

```

<hr>

