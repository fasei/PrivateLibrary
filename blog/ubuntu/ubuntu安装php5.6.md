---
title: ubuntu安装php5.6
tags: [docker,wanc镜像版本]
date: 2018-12-07
categories: docker
---

ubuntu中不能直接安装php5.6

<!--more-->

## 卸载php7.0
```
sudo apt-get autoremove php7*
```

## 安装相关软件

使用ppa增加源:
```
sudo apt-get install  software-properties-common
apt-get update
//如果下面的命令有问题，重复执行上2条命令
sudo add-apt-repository ppa:ondrej/php  
sudo apt-get update 
sudo apt-get -y install php5.6 php5.6-mcrypt php5.6-mbstring php5.6-curl php5.6-cli php5.6-mysql php5.6-gd php5.6-intl php5.6-xsl php5.6-zip
```


sudo apt-get -y install php5.2 php5.2-mcrypt php5.2-mbstring php5.2-curl php5.2-cli php5.2-mysql php5.2-gd php5.2-intl php5.2-xsl php5.2-zip
再用php -v查看当前版本



