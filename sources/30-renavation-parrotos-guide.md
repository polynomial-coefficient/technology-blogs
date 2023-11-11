
<hr>

# 快捷启动键

快捷启动建:<br>
Dell: F12 <br>
神舟: F7 <br>


<hr>


# mirror

```

sudo tar -cvf /etc/apt/old-list.tar /etc/apt/sources.list.d/*;
sudo rm -rf /etc/apt/sources.list.d/*;

sudo mv /etc/apt/sources.list /etc/apt/sources-list-backup;

echo -e '\n' >> ./sources.list;
echo "deb https://mirrors.aliyun.com/parrot parrot main contrib non-free" >> ./sources.list;

echo -e '\n' >> ./sources.list;
echo "deb https://mirrors.sjtug.sjtu.edu.cn/parrot/ parrot main contrib non-free" >> ./sources.list;

sudo cp ./sources.list /etc/apt/sources.list.d/;


```


<hr>


# uninstall software


```
sudo apt-get purge xboard -y;
sudo apt-get purge geany -y;
sudo apt-get purge pluma -y;
sudo apt-get purge libreoffice-common -y;
sudo apt-get purge libreoffice-style-colibre -y;
sudo apt-get purge brasero -y;
sudo apt-get purge onionshare -y;
sudo apt-get purge tor -y;
sudo apt-get purge torbrowser-launcher -y;

```


<br>


推荐更换为 qBittorrent-Enhanced-Edition-x86_64.AppImage
```
sudo apt-get remove qbittorrent;
```

<hr>


# 移除多余系统自启服务


查看开机自启动的系统服务:
```
systemctl list-unit-files | grep -i 'enabled' | grep -i 'blue'
```

关闭开机自启动的系统服务:
```

sudo systemctl disable virtualbox-guest-utils.service;


sudo systemctl disable blueman-mechanism.service;

sudo systemctl disable bluetooth.service;

sudo systemctl disable NetworkManager-dispatcher.service;

```

<hr>


查看开机自启动软件程序:

```
dir /etc/xdg/autostart 
```

移除自启程序:
```
sudo mv /etc/xdg/autostart/blueman.desktop ~/Downloads; 
sudo chown -R user:user ~/Downloads/blueman.desktop;
```



# oh-my-zsh
<br>


## install zsh

```
sudo apt-get install zsh;

sudo chsh -s $(which zsh);
```

<br>

## from github

```

sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)";

cd ~/.oh-my-zsh/plugins/;

git clone https://github.com/zsh-users/zsh-autosuggestions

git clone https://github.com/zsh-users/zsh-syntax-highlighting.git


sed -i "s/plugins=(/plugins=(zsh-syntax-highlighting zsh-autosuggestions /g"  ~/.zshrc;

echo -e '\n' >> ~/.zshrc;
echo 'alias del="mv -t ~/.local/share/Trash/files/ --backup=t"'   | tee -a  ~/.zshrc;

echo -e '\n' >> ~/.zshrc;
echo 'alias empty-trash="rm -rf ~/.local/share/Trash/files/*"'   | tee -a  ~/.zshrc;

echo -e '\n' >> ~/.zshrc;
echo 'alias dir="dir -l -h --color"'   | tee -a  ~/.zshrc;

echo -e '\n' >> ~/.zshrc;
echo 'export PATH=/sbin:$PATH' >> ~/.zshrc; 


if [[ -d "~/.local/share/Trash/files/" ]];then
    echo "该目录存在";
else
    echo "该目录不存在,即将创建它";
    mkdir -p ~/.local/share/Trash/files/;
fi

```

<br>

## from gitee

```

sh -c "$(curl -fsSL https://gitee.com/pocmon/ohmyzsh/raw/master/tools/install.sh)";

git clone https://gitee.com/asddfdf/zsh-syntax-highlighting.git  ~/.oh-my-zsh/plugins/zsh-syntax-highlighting;

git clone https://gitee.com/chenweizhen/zsh-autosuggestions.git  ~/.oh-my-zsh/plugins/zsh-autosuggestions;

sed -i "s/plugins=(/plugins=(zsh-syntax-highlighting zsh-autosuggestions /g"  ~/.zshrc;

echo -e '\n' >> ~/.zshrc;
echo 'alias del="mv -t ~/.local/share/Trash/files/ --backup=t"'  | tee -a  ~/.zshrc;

echo -e '\n' >> ~/.zshrc;
echo 'alias empty-trash="rm -rf ~/.local/share/Trash/files/*"'  | tee -a  ~/.zshrc;

echo -e '\n' >> ~/.zshrc;
echo 'alias dir="dir -l -h --color"'   | tee -a  ~/.zshrc;

echo -e '\n' >> ~/.zshrc;
echo 'export PATH=/sbin:$PATH' >> ~/.zshrc; 


if [[ -d "~/.local/share/Trash/files/" ]];then
    echo "该目录存在";
else
    echo "该目录不存在,即将创建它";
    mkdir -p ~/.local/share/Trash/files/;
fi

```

**安装fcitx和ohmyzsh后,重启系统**



<hr>


# ssh

<br>

```
sudo apt-get install openssh-server;
```

<br>

```
sudo service ssh start;
service ssh status;
sudo service ssh restart;

```

<br>

或者:
```

sudo /etc/init.d/ssh  start;
/etc/init.d/ssh status;
sudo /etc/init.d/ssh restart;
```

<hr>


# vimrc location

```
dir ~/.config/nvim/
```

<hr>



# vlc player 

播放器设置中的文件路径变量: ` $N `


<hr>


