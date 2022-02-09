---
title: hexo博客写法
date: 2020-06-16 12:32:11
tags: 
	- hexo 
	- 标准
top: 1
---

该文记录博客的常用写法。

<!-- more -->
## 命令及作用

1. 创建新文章

``` bash
hexo new "My New Post"
```

2. 运行服务端

``` bash
hexo server
```

3. 生成静态文件

``` bash
hexo generate
```

4. 推送到远端站点

``` bash
hexo deploy
```

5. 增量更新

``` bash
hexo d -g
```


## 写作技巧
1.  为特定的文章配置特定的顶部图
方法：在文章  ` md ` 文件的头部，添加 `top_img` 项。文章的顶部图不会受主题配置的顶部图的影响。

2. 文章置顶
方法：在文章  ` md ` 文件的头部，添加 `top: True` 项。

3. 节选
添加 `<!-- more -->` 可替换成阅读更多。

## 添加图片
![test](/images/hexo_write/test.jpg)


