---
layout:     post
title:      "mysql的安装与常见配置"
subtitle:   ""
date:       2015-05-05 23:00:00
author:     "junbaor"
header-img: "img/post-bg-01.jpg"
catalog: true
tags:
    - 技术
    - mysql
---

### 更新
```
apt-get update
apt-get upgrade
```

### 安装
`apt-get install mysql-server`

会提示输入`root`用户的密码

### 修改编码

SHOW VARIABLES LIKE 'character_set_%'; #查看编码;

修改 `vim /etc/mysql/my.cnf` 文件

在 [mysqld] 标签下加
```
character-set-server = utf8
collation-server = utf8_general_ci
init_connect = 'SET collation_connection = utf8_general_ci'
init_connect = 'SET NAMES utf8'
lower_case_table_names = 1  #表名大小写不敏感
```

在 [mysql.server]标签下加
```
default-character-set = utf8
```

在 [mysqld_safe]标签下加
```
default-character-set = utf8
```

在 [client]标签下加
```
default-character-set = utf8
```

如果想让其他机子远程也可以登陆需要把这句注释掉(前面加`#`)
```
bind-address        = 127.0.0.1
```

### 开启`root`的远程登录权限

首先应确保 mysql 服务处于开启状态,然后进入 mysql 终端，执行以下命令

```
Grant all privileges on *.* to 'root'@'%' identified by 'root' with grant option;
把后面的 `root` 替换成你自己的密码
flush privileges; #刷新一下权限
```

### 修改账户密码
```
UPDATE mysql.user SET password=PASSWORD('root') WHERE user='root';
把前面的 `root`替换成用户名 ,后面的 `root` 替换成密码即可
`flush privileges;`
```

