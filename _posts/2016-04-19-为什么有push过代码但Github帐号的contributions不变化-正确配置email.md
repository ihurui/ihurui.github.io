---
layout: post
title:  "为什么有push过代码但Github帐号的contributions不变化"
subtitle: "正确配置email了吗"
date:   2016-04-19 15:34:01
categories: [design, tool]
---

今天看Github自己的主页，发现contributions竟然还是3，最长连续提交记录只有一天！想想自己这么多天做个人主页几乎天天都有push啊，心都碎了～。为啥没有记录？！看contributions下面一行链接[Learn how we count contributions](https://help.github.com/articles/why-are-my-contributions-not-showing-up-on-my-profile/),里面有详细介绍怎样才被记录到contributions，我自己简单翻译了一下。

## 记录push到contributions的规则

### Issues and pull requests
Issues和pull requests被记录到contributions如果它们满足如下两个要求：

* 在去年创建（毕竟contributions本来就是记录的过去一年的）
* 在一个独立的repository中创建，而不是fork的

### Commits
commits 满足以下条件会被记录到contributions：

* 在去年一年内提交（同理）
* email地址和Github帐号绑定的邮箱地址一样（我就是在这里被坑了。。）
* commits是由一个独立的repository中提交的，非fork的
* commits还必须是repository的默认分支，一般是master，或者是Github pages分支（一般做个人主页，但我个人主页用的是master。。）

检查了一下我git commit的时候response，信息如下：


		Committer: 胡睿 <hurui@huruideMBP.lan>
		Your name and email address were configured automatically based on your username and hostname. Please check that they are accurate.


都是自己平时提交后就万事大吉不看返回信息的锅啊（虽然记得本机上git全局配置的用户名和邮箱都正确设置过啊～），但是错过的提交已经错过了，就当吸取个教训了。使用

		
		git config --local user.name "github帐号名"  
		git config --local user.email github帐号绑定邮箱地址
		
 
 配置正确用户名和邮箱后，再次push，刷新Github主页后可以看到contributions增加了。

