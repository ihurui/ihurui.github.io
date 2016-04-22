---
layout: post
title:  "记录安装Jekyll遇到的问题-切换ruby镜像源解决"
subtitle: "subtitle"
date:   2016-04-10 23:34:01
categories: [design, tool]
---

其实不是Jekyll的问题，是ruby的问题哈。

最近利用Github pages 打造一个个人站点，在Github pages官网上看到对Jekyll的推荐，查阅了一些资料，觉得Jekyll是个不错的博客内容输出工具，遂决定入坑。不过第一步就遇到了麻烦，在terminal中输入“ gem install jekyll"安装Jekyll时得到报错如下：
		
	ERROR: While executing gem ... 	(OpenSSL::SSL::SSLError)SSL_connect returned=1 errno=0 state=SSLv3 read server hello A: sslv3 alert handshake failure
	
从字面意思可以猜测出应该是网络问题，在网上searching了一下还在Jekyll的Github主页上添加了一个issue（结果被大神告知这不是Jekyll的问题是ruby的问题啊，捂脸逃～）。最后找到解决办法，将gem的镜像源改到淘宝镜像。

	gem sources --remove https://rubygems.org/
	gem sources -a https://ruby.taobao.org/
	
于是问题解决。
要注意的是，ruby版本最好在2.0以上，使用gem -v查看版本，gem update --system升级版本。另外不切换ruby镜像到淘宝的话，连升级ruby版本都是不行的。



	
		
	


