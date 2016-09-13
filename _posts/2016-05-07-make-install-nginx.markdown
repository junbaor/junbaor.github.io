---
layout:     post
title:      "编译安装nginx"
subtitle:   ""
date:       2016-09-13 16:53:00
author:     "junbaor"
header-img: "img/post-bg-01.jpg"
catalog: true
tags:
    - 技术
---

### 更新 apt

```
apt-get update
apt-get upgrade
```

### 编译 nginx 需要用到 gcc pcre gzip,先安装这些依赖库

```
apt-get install -y gcc libpcre3 libpcre3-dev libpng-dev
```

### 下载nginx包,解压后编译

```
wget http://nginx.org/download/nginx-1.10.1.tar.gz
tar zxvf nginx-1.10.1.tar.gz
cd nginx-1.10.1.tar.gz
./configure  #在 configure 可以加一些参数，在文末列出
```

### 编译并安装

```
make && make install
```

到这一步就已经安装完成了

默认安装在 /usr/locale/nginx

里面有四个目录：

* conf: 配置文件夹，最重要文件是 nginx.conf
* html: 静态网页文件夹
* logs: 日志文件夹
* sbin: nginx 的可执行文件，启动、停止等操作

***

### 启动

```
cd /usr/locale/nginx/sbin
./nginx
```

启动后，就可以访问自己机子的ip了，会出现一个欢迎网页

### 停止

```
cd /usr/locale/nginx/sbin
./nginx -s quit
或者
./nginx -s stop
```

### 重启

```
cd /usr/locale/nginx/sbin
./nginx -s reopen
```

### 检查配置文件是否有错误

```
cd /usr/locale/nginx/sbin
./nginx -t
```

重新加载配置文件，加载时会检查配置文件的正确性，如果正确会慢慢替换掉旧进程，反之，则不加载配置文件

```
cd /usr/locale/nginx/sbin
./nginx -s reload
```

### 加入开机自启： vim /etc/rc.local
在exit 0前加入nginx命令的路径
例如：

```
/usr/locale/nginx/sbin/nginx
```

### 常用编译参数：

```
--prefix= 指向安装目录
--sbin-path 指向（执行）程序文件（nginx）
--conf-path= 指向配置文件（nginx.conf）
--error-log-path= 指向错误日志目录
--builddir= 指向编译目录
--with-ipv6 启用ipv6支持
--with-http_sub_module（允许用一些其他文本替换nginx响应中的一些文本）
--with-http_ssl_module 启用ngx_http_ssl_module支持（使支持https请求，需已安装openssl）
```

