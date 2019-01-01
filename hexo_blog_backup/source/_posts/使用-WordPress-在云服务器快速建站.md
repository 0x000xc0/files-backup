---
title: 使用 WordPress 在云服务器快速建站
date: 2019-01-01 15:06:27
tags: 记录小结
---
> 阿里云可以直接使用 WordPress，本博文教程使用虚拟机（Ubuntu）当作 ECS 云服务器，从零开始建站。

> 参考：
1、 [WordPress 官方中文文档](https://codex.wordpress.org/zh-cn:Main_Page)
2、 [阿里云服务器使用教程，新手上云必备功课](https://yq.aliyun.com/articles/680675?spm=a2c4e.11155472.0.0.ffd460c7YeHPNs)
3、 [建站零基础入门（阿里云）](https://help.aliyun.com/document_detail/63819.html?spm=a2c4g.11186623.6.874.57c74cc1dj0fps)
4、 [手动建站方式汇总（阿里云）](https://help.aliyun.com/document_detail/57160.html?spm=a2c4g.11186623.6.876.434f68110P5L7q)
5、 [域名注册流程](https://help.aliyun.com/document_detail/54068.html?spm=a2c4g.11186623.2.34.e56523c7sxHfK4#concept-x22-3rv-12b)
6、 [首次备案](https://help.aliyun.com/knowledge_detail/36922.html#concept-ghz-3rl-zdb)，（国内 CN 等域名需要备案。）
7、 [设置域名解析](https://help.aliyun.com/document_detail/29716.html?spm=a2c4g.11186623.2.37.e56523c7sxHfK4)

# 一 环境搭建
1. 首先设置虚拟机的环境（LAMP）：
- 使用 SSH 客户端链接虚拟机。
- 查看 WordPress 环境要求，[参考文档](https://wordpress.org/about/requirements/)。
- 搭建环境，参考：[方法一：LAMP一键安装包](https://lamp.sh/install.html)，[方法二：Ubuntu下搭建LAMP环境](https://jingyan.baidu.com/article/4ae03de3e19ede3eff9e6b3c.html)。
```
方法二：

sudo apt-get  install apache2
sudo apt-get install php
sudo apt-get install mysql-server

sudo service mysql restart
sudo service apache2 restart

sudo chmod 777 /var/www

cd /var/www/html
sudo vi info.php

内容为
<?php
phpinfo();
?>

浏览器 127.0.0.1/info.php 查看环境是否搭建完成。

sudo a2enmod rewrite // 启用 mod_rewrite 模块。
sudo service apache2 restart

sudo apt-get install libapache2-mod-php5
sudo apt-get install libapache2-mod-auth-mysqlsudo apt-get install php5-mysql
sudo apt-get install php5-gd

sudo apt-get install phpmyadmin

mkdir pma // 在 /var/www/html 文件夹下创建 pma 文件夹。
ln -s /usr/share/phpmyadmin /var/www/html/pma

浏览器 127.0.0.1/pma/phpmyadmin/ 查看，若出现错误则 sudo vi php.ini 开启 mbstring，然后再次访问。
```

2. 启动服务：
```
sudo service mysql start
sudo service apache2 start
```

# 二 创建 WordPress 的数据库和用户
注：使用命令 `uname -n` 查看主机名，/etc/hostname 文件修改主机名。


```
mysql -u root -proot

CREATE DATABASE databasename; // wordpress 作为数据库名字。

GRANT ALL PRIVILEGES ON databasename.* TO "wordpressusername"@"hostname" // "wpblog"@"localhost"
IDENTIFIED BY "12345"; // 设置 wpblog 这个用户的密码。

FLUSH PRIVILEGES;

EXIT
```

# 三 配置文件
1. 将 wp-config-sample.php 重命名为 wp-config.php

2. 在  `// ** MySQL settings - You can get this info from your web host ** //` 下输入信息。
```
DB_NAME 
    在第二步中为WordPress创建的数据库名称
DB_USER 
    在第二步中创建的WordPress用户名
DB_PASSWORD 
    第二步中为WordPress用户名设定的密码
DB_HOST 
    第二步中设定的hostname（通常是localhost，但总有例外；参见编辑wp-config.php文件中的“可能的DB_HOST值）。
DB_CHARSET 
    数据库字符串，通常不可更改（参见zh-cn:编辑wp-config.php）。
DB_COLLATE 
    留为空白的数据库排序
```

3. 在 `* Authentication Unique Keys.` 下输入密钥的值，[参考链接](https://codex.wordpress.org/Editing_wp-config.php#Security_Keys)，[WordPress 2.6中关于如何设置SSL](http://boren.nu/archives/2008/07/14/ssl-and-cookies-in-wordpress-26/)。

4. 上传文件，决定将博客放在网站的什么位置上：
- 网站根目录下（如：http://example.com/ ），可用 FTP 客户端将 wordpress 目录下所有内容（无需上传目录本身）上传至网站根目录。
- 网站子目录下（如：http://example.com/blog/ ），需将 wordpress 目录重命名，之后用 FTP 客户端将重命名后的目录上传到网站根目录下某一位置。

# 四 运行安装脚本
1. 访问页面进行安装：
- 放在根目录的，http://example.com/wp-admin/install.php （本地用 127.0.0.1/wp-admin/install.php）
- 放在子目录的，http://example.com/blog/wp-admin/install.php

2. 填写信息：
注：
可能出现 Error establishing a database connection 错误；
查看 /var/log/mysql，发现 Access denied for user 'root'@'localhost' (using password: NO)
可能是因为安装数据库时没设置密码所致，通过修改密码解决，

![填写信息](图1.PNG)