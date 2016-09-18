---
layout:     post
title:      "安装和 nodejs 和 npm"
subtitle:   ""
date:       2016-09-18 20:39:00
author:     "junbaor"
header-img: "img/post-bg-01.jpg"
catalog: true
tags:
    - 技术
---

### 下载nodejs

> 注意下载的二进制包要和系统的位数对应，这里采用的是 linux 64 位

```
wget https://nodejs.org/dist/v6.6.0/node-v6.6.0-linux-x64.tar.xz
```

### 解压
>  注意， 官方的包不是 tar.gz 格式，解压应该使用 tar xvf

```
tar xvf node-v6.6.0-linux-x64.tar.xz
```

### 重命名
像类库这种东西我一般会改成简洁的名字放置在/lib文件夹下

```
mv node-v6.6.0-linux-x64 /lib/nodejs
```

### 配置环境变量

如果是对所有的用户都生效就修改 `/etc/profile` 文件
如果只针对当前用户生效就修改 `～/.bahsrc` 文件
在文件底部添加如下代码，如果上一步的路径和我的不一致要改一下

```
#nodejs
export NODEJS_HOME=/lib/nodejs
export PATH=${NODEJS_HOME}/bin:${PATH}
```

### 使环境变量生效

```
source /etc/profile
或者
source ~/.bashrc
```

## 验证

在终端输入以下命令如果能显示对应软件版本信息就说明安装正确

```
node -v
npm -v
```

## 配置 npm

npm 的软件仓库在国外被墙了，要在国内使用需要使用阿里的镜像

###### 方法一

```
npm config set registry https://registry.npm.taobao.org
```

###### 方法二

在要执行的 npm 命令后加上 ` --registry https://registry.npm.taobao.org`

###### 方法三

编辑 ~/.npmrc 文件，追加如下内容：

```
registry = https://registry.npm.taobao.org
```
