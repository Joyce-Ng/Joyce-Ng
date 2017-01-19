## 个人博客搭建教程——如何用github Pages＋Jekyll＋markdown搭建Blog

—— Make you different everyday

[https://pages.github.com](https://pages.github.com) 观看详细的视频教程

### 简单介绍

**github Pages**

> [github Pages](https://pages.github.com/) 托管你的静态网页

**MarkDown**

>  [Markdown入门指南](http://www.jianshu.com/p/1e402922ee32/) 
>   Markdown is a text-to-HTML conversion tool for web
>   writers.“Markdown” is two things: (1) a plain text formatting syntax; 
>   and (2) a software tool, written in Perl, that converts the plain text
>   formatting to HTML.简单的说，它替你排版，让你更专注写作 

**Jekyll**

>  [Jekyll](http://jekyllrb.com/) Simple, blog-aware, static site generator.
>   静态网站产生器，有丰富的主题模版供你使用

### 准备工作

github Pages相关

* [注册Github](http://www.github.com/)帐号
* 配置SSH keys,让本地git项目与远程的github建立联系
* 本地安装git,[git教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137396287703354d8c6c01c904c7d9ff056ae23da865a000)

Jekyll相关

* 本地安装

```
$ gem install jekyll bundler
$ gem install jekyll-paginate
```

Markdown相关

* 网站项目开发环境：[Atom](https://atom.io/) 
* Markdown编辑环境：Sublime3
安装Sublime3下两款Markdown插件，[安装教程](http://www.jianshu.com/p/335b7d1be39e)
  1. **MarkdownEditing** : 高亮显示Markdown语法
  2. **OmniMarkupPreviewer** : 预览markdown编辑的效果  
* 注册图床账号，用于保存图片，生成图片url


### 实例

>  下面演示如何操作

#### 第一步 创建项目

 首先在Github上创建新的储存库，命名为myblog

 拷贝到本地git（username为你的Github账户名）

```
$ git clone https://github.com/username/myblog.git
```

 以下两种方式均可

  1. 不使用主题模版

```
$ jekyll new mysite           //创建一个jekyll文件夹
$ cd mysite
```

  2. [下载主题模板](http://jekyllthemes.org/)
     将模版里的内容拷贝到mysite文件夹下

 此时目录结构为：

```
/mysite
　　　　|--　_config.yml
　　　　|--　_posts
　　　　|...
```

config.yml为设置文件，在_post文件夹里加入自己写的网页（.md文件）

#### 第二步 创建一个没有父节点的分支gh-pages
（因为github规定，只有该分支中的页面，才会生成网页文件）

```
$ git checkout --orphan gh-pages
```

#### 第三步 修改名为_config.yml的设置文件

```
baseurl: "/mysite/"   //区分大小写
```

#### 第四步 到_post文件夹下创建blog页面，完成后执行jekyll

1. 写一个页面 (文件名必须为"年-月-日-文章标题.后缀名"的格式，可直接用 **sublime** 编辑然后上传)
 
```
~/mysite $ cd _post
~/_posts $ vim 2017-01-17-Hello-World.md 
```

在2017-01-17-Hello-World.md里编辑以下内容,然后保存

```
＃ Hello World
> 你好，世界！  
```

此时目录结构为：

```
/mysite
　　　　|--　_config.yml
　　　　|--　_posts
　　　　|　　　|--　2017-01-17-Hello-World.md  //新增
       |...
```

2. 回到mysite，执行jekyll
 
```
~/mysite $ bundle exec jekyll serve 
```

回车后出现以下内容：

```
B000000080184C:Blog $ bundle exec jekyll serve
Configuration file: /Users/Blog/_config.yml
Configuration file: /Users/Blog/_config.yml
            Source: /Users/Blog
       Destination: /Users/Blog/_site
 Incremental build: disabled. Enable with --incremental
      Generating... 
                    done in 0.504 seconds.
 Auto-regeneration: enabled for '/Users/Blog'
Configuration file: /Users/Blog/_config.yml
    Server address: http://127.0.0.1:4000/username/      　//复制此url
  Server running... press ctrl-c to stop.
```

复制 Server address: http://127.0.0.1:4000/Joyce-Ng/，在浏览器中打开预览网站效果

此时目录结构为：

```
/mysite
　　　　|--　_config.yml
　　　　|--　_posts
　　　　|　　　|--　2017-01-17-Hello-World.md  
       |-- _site
       |     |--　2017-01-17-Hello-World.html  //新增
       |...
```

#### 第五步 发布内容

```
$ git add .
$ git commit -m "first post"
```

#### 第六步 将本地内容推送到github上刚创建的库

```
$ git push -u origin gh-pages  //下一次推送则直接使用 git push
```

上传成功之后，访问http://username.github.io/mysite/就可以看到Blog已经生成了（将username换成你的用户名）。
