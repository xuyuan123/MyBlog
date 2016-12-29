---
title: 利用Hexo博客搭建全过程
toc: true
date: 2016-03-05 11:50:35
author: XuYuan
categories: hexo
tags: [hexo, github]

---

这篇文章记录了这个博客平台的整个搭建过程，仅留做记录，供自己以后参考。
<!--more-->



## 准备工作：安装git，node.js和hexo
- 进入[git for windows官网](https://git-for-windows.github.io/)并下载git for windows安装包,安装git到自己电脑上。安装完成后在鼠标右键中可以看到多了个Git Bash选项。
- 进入[node.js官网](https://nodejs.org/en/)，并下载安装包，直接安装即可。
- 在电脑任何位置右击鼠标，选择Git Bash，在弹出的命令提示框中输入下面命令：  
    ```
    npm install -p hexo
    ```

- 安装文本文件编辑器，推荐**sublime text**或者**notepad++**。或者使用网页版的[作业部落](https://www.zybuluo.com/cmd/)作为博客文章的书写编辑工具。

## 注册github帐号并新建仓库
- 进入[github的官方网站](https://github.com/)，输入username，email和passward点击Sign up for Github进行注册并登录进去。
- 注册完成后登录进入自己的github页面，选择`+New repository`新建一个仓库，仓库名字为`username.github.io`，其中`username`改为你自己注册的时候的用户名。仓库名字必须按照这样的格式书写，这个仓库用来存放搭建网站所需文件。
- 同理再新建一个仓库，名字命名为MyBlog。这个仓库主要是用来存放博客文件的地方。这个仓库的名字可以随便取任何名字都可以。

## 初始化和配置hexo和github
- 首先需要设置和添加`SSH key`，打开电脑的命令行，或者直接使用鼠标右键中的Git Bash。在命令行中输入下面命令：  
    ```
    ssh-keygen -t rsa -C "your_email@example.com"
    ```
-  运行上面的命令后会提示让你输入生成文件的地址和文件名，直接回车，按照默认设置，就会在默认路径生成的`SSH key`文件：`id_rsa` 和 `id_rsa.pub`，还会提示让输入密码，可以不用填写，直接回车。用文本编辑器打开文件，复制其中的全部代码到剪贴板。
- 在[Github网站](https://github.com/)上登录进去自己的Github账户页面，选择setting选项中的`SSH keys`，选择`New SSH key`，将刚才复制到剪贴板上的内容粘贴到要添加的`SSH key`上面添加即可。
- 在本地电脑命令行中输入下面命令即可查看'ssh key'是否设置成功。
    ```
    ssh -T git@github.com
    ```
- 在电脑任意位置克隆仓库到本地，运行下面命令，将之前新建的MyBlog仓库克隆志本地电脑。
    ```
    git clone https://github.com/username/MyBlog.git/
    ```
- 在MyBlog中新建一个文件夹hexo，并进入到该文件夹内，打开Git Bash，运行下面命令。
    ```
    hexo init
    npm install
    npm install-deployer-git  --save
    ```
- 在该文件夹中继续执行如下命令，进行初始化提交。
    ```
    hexo g
    hexo s
    ```
    然后打开本地浏览器输入 `localhost:4000` ，查看预览效果。
- 在hexo文件夹中配置deployer信息。用文本编辑器打开hexo文件夹中的.yml文件，在最下面的deploy信息中输入以下内容，并保存。
    ```
    deploy:
        type: git
        repository: https://github.com/yourUsername/yourUsername.github.io.git
        branch: master
    ```
- 在hexo文件夹中打开Git Bash，输入以下命令。
    ```
    hexo g
    hexo d
    ```
    电脑会弹出提示框，提示输入github账户的用户名和密码。之后就会显示提交成功。
- 提交成功之后在浏览器中打开 `用户名.github.io` 这个地址，即可看到自己的网页。

## 创建博客文章，并提交到网站
- 在hexo文件夹中打开命令提示符，输入下面命令即可在`hexo\source\post`文件夹中生成`firstBlog.md`文件。
    ```
    hexo n "firstBlog.md"
    ```
- 用文本编辑器打开生成的`firstBlog.md`文件，参照**MarkDown**语法修改文章内容，然后保存即可。（也可直接使用编辑器新建后缀名为`.md`的文件,放在上述文件夹中即可）
- 参照第三部分内容，使用下面两条命令即可将本地编写的Blog文件提交到自己的个人网站。
    ```
    hexo g
    hexo d
    ```
- 在浏览器中打开自己的个人网页：`username.github.io`，查看确认自己的博客文章的提交效果。

## 申请自己的域名，并绑定到自己的github帐号
- 通过以上步骤基本上就建立了自己的一个博客网页，但是网址是github的一个二级域名，如果要想绑定一个自己独有的域名，就需要自己先购买一个自己的个人域名。
- 购买域名，首选Godday，不同域名价格不同，首选`.com`，`.me`，`.net`域名，可以使用支付宝付款。
- 如果只是个人使用，随便拿来玩一玩的话，还有很多免费的域名，就像本博客的`.cf`域名，还有类似的`.ga`，`.gq`，`.tk`等域名。
- 免费域名申请。进入[Freenom网站](http://www.freenom.com/zh/index.html?lang=zh)，输入名字，搜索域名是否可用，该网站支持`.ga`，`.gq`，`.tk`，`.ml`,`.cf`五种免费的顶级域名。
- 搜索到合适的免费域名之后，就可以直接在该网站免费申请注册。申请成功之后进入到自己账户中就可以管理该域名，我们使用DNSpod进行域名解析服务，在该域名的后台管理的nameserver中输入下面两个服务器解析地址：
	> f1g1ns1.dnspod.net
	> f1g1ns2.dnspod.net
- 进入[DNSpod官网](https://www.dnspod.cn/)，注册自己的一个账号。登陆进入自己的账号，选择域名管理，添加域名。输入刚刚申请到的域名，在该域名下添加下面两条记录。
	```
	主机记录		记录类型		记录值
	@		CNAME		username.github.io
	www		CNAME		username.github.io
	```
- 在自己博客的hexo中的source文件夹下，添加一个文本文件，名字为CNAME，没有后缀名，在文本文件中输入你自己的网站域名。例如：
	> xuyuan.cf
- 在浏览器中输入你新申请注册的个人网站域名，即可指向到你的个人博客网站。

## 修改配置文件
- 站点的配置文件是`\hexo`根目录中的：`_config.yml`文件。该文件内容及详细解释如下：
```
# Site 站点信息
title: XuYuan's Blog #网站题目
subtitle: Learning and Sharing  #网站子标题
description: Learning and Sharing  #网站描述
author: XuYuan  #作者
language: zh-Hans  #语言
timezone:
email: xjtuxuyuan@gmail.com

# URL 网站链接
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: xuyuan.cf  #网站链接
root: /
permalink: :year/:month/:day/:title/
permalink_defaults:

# Directory 文件目录
source_dir: source
public_dir: public
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code
i18n_dir: :lang
skip_render:

# Writing 写博客的配置
new_post_name: :title.md # File name of new posts
default_layout: post
titlecase: false # Transform title into titlecase
external_link: true # Open external links in new tab
filename_case: 0
render_drafts: false
post_asset_folder: false
relative_link: false
future: true
highlight:
  enable: true
  line_number: true
  auto_detect: false
  tab_replace:

# Category & Tag 归档和标签
default_category: uncategorized
category_map:
tag_map:
archive: 1
categories: 1
tag: 1

# 服务器设置
port: 4000
logger: false
logger_format:

# Date / Time format 日期和时间
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: YYYY-MM-DD
time_format: HH:mm:ss

# Pagination 分页设置
## Set per_page to 0 to disable pagination
per_page: 5  #每页显示的文章数目
pagination_dir: page

# Extensions 插件和主题
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: next  #博客主题
avatar: /images/logo.png #头像logo
duoshuo_shortname: xylpp # 添加多说评论
baidu_analytics: 2ea32e6cab4b74ce10e61cfc209c8cac  # 添加百度统计

# Deployment 部署配置
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repository: https://github.com/xuyuan123/xuyuan123.github.io.git
  branch: master

```

## 更换主题，美化网页
- 本博客使用的诗next主题，使用其他主题的方法类似。
- 首先从GitHub下载next主题，进入`hexo`文件夹，打开Git Bash，输入下面命令：
```
git clone https://github.com/iissnan/hexo-theme-next themes/next
```
- 更改站点配置文件`hexo\_config.yml`文件，将其中的theme字段设置为next
```
theme: next
```

- 美化主题主要是通过修改`hexo\theme\_config.yml`文件，来实现对主题的自定义修改。下面是我自己的`_config.yml`文件：
```
# ---------------------------------------------------------------
# Site Information Settings
# ---------------------------------------------------------------

# Place your favicon.ico to /source directory.
favicon: /favicon.ico  #网站图标，放在source根目录里

# Set default keywords (Use a comma to separate)
keywords: "Hexo, NexT" #关键字

# Set rss to false to disable feed link.
# Leave rss as empty to use site's feed link.
# Set rss to specific value if you have burned your feed already.
rss:

# Specify the date when the site was setup
since: 2016  #网站建立时间

language: zh-hk  #网站语言


# ---------------------------------------------------------------
# Menu Settings  菜单设置
# ---------------------------------------------------------------

# When running hexo in a subdirectory (e.g. domain.tld/blog)
# Remove leading slashes ( "/archives" -> "archives" )
menu:  #菜单对应文件夹
  home: /
  #categories: /categories
  archives: /archives
  about: /about
  tags: /tags
  #commonweal: /404.html


# Enable/Disable menu icons.
# Icon Mapping:
#   Map a menu item to a specific FontAwesome icon name.
#   Key is the name of menu item and value is the name of FontAwsome icon.
#   When an question mask icon presenting up means that the item has no mapping icon.
menu_icons:  #菜单图标
  enable: true
  # Icon Mapping.
  home: home
  about: user
  categories: th
  tags: tags
  archives: archive
  commonweal: heartbeat

# ---------------------------------------------------------------
# Scheme Settings
# ---------------------------------------------------------------

# Schemes  #主题方案设置
#scheme: Muse
scheme: Mist
#scheme: Pisces



# ---------------------------------------------------------------
# Sidebar Settings  侧边栏设置
# ---------------------------------------------------------------


# Social links  #社交链接
# social:
  #GitHub:
  #Others:

# Social Icons  #社交链接图标
social_icons:
  enable: true
  # Icon Mappings
  GitHub: github
  Twitter: twitter
  Weibo: weibo


# Sidebar Avatar  #侧边栏头像
# in theme directory(source/images): /images/avatar.jpg
# in site  directory(source/uploads): /uploads/avatar.jpg
# default : /images/default_avatar.jpg
# avatar: /images/logo.png


# TOC in the Sidebar  #侧边栏里的文章目录显示设置
toc:
  enable: true

  # Automatically add list number to toc. #是否自动为文章目录添加序号
  number: true


# Creative Commons 4.0 International License.
# http://creativecommons.org/
# Available: by | by-nc | by-nc-nd | by-nc-sa | by-nd | by-sa | zero
#creative_commons: by-nc-sa
#creative_commons:

sidebar:
  # Sidebar Position, available value: left | right  #侧边栏位置设置
  position: left
  #position: right

  # Sidebar Display, available value:
  #  - post    expand on posts automatically. Default.
  #  - always  expand for all pages automatically
  #  - hide    expand only when click on the sidebar toggle icon.
  #  - remove  Totally remove sidebar including sidebar toggle icon.
  display: post
  #display: always
  #display: hide
  #display: remove



# ---------------------------------------------------------------
# Misc Theme Settings
# ---------------------------------------------------------------

# Custom Logo.
# !!Only available for Default Scheme currently.
# Options:
#   enabled: [true/false] - Replace with specific image
#   image: url-of-image   - Images's url
custom_logo:
  enabled: false
  image:


# Code Highlight theme #代码高亮设置
# Available value:
#    normal | night | night eighties | night blue | night bright
# https://github.com/chriskempson/tomorrow-theme
highlight_theme: normal

# Automatically scroll page to section which is under <!-- more --> mark.
scroll_to_more: true

# Automatically Excerpt
auto_excerpt:
  enable: false
  length: 150

# Use Lato font
use_font_lato: true



# ---------------------------------------------------------------
# Third Party Services Settings
# ---------------------------------------------------------------

# MathJax Support  #mathjax的支持
mathjax: true


# Swiftype Search API Key #站内搜索swiftype设置
swiftype_key: RoCKZsAXr9rYSEazsP_2


# Baidu Analytics ID  #百度统计设置
baidu_analytics: 2ea32e6cab4b74ce10e61cfc209c8cac

# Duoshuo ShortName #多说评论设置
duoshuo_shortname: xylpp

# Disqus
#disqus_shortname:

# Baidu Share
# Available value:
#    button | slide
#baidushare:
##  type: button

# Share
#jiathis:
#add_this_id:

# Share
#duoshuo_share: true

# Google Webmaster tools verification setting
# See: https://www.google.com/webmasters/
#google_site_verification:


# Google Analytics
#google_analytics:


# Make duoshuo show UA
# user_id must NOT be null when admin_enable is true!
# you can visit http://dev.duoshuo.com get duoshuo user id.
duoshuo_info:
  ua_enable: true
  admin_enable: false
  user_id: 0
  #admin_nickname: ROOT


# Facebook SDK Support.
# https://github.com/iissnan/hexo-theme-next/pull/410
facebook_sdk:
  enable: false
  app_id:       #<app_id>
  fb_admin:     #<user_id>
  like_button:  #true
  webmaster:    #true


# Show number of visitors to each article.
# You can visit https://leancloud.cn get AppID and AppKey.
leancloud_visitors:
  enable: false
  app_id: #<app_id>
  app_key: #<app_key>


# Tencent analytics ID
# tencent_analytics:

#! ---------------------------------------------------------------
#! DO NOT EDIT THE FOLLOWING SETTINGS
#! UNLESS YOU KNOW WHAT YOU ARE DOING
#! ---------------------------------------------------------------

# Motion
use_motion: true

# Fancybox
fancybox: true

# Static files
vendors: vendors
css: css
js: js
images: images

# Theme version
version: 0.5.0

```

- **注意**：`_config.yml`文件中，每个选项后的冒号后面要有一个空格，再跟上对应的值。

## 让你的网站支持LaTeX编辑的数学公式
- 对于**Next**主题，默认是支持使用Mathjax来对数学公式的显示。
- 首先需要在主题的配置文件`hexo\theme\_config.yml`中设置；
```
mathjax: true
```
- 然后只需要在每次写文章时，在文章最前面的title下面添加下面一条语句：
```
mathjax: true
```
- 这样可以控制哪篇文章需要加载mathjax，哪篇不需要加载。因为加载mathjax需要耗费一些时间，所以这样的好处可以提高一些没有数学公式的网页的加载速度，只在有数学公式的网页中加载mathjax。
- 对于其他主题的mathjax的支持，可以参考这篇文章：[在 Hexo 中完美使用 Mathjax 输出数学公式](http://lukang.me/2014/mathjax-for-hexo.html)














-------
**参考文章：**
1. [使用Hexo搭建个人博客(基于hexo3.0)](http://opiece.me/2015/04/09/hexo-guide/)
2. [hexo系列教程：（一）hexo介绍](http://zipperary.com/2013/05/28/hexo-guide-1/)
3. [Hexo插件安装](http://luuman.github.io/2015/12/27/Hexo-plug/)
4. [Hexo 优化与定制(一)](http://lukang.me/2014/optimization-of-hexo.html)


