---
title: elk日志管理搭建
catalog: true
date: 2021-07-15 15:02:27
#subtitle: 
lang: cn
header-img: /img/header_img/Iml_bg.jpg
tags:
- es
categories:
- es
---

## 概述
ELK 是三个开源软件的缩写，分别表示：Elasticsearch，Logstash，Kibana , 它们都是开源软件。新增了一个 FileBeat，它是一个轻量级的日志收集处理工具(Agent)，Filebeat 占用资源少，适合于在各个服务器上搜集日志后传输给 Logstash，官方也推荐此工具。

Elasticsearch 是个开源分布式搜索引擎，提供搜集、分析、存储数据三大功能。

Logstash 主要是用来日志的搜集、分析、过滤日志的工具，支持大量的数据获取方式。一般工作方式为 c/s 架构，client 端安装在需要收集日志的主机上，server 端负责将收到的各节点日志进行过滤、修改等操作在一并发往 elasticsearch 上去。

Kibana 是一个开源和免费的工具，Kibana 可以为 Logstash 和 ElasticSearch 提供的日志分析友好的 Web 界面，可以帮助汇总、分析和搜索重要数据日志。

Filebeat 是一个轻量级的日志收集处理工具

## 搭建步骤

### 在服务器上安装es
[参考文章](https://www.cnblogs.com/wangzhuxing/p/9351245.html)

按照博客步骤下载安装，并修改config中的文件

在bin目录下输入 ./elasticsearch -d可以后台运行es，输入curl localhost:配置文件中设置的端口  显示以下界面表示es已经部署成功（注意对照name和cluster_name是不是配置文件中设置的）

### 在服务器上安装logstash
[参考文章](https://elasticsearch.cn/article/6141)
在config目录下新建一个logstash.conf 进行配置
