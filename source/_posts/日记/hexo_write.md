---
title: 博客启动！
date: 2021-06-16 12:32:11
top: 999
tags: 
	- hexo
categories:
	- 博客
---

blog.mornw.com!
<!-- more -->

# 为什么写博客？

看见舍友的网站是在是好看，羡慕之余，自然也想自己做一个。

# 做个什么样的网站？

问：越简单越好不是吗？
答：轻量级博客，静态网站、方便的整理自己的文章。让我找到了HEXO。

问：需要评论功能吗？
答：不需要，也没人看不是吗（当然我也想让人看啦！T.T）

问：图床用什么呀？
答：我是十分倾向于选择 github 的，很多人都说 github 访问速度慢，目前就使用 CDN 加速吧。

# 开始博客搭建

想写博客，当然是先搭建图床啦！

### 1. 图床

1. 在 github 上创建一个公开的图床仓库。

2. 下载 PicGO。
 - github 生成自己的 token 时，需要勾选 repo 项。
  ![](https://raw.githubusercontent.com/onlywant/blog_img/main/img/hexo_write/20220211152431.png)

  - 设置 CDN 加速
 ![](https://cdn.jsdelivr.net/gh/onlywant/blog_img/img/hexo_write/20220211153922.png)

### 2. 安装 hexo + hexo-theme-melody

1. 在 github 上创建一个 github pages。
 比如我的是： onlywant.github.io

2. 安装 nodejs 和 npm。

3. 创建一个博客文件夹

4. ```npm install hexo --save```

5. ```npm install hexo-theme-melody --save```

6. 即可使用`hexo -g && hexo -s`，生成自己的博客，本地查看。

7. 推送到远端仓库
	- 设置博客根目录中的`_config.yml`中的`deploy`项为自己的 github pages 地址。
 ![](https://cdn.jsdelivr.net/gh/onlywant/blog_img/img/hexo_write/20220211154803.png)

	- 即可使用`hexo -d`推送到远端。

### 3. 使用github actions自动编译发布网站
1. 在 github 上创建 blog 源代码仓库，上传自己的源代码。
![](https://cdn.jsdelivr.net/gh/onlywant/blog_img/img/hexo_write/20220211155536.png)

2. 设置两个仓库的沟通桥梁
	- 使用 ssh-keygen 生成一对公私钥。
	- 在源代码仓库`settings->secrets->actions`中添加 `HEXO_DEPLOY_PRI`，内容为私钥。
	![](https://cdn.jsdelivr.net/gh/onlywant/blog_img/img/hexo_write/20220211160209.png)
	- 在 pages 仓库`settings->deploy keys`中添加 `HEXO_DEPLOY_PUB`， 内容为公钥。
	![](https://cdn.jsdelivr.net/gh/onlywant/blog_img/img/hexo_write/20220211160502.png)

3. 在仓库根目录下添加`.github/workflow/deploy.yml`文件。内容如下：
	```
	name: CI

	on:
	push:
		branches:
		- master

	env:
	GIT_USER: 你的名字
	GIT_EMAIL: 你的email地址
	DEPLOY_REPO: 推送到的仓库
	DEPLOY_BRANCH: 仓库分支

	jobs:
	build:
		name: Build on node ${{ matrix.node_version }} and ${{ matrix.os }}
		runs-on: ubuntu-latest
		strategy:
		matrix:
			os: [ubuntu-latest]
			node_version: [12.x]

		steps:
		- name: Checkout
			uses: actions/checkout@v2

		- name: Checkout deploy repo
			uses: actions/checkout@v2
			with:
			repository: ${{ env.DEPLOY_REPO }}
			ref: ${{ env.DEPLOY_BRANCH }}
			path: .deploy_git

		- name: Use Node.js ${{ matrix.node_version }}
			uses: actions/setup-node@v1
			with:
			node-version: ${{ matrix.node_version }}

		- name: Configuration environment
			env:
			HEXO_DEPLOY_PRI: ${{secrets.HEXO_DEPLOY_PRI}}
			run: |
			sudo timedatectl set-timezone "Asia/Shanghai"
			mkdir -p ~/.ssh/
			echo "$HEXO_DEPLOY_PRI" > ~/.ssh/id_rsa
			chmod 600 ~/.ssh/id_rsa
			ssh-keyscan github.com >> ~/.ssh/known_hosts
			git config --global user.name $GIT_USER
			git config --global user.email $GIT_EMAIL
		- name: Install dependencies
			run: |
			npm install
		- name: Deploy hexo
			run: |
			npm run clean
			npm run build
			npm run deploy
	```

