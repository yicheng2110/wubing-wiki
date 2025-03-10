# 关于

> 本wiki是基于Mkdocs一个基于python的开源文档（wiki）发布系统。

### 基础用法

#### 编写

文档可写在：`docs/xxx/xxx.md` 中。

在`根目录`的`mkdocs.yml`的 nav 节点中添加菜单目录即可

#### 运行

因为本文档是基于python的 mkdocs项目，随意拉取代码后第一步就是按照依赖

1. 拉取文档
``` shell
# 不需要指定目录
git clone https://github.com/yicheng2110/wubing-wiki.git

# 指定目录拉取
git clone https://github.com/yicheng2110/wubing-wiki.git "D:/code/wiki"
```

2. 按照依赖 (最后基于虚拟环境：`python -m venv .venv`)
``` shell
pip install -r requirements.txt
```

3. 运行本地环境
``` shel
mkdir serve
```

#### 发布

> 1. 自定义部署（生成html）
``` shell
mkdocs build
```

这将创建一个名为site的新目录。 看一下该目录的情况：
``` shell
Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----       2025/3/10  下午 02:37                about
d-----       2025/3/10  下午 02:37                assets
d-----       2025/3/10  下午 02:37                search
-a----       2025/3/10  下午 02:37          15513 404.html
-a----       2025/3/10  下午 02:37          15789 index.html
-a----       2025/3/10  下午 02:37            109 sitemap.xml
-a----       2025/3/10  下午 02:37            127 sitemap.xml.gz
```

如果自定义部署子直接把site目录的所有文件上传到指定目录即可

> 2. 使用github 的pages 来部署项目
```shell
mkdocs gh-deploy
```
在本地拉取github文档后，如果对文章进行进行变更以后，可以直接执行该命令直接部署pages

### 常见问题
#### 如果Pages使用了自定义域名则实行以下步骤 

**a. 添加`cname` dns记录，比如：将`wiki.20211001.xyz`记录`cname`到你得`github`主页地址：`github.com/yicheng2110`**

**b. 在master分支docs目录中创建一个`CNAME`文件，文件内容就是自定义域名地址: `wiki.20211001.xyz` 不需要加http,https协议头**

#### 如果在github的网页操作了什么配置。可能会导致仓库发生了改变。、

此时可能执行`mkdocs gh-deploy`命令可能会失效
我这边的解决方案为，本地git检出到`gh-pages`分支，且重新拉取`gh-pages`仓库，大概率会有新的代码。
此时再切换到master分支中，执行`mkdocs gh-deploy`命令记录即可操作成功。