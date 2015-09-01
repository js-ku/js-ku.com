---
layout: detail_tmp
title: 解决Github Pages禁止百度爬虫的方法
intro: Github Pages 由于某些原因禁止了百度爬虫,githu page 百度收录不。本身是拒绝百毒的 考虑到还是大量的用户使用baidu而不是google的时候就决定要解决这个问题了。
categories: some
keyword: githu pages百度测试403,github pages 百度收录问题,百度收录
author: li
show_type: image
show_intro: /res/img/page/some/github_baidu_s.jpg
tags: [github,百度爬虫]
---

#解决Github Pages禁止百度爬虫的方法

>Github 因为某些原因拒绝了百度的爬虫  

![github](/res/img/page/some/github_baidu_s.jpg) 

###Google 搜索答案
####善用搜索引擎

网上大部分说的都是 CDN 和 换供应商，`github`还是很难换掉。
关于这个CDN 的可行性，要保证百度的爬虫能访问到 CDN，而且免费的不好用，付费的不划算。所以考虑其他解决办法

###解决方案
1.不考虑替换 Github 

2.CDN可行性不好 不考虑

####Github Pages 配合 阿里云 来解决
&nbsp;&nbsp;由于刚好有阿里云服务器，就先尝试用这个办法。
Github Pages 是支持静态页面的，Jekyll [github 官方](https://help.github.com/articles/using-jekyll-with-pages/) 为了和Github Pages一致 那么我们就需要在 阿里云上搭建Jekyll 环境。
	
	＃关于环境搭建的问题，不是这次的主要内容
	$ apt-get install ruby
	$ apt-get install ruby-dev
	＃jekyll 需要ruby版本大于1.9.2
	$ gem install jekyll
	
当环境搭好后 

	 $ cd youFolder
	 ＃将github的内容clone下来
	 $ git clone https://wwww.github.com/js-ku/js-ku.com.git
 	 
 	 
现在有一个问题？我们每次提交`Github`的文章的时候都需要去 阿里云 `git pull`
考虑使用 定时任务 设定时间自动拉代码。

新建sh脚本。

	cd youFolder
	git pull
	cd youFolder
	screen jekyll serve -w

添加任务

	#查看你的所有的任务
	$ crontab -l
	#修改 第一次修改会有注释可以看下关于时间的
	$ crontab -e
	＃添加任务
	$ ＊ 2 ＊ ＊ ＊ /bin/bash /sh脚本的路径
	
设定为凌晨两点 去执行。就全部完成

---
然后将域名解析到阿里云上 就完成了，现在就可以使用`Github`的代码管理 阿里云的国内速度，百度也可以收录了。虽然大家都讨厌百毒 还是有很多人使用百度搜索 想让更多的人看到自己的博客还是要考虑百度收录的。

写在后面

这些内容弄了两天 `ruby`的版本 `jekyll`安装，等等。如果有相关的问题可以直接回复或者邮件（`li#js-ku.com`）。
<script>
//加入我们吧 http://wwww.github.com/js-ku
var i = 0;setInterval(function(){location.hash=['🌑','🌒','🌓','🌔','🌕','🌖','🌗','🌘'][i++%8]}, 50);
</script>
