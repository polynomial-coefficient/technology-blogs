
以下是在 Linux(Debian) 系统下安装 Manim 的步骤：

### 首先查看python3的版本号。
```
python3 -V
```
结果是: 3.9, Manim 最新版本 1.6.1 支持 python3.7 以上（包括python3.7）。

<hr>

### 安装系统依赖： 

包括FFmpeg、OpenGL、Pango（包括 Pango 的开发头文件）、LaTeX等。

* 安装 FFmpeg:
```
sudo apt-get install ffmpeg;
```

* 安装OpenGL：
```
sudo apt install libglu1-mesa-dev freeglut3-dev mesa-common-dev
```

* 安装Pango：
```
sudo apt install libpango1.0-dev
```

* 安装 libssl-dev：
```
sudo apt install libssl-dev
```

<hr>


### 安装和配置 texlive：

* 下载：
```

wget https://mirrors.tuna.tsinghua.edu.cn/CTAN/systems/texlive/Images/texlive.iso

```

* 使用图形化界面安装texlive，需要安装perl-tk组件：
```
sudo apt-get install perl-tk
```

* 加载镜像文件
```
sudo mkdir /mnt/texlive/;
sudo mount -o loop texlive.iso /mnt/texlive/
```


* 用图形界面进行安装
```
cd /mnt/texlive/;
sudo ./install-tl -gui
```


* 安装完成后，卸载镜像文件
```
cd /; 
sudo umount /mnt/texlive/
```


* 安装完TeX Live后，还需要配置环境变量,在bashrc最后中添加：
```
export PATH=/usr/local/texlive/2018/bin/x86_64-linux:$PATH
export MANPATH=/usr/local/texlive/2018/texmf-dist/doc/man:$MANPATH
export INFOPATH=/usr/local/texlive/2018/texmf-dist/doc/info:$INFOPATH
```
ps：版本号`2018`可以改成其他版本号，如2022，2021，2020等，根据自己安装的版本决定版本号。

刷新.bashrc:
```
source ~/.bashrc
```

* 字体设置:
要在整个系统中使用 TeX 字体，还需要将 TeX 自带的配置文件复制到系统目录下:
```
sudo cp /usr/local/texlive/2018/texmf-var/fonts/conf/texlive-fontconfig.conf /etc/fonts/conf.d/09-texlive.conf
```


刷新字体数据库:
```
sudo fc-cache -fv
```

检查一下是否安装成功：
```
tex -v
```

<hr>



* 安装过程中出现报错: 

ERROR: moderngl-window 2.4.3 has requirement Pillow <10,>=9,but you'll have pillow 7.0.0 which is incompatible.


解决：
```
pip3 install --upgrade pillow
```



* 安装 ManimGL

去往 https://github.com/3b1b/manim/releases，查找自己系统中python3版本对应的 ManimGL 版本，例如 python 3.9 对应的是`manimgl-1.6.1`及以下，那就下载`manimgl-1.6.1-py39-none-any.whl`(下载的whl文件必须保持原名不变，不要改名)。

然后执行：
```
pip install manimgl-1.6.1-py39-none-any.whl
```

<hr>

### 获取manim模板工程
```
git clone https://github.com/3b1b/manim
```

<hr>

测试安装是否成功。在manim目录下，使用以下命令在命令行中运行一个简单的场景：
```
manimgl example_scenes.py OpeningManimExample
```
如果自动出现一个简单的场景可播放文件，说明 Manim 安装成功了。

<hr>

### 可选步骤：

如果你想要自定义 Manim 的配置，可以编辑 custom_config.yml 文件。你可以在运行 Manim 的当前目录下创建一个新的同名文件，然后在该文件中设置你的自定义配置。例如，你可以指定视频输出路径、图片和音频文件的路径、样式和视频质量等等。

