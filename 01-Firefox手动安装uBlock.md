
# step 1

先确保Firefox开启了自定义安装扩展程序的功能：在地址栏输入`about:config`然后回车，进入到高级首选项界面。

接着在其中的搜索栏查找`xpinstall.signatures.required`设置项，确保其设置为**true**状态。


# step 2

前往ublock的官方仓库的发行页： https://github.com/gorhill/uBlock/releases ，直接点击： uBlock0_版本号.firefox.signed.xpi ，firefox 便会自动安装它。