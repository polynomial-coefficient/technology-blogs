

做python项目时,想安装某个依赖包的最新版本,但又不知道它的版本号具体到多少,因此需要搜索查看它的相关简介信息.

原来的时候,可以直接通过pip搜索查看: `pip search xxx`.

但如今,再用这种方式会报错:

```
pip search django 
ERROR: XMLRPC request failed [code: -32500]
RuntimeError: PyPI no longer supports 'pip search' (or XML-RPC search). Please use https://pypi.org/search (via a browser) instead. See https://warehouse.pypa.io/api-reference/xml-rpc.html#deprecated-methods for more information.

```

<hr>

于是,得换另一种方法:`pip_search`,首先是安装`pip_search`:
```
pip install pip-search

```

安装完毕后,直接使用可能会报错找不到`pip_search`.因为本文所讨论的是在linux环境下,而pip下载依赖模块的路径可能是在`~/.local/bin`,这个路径可能尚未加入到系统环境变量中,所以需要:

```
echo -e "\n" >> ~/.bashrc;

echo "export PATH=~/.local/bin:NewNewNewPATH;" >> ~/.bashrc;

sed -i "s/NewNewNew/$/g" ~/.bashrc;

source ~/.bashrc;

```

<hr>

使用示例:

```
pip_search django
```


结果:
``````
                   🐍 https://pypi.org/search/?q=django 🐍                     
┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━┳━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━┓
┃ Package                             ┃ Version ┃ Released   ┃ Description     ┃
┡━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━╇━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━┩
│ 📂 Django                           │ 4.1.6   │ 01-02-2023 │ A high-level    │
│                                     │         │            │ Python web      │
│                                     │         │            │ framework that  │
│                                     │         │            │ encourages      │
│                                     │         │            │ rapid           │
│                                     │         │            │ development and │
│                                     │         │            │ clean,          │
│                                     │         │            │ pragmatic       │
│                                     │         │            │ design.         │
│ 📂 django-503                       │ 0.1     │ 03-10-2011 │ An app to show  │
│                                     │         │            │ 503 error page, │
│                                     │         │            │ while your      │
│                                     │         │            │ django site is  │
│                                     │         │            │ on maintenance. │
│ 📂 django-filebrowser-django13      │ 3.0     │ 14-03-2011 │ Media-Manageme… │
│                                     │         │            │ with the Django │
│                                     │         │            │ Admin-Interfac… │
│                                     │         │            │ Package for     │
│                                     │         │            │ using without   │
│                                     │         │            │ django-grapelli │
│                                     │         │            │ in Django 1.3   │
│ 📂 django-tracking-analyzer-django2 │ 0.3     │ 02-01-2019 │ User actions    │
│                                     │         │            │ tracking and    │
│                                     │         │            │ analytics for   │
│                                     │         │            │ Django sites. 

......

``````