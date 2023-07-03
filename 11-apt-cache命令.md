
# 介绍

apt-cache 命令可显示 apt 内部数据库里的多种信息. 这些信息是从`/etc/apt/sources.list`文件内全部软件包仓库来源的缓存. 于运行`apt update`运作时所缓存的. 

apt包管理器的工作就建立在软件包元数据的本地缓存上. 通过`apt-cache`命令, 可以查询本地apt缓存并获得相关信息. 

apt缓存的位置是`/var/lib/apt/lists/`目录. 

缓存哪些仓库元数据取决于你的源列表,亦即`/etc/apt/sources.list`文件中添加的仓库, 以及位于`/etc/apt/sources.list.d`目录下的额外仓库文件. 


# 使用

- 在线查找可安装的软件名:
`apt-cache search PkgName`

<br>

- 若想知道完整细节, 那就加上 --full 选项:
`apt-cache search --names-only PkgName --full`

<br>

- 获取详细的包装信息:(已经知道确切的软件包名称):
`apt-cache show PkgName`

<br>

- 显示软件包的名称、版本、正向和反向依赖关系等信息:
`apt-cache showpkg PkgName`

<br>

- 在线查找并列出软件包的版本号,来源:
`apt-cache madison PkgName`

<br>

- 安装指定版本和指定软件源的软件包:
`apt-get install <<PkgName>>=<<version>> `
如: ` apt-get -y install redis=5:6.0.16-1+deb11u2~bionic-proposed `

<br>
 
- 如果指定了软件包的名称, 它将显示该软件包是否已经安装, 在哪个版本的仓库中可用, 以及它的优先级:
`apt-cache policy PkgName`
如: `apt-cache policy redis`
每个已安装的软件包的版本优先级默认为100, 未安装的软件包的优先级默认为600.
同一软件包可能有多个不同优先级的版本. apt会安装优先级较高的版本, 除非安装的版本较新.

