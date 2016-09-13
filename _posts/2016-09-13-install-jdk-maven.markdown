---
layout:     post
title:      "安装jdk和maven"
subtitle:   ""
date:       2016-09-13 16:35:00
author:     "junbaor"
header-img: "img/post-bg-01.jpg"
catalog: true
tags:
    - 技术
---

## 下载jdk和maven

```
wget http://yun.junbaor.com/file/jdk.tar.gz  
# oracle 1.8 版本，oracle官网下载链接需要登录，为了方便就自己放服务器上了一份
wget http://mirrors.hust.edu.cn/apache/maven/maven-3/3.3.9/binaries/apache-maven-3.3.9-bin.tar.gz
```

## 解压

```
tar zxvf jdk.tar.gz
tar zxvf apache-maven-3.3.9.bin.tar.gz
```

## 重命名
像类库这种东西我一般会改成简洁的名字放置在/lib文件夹下

```
mv jdk1.8.0_60/ /lib/jvm
mv apache-maven-3.3.9/ /lib/maven
```

## 配置环境变量

如果是对所有的用户都生效就修改 `/etc/profile` 文件

如果只针对当前用户生效就修改 `～/.bahsrc` 文件

在文件底部添加如下代码，如果上一步的路径和我的不一致要改一下

```
#jdk
export JAVA_HOME=/lib/jvm
export JRE_HOME=${JAVA_HOME}/jre   
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib   
export PATH=${JAVA_HOME}/bin:$PATH 
#maven
export MAVEN_HOME=/lib/maven
export PATH=${MAVEN_HOME}/bin:${PATH}
```

## 使环境变量生效

```
source /etc/profile
或者
source ~/.bashrc
```

## 验证

在终端输入以下命令如果能显示对应软件版本信息就说明安装正确

```
java -version
mvn -version
```
