### 漏洞描述

```
影响版本：phpstudy <= 8.1.0.7
phpstudy 存在 nginx 解析漏洞，攻击者能够利用上传功能，将包含恶意代码的合法文件类型上传至服务器，从而造成任意代码执行的影响。
```

### 环境搭建

### 下载phpstudy v8.1.0.7，安装完成后如下：

![img](phpStudy-nginx-解析漏洞.assets/1590180-20200911201109107-1095326028.png)

### 漏洞复现

### 正常访问图片：

```
http://192.168.3.142:8088/123.gif
```

![img](phpStudy-nginx-解析漏洞.assets/1590180-20200911201248509-1032607674.png)

### 增加后缀访问如下：

```
成功解析php文件
http://192.168.3.142:8088/123.gif/xxx.php
```

![img](phpStudy-nginx-解析漏洞.assets/1590180-20200911201322842-11528172.png)

### 漏洞分析

```
该漏洞属于安全配置错误漏洞。
漏洞产生的原因为：
1、由于配置错误，导致 nginx 把以 .php 结尾的文件交给 fastcgi 处理，因此可以构造 http://192.168.3.142:8088/123.gif/xxx.php（任何服务器端不存在的php文件均可，比如X.php）
2、但是 fastcgi 在处理 xxx.php 文件时发现文件并不存在，这时 php.ini 配置文件中 cgi.fix_pathinfo=1 发挥作用，这项配置用于修复路径，如果当前路径不存在则采用上层路径。因此这里交由 fastcgi 处理的文件就变成了 /123.gif.
3、最重要的一点是 php-fpm.conf 中的 security.limit_extensions 配置项限制了 fastcgi 解析文件的类型（即指定什么类型的文件当做代码解析），此项设置为空的时候才允许 fastcgi 将 .png 等文件当做代码解析.
```

​    分类:             [Web安全](https://www.cnblogs.com/Yang34/category/1392865.html)