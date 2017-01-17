## 个人博客搭建教程——如何用github Pages＋Jekyll＋markdown搭建Blog

—— different everyday

### 简单介绍

**github Pages**
> [github Pages](https://pages.github.com/)托管你的静态网页

**MarkDown**
>  [Markdown](http://jekyllrb.com/) 简单易学，替你排版，专注写作 

**Jekyll**
>  [Jekyll](http://jekyllrb.com/) 静态网站产生器

### 准备工作
* 注册Github帐号
* 本地下载git
* 等等

### 实例

>  下面就来演示如何在github上搭建Blog吧

#### 第一步 创建项目
```
$ gem install jekyll bundler  //安装jekyll
$ jekyll new mysite           //创建一个jekyll文件夹
$ cd mysite
```

#### 第二步 对该目录进行git初始化，然后创建一个没有父节点的分支gh-pages（因为github规定，只有该分支中的页面，才会生成网页文件）
```
$ git init
$ git checkout --orphan gh-pages
```

#### 第三步 修改名为_config.yml的设置文件
```
baseurl: "mysite"
```

#### 第四步 到_post文件夹下创建blog页面，执行jekyll
```
~/mysite $ 
~/my-awesome-site $ jekyll build //产生静态网页
~/my-awesome-site $ jekyll serve //执行jekyll服务
```

#### 第五步 发布内容
```
$ git add *
$ git commit -m "first post"
```

#### 第六步
前往github的网站，在网站上创建一个名为jekyll_demo的库。接着，再将本地内容推送到github上你刚创建的库。注意，下面命令中的username，要替换成你的username。
```
$ git remote add origin https://github.com/username/jekyll_demo.git
$ git push origin gh-pages
```

上传成功之后，访问http://username.github.io/mysite/就可以看到Blog已经生成了（将username换成你的用户名）。
