---
layout: post
title: "Github Pages + Jekyll"
date: 2020-01-13 15:40:33 +0800
featured-img: emile-perron-190221
published: false
---
# Github Pages

> **Websites for you and your projects.**<br>
> Hosted directly from your <u>GitHub repository</u>. Just edit, push, and your changes are live.

Github Pages是一个静态站点托管服务，可直接从 Github 上的仓库中获取 HTML, CSS 和 JavaScript 文件。通过构建服务处理并发布以供访问<br>
[Github Pages Examples](https://github.com/collections/github-pages-examples)

## 站点类型

Github Pages 可以为我们提供三种站点类型，我们可以根据需要来选择。

| 站点类型 | 站点发布地址 | 构建站点的个数 |
| ------- | ---------- | ----------- |
| 用户 | http(s)://`<user>`.github.io | 1 |
| 组织 | http(s)://`<organization>`.github.io | 1 |
| 项目 | http(s)://`<user/organization>`.github.io/`<repository>` | 不限制 |

## 构建方式

### 构建用户或组织站点

  1、创建仓库

  **用户或组织**类型的站点创建成功后 Github Pages 服务就**自动构建**仓库内容**发布**在 http(s)://`user`.github.io/ 或 http(s)://`organization`.github.io/

  ![Create new repository](https://i.loli.net/2020/01/15/TQABro1NXRp5tKc.png)

  **`Tip`**: 仓库的名称必须和当前用户或组织的名称一致，否则这个站点则不会生效。

  2、添加内容测试站点情况

  2.1、Clone 仓库

  ```shell
  git clone https://github.com/username/username.github.io
  ```

  2.2、Hello World

  ```shell
  cd username.github.io
  echo "Hello World" > index.html
  ```

  2.3、Push 改动的内容到远程库

  ```shell
  git add --all
  git commit -m "Initial commit"
  git push -u origin master
  ```

  2.4、完成所有步骤，在浏览器中输入 **`https://username.github.io`** 访问查看

### 构建项目站点

1、创建仓库

进入 [Github.com](https://github.com/) 创建新的仓库，如果想对现有仓库进行构建的话，点击仓库的设置选项进入设置


2、添加Hello World

通过 GitHub 的编辑功能创建 `index.html` 文件，并添加一些内容<br>
![Create new file](https://pages.github.com/images/new-create-file@2x.png)

![Hello World](https://pages.github.com/images/new-index-html@2x.png)

提交新增的内容到仓库

![Commit new file](https://pages.github.com/images/new-commit-file@2x.png)

3、设置仓库属性中 Github Pages 相关配置进行发布

点击设置选项卡向下滚动到 Github Pages 选项卡，选择一个分支进行发布。
![Setting repository](https://i.loli.net/2020/01/15/nod86hfA14FVINQ.png)

![Github_pages_setting.jpeg](https://i.loli.net/2020/01/15/puRIxmodlQ6NLhZ.jpg)

如果要取消发布我们的站点，配置 Github Pages 的 Source 分支为 None 就可以了

**`Tip：`**关于发布的分支有一点建议，官方建议我们新建一个专门用来发布内容的分支。例：`gh-pages`, 主要原因我觉得因为有[几点限制](https://help.github.com/en/github/working-with-github-pages/about-github-pages#guidelines-for-using-github-pages)，如果我们在发布分支上频繁提交，每次提交服务就会自动构建站点内容，超过限制就不会更新站点内容了。

* Github Pages 服务每个月带宽限制为 100GB
* Github Pages 服务每个小时最高可以构建 10 次

# Jekyll

> Jekyll 是一个简单的博客形态的静态站点生产机器。它有一个模版目录，其中包含原始文本格式的文档，通过一个转换器（如 [Markdown](https://daringfireball.net/projects/markdown/)）和我们的 Liquid 渲染器转化成一个完整的可发布的静态网站，你可以发布在任何你喜爱的服务器上。Jekyll 也可以运行在 GitHub Page 上，也就是说，你可以使用 GitHub 的服务来搭建你的项目页面、博客或者网站，而且是完全免费的。

了解了 Jekyll 是为我们生成静态站点的工具，而且 Github Pages 默认的构建工具就是 Jekyll 。比如说我们构建自己的博客就不用从头开始编写主题样式、接入分析等等，直接将生成的站点放在 Github repository 中就可以。自己专注写文章就好。

## 环境配置

因为 Jekyll 是基于 Ruby 的静态网站生成系统，所以我们首先需要安装 Ruby 环境，参考 [Ruby官方安装文档](https://www.ruby-lang.org/en/documentation/installation/)

检查环境是否满足：

Ruby 环境
```shell
ruby -v
```

RubyGems Ruby 的包管理工具
```shell
gem -v
```

## 安装 Jekyll

```shell
gem install jekyll bundler
```

## 创建 Jekyll Demo

创建一个存放站点内容的目录 `./myblog`。

```shell
jekyll new mybloy
cd myblog
bundle exec jekyll serve
```

现在我们就创建了一个静态站点，并且运行在 [http://localhost:4000](http://localhost:4000), 打开浏览器访问吧。

<!-- ## 配置主题

```shell
myblog
├── 404.html
├── Gemfile
├── Gemfile.lock
├── _config.yml
├── _posts
│   └── 2020-01-09-welcome-to-jekyll.markdown
├── _site
│   ├── 404.html
│   ├── about
│   │   └── index.html
│   ├── assets
│   │   ├── main.css
│   │   ├── main.css.map
│   │   └── minima-social-icons.svg
│   ├── feed.xml
│   ├── index.html
│   └── jekyll
│       └── update
│           └── 2020
│               └── 01
│                   └── 09
│                       └── welcome-to-jekyll.html
├── about.markdown
└── index.markdown
``` -->

# 参考

[Github Pages](https://pages.github.com)<br>
[Github Help / Working with GitHub Pages](https://help.github.com/en/github/working-with-github-pages)
