<hr>

+ install node

```

# 末尾不要有反斜杠
u1=/your/nodejs/path;
echo $u1;

wget https://cdn.npmmirror.com/binaries/node/v18.12.1/node-v18.12.1-linux-x64.tar.xz;

tar -xvf node-v18.12.1-linux-x64.tar.xz -C $u1;


echo -e '\n' >> ~/.zshrc;
echo -e '\n' >> ~/.zshrc;

echo "# node.js" | tee -a  ~/.zshrc;

echo -e '\n' >> ~/.zshrc;

echo "export NODE_HOME=${u1};" | tee -a  ~/.zshrc;

echo -e '\n' >> ~/.zshrc;

echo "export PATH=$PATH:$NODE_HOME/bin;" | tee -a  ~/.zshrc;

echo -e '\n' >> ~/.zshrc;

echo "export NODE_HOME=$NODE_HOME/lib/node_modules;" | tee -a  ~/.zshrc;

source ~/.zshrc;

```


<hr>


+ upgrade npm

```
npm --registry=https://registry.npm.taobao.org install -g npm
```


<hr>
