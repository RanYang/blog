##Linux GitHub Blog Start

####GitHub 注册与新建 仓库
1.注册 [github](https://github.com/)

2.页面右上角，姓名旁边, 点击新建仓库

3.Repository Name -> blog, 勾选 Initialize this repository with a README，确定

####Linux 安装配置Git
1.Git 的工作需要调用 curl，zlib，openssl，expat，libiconv 等库的代码，所以需要先安装这些依赖工具

``sudo apt-get install curl-devel expat-devel gettext-devel openssl-devel zlib-devel``

2.Git 核心包

``sudo apt-get install git-core``

3.Git配置

    首先要配置的是你的用户名称和电子邮件。这两条配置很重要，每次 Git 提交时都会引用这两条信息，说明是谁提交了更新，所以会随更新内容一起被永久纳入历史记录：
    ``
    $ git config --global user.name "RanYang"
    $ git config --global user.email "@gmail.com"
    ``
    接下来要设置的是默认使用的文本编辑器。Git 需要你输入一些额外消息的时候(比如提交更新写描述信息时)，会自动调用一个外部文本编辑器给你用。
        
    ``
    $ git config --global core.editor vim
    
    ``
    在解决合并冲突时使用哪种差异分析工具.
    ``
    $ git config --global merge.tool vimdiff
    ``
    查看配置信息的相关命令
    查看所有配置
    ``
    git config --list
    ``
    
    现在，在你的系统上已经装好了 Git，并完成了基本的配置。

    若在以下任何步骤中出现SSH PERMISSION DENIED就可以是以下步骤不正常
    
    (1)跳到家目录.ssh下
    ``
    cd ~/.ssh
    ``
    (2)SSH-KEYGEN(一路按Y到最后)
    ``
    ssh-keygen -t rsa -C "ran.yang"
    ``
    (3)添加密钥到GITHUB上
    ``
    复制 id_rsa.pub 到 GITHUB 个人首页(右上角)Account setting->（左边导航）SSH KEYS -> 添加刚刚的密钥到里面
    ``
    
    此部分内容来源与 http://codingnow.cn/git/195.html
    
####Linux Git本地开发

1.创建文件夹 mygit
    ``
    mkdir mygit
    cd mygit
    ``
2.初始化 mygit
   ``
   git init
   ``
3.添加文件
    ``
    touch hello.txt
    ``
4.将文件添加到管理系统中(所生成的快照并存放到一个临时的存储区域， Git 称该区域为索引)
    ``
    git add hello.c
    ``
5.提交到仓库(commit 仅是操作的本地库)
    ``
    git commit -m “Version 1.0 hello.txt”
    ``
6.添加远程仓库(origin)路径
    ``
    git remote add origin https://github.com/RanYang/blog.git
    ``
7.本地修改后的内容推送到服务器MASTER分支上()
    ``
    git push origin master
    ``
    此处可能会提示你please git pull最新代码
    
    代表MASTER上有比这个分支更新的内容
    
    ``
    git pull origin master
    ``
    再提交，就能在GITHUB上看到自己最新的代码

####GIT BLOG
1. 进入到刚刚本地新建的工作区
   ``
   cd mygit
   ``
2. 如果你的项目不存在 README.md (或 README.markdown)，你首先需要建立一个README.md (或 README.markdown)。

3. mygit的根目录新增gitpress.json

   ``
   touch gitpress.json
   ``
    
   gitpress.json模板
   
   <code>
   {
    "docs" : ["posts"],
    "template" : "default",
    "domain_alias" : ["your.domain"],
    "perpage" : 10,
    "order" : "number",
    "types" : {
    "\\.(md||markdown)$" : "markdown",
    "\\.(js||css||json)$" : "code",
    "\\.html?$" : "html",
    ".*" : "text"
    },
    "title" : "Akira's Blog",
    "description" : "My Blog Description...",
    "comment" : "on",
    "friends" : [
    {
    "name" : "github",
    "title" : "github",
    "url" : "http://github.com"
    },
    {
    "name" : "gitpress",
    "title" : "gitpress",
    "url" : "http://gitpress.org"
    }
    ]
    }
   </code>

4.提交到远程版本库

    ``
    $ git add .
    $ git commit -m "test add"
    $ git push origin master
    ``
5. 2－3分钟后访问blog.用户名.gitpress.org(很多教程说只要仓库名字叫BLOG就不用在域名前加blog,但我的是不能访问的，我也不知道为什么)

以下几种方式都可以新建一个BLOG：
http://www.cnblogs.com/shanyou/archive/2012/09/22/2698368.html（最简单）
http://www.html-js.com/article/1586（较简单）
http://www.ilehao.com/blog/2012/11/11/github-blog-config/

    
    
    