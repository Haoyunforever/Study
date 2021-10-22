# 华宜互联CMS默认存在超级管理员漏洞

## 漏洞描述

华宜互联CMS默认存在超级管理员漏洞，如不修改则使用默认账号密码即可登录超级管理员

## 影响版本

华宜互联CMS

## FOFA

> [!NOTE]
>
> body="华宜网络"

## 漏洞复现

原版的源码需要付费，可找到免费版的源码

![](华宜互联CMS默认存在超级管理员漏洞.assets/1627363046995285.jpg)

在目录下的DATA目录中有**mdb文件**, 打开后可以发现存在默认的两个用户

> [!NOTE]
>
> admin/123456
>
> lu123/cui123

![](华宜互联CMS默认存在超级管理员漏洞.assets/1627363047312588.jpg)

使用 用户lu123 即可登录超级管理员

![](华宜互联CMS默认存在超级管理员漏洞.assets/1627363047547456.jpg)

## 参考文章

[华宜互联0day分享](https://mp.weixin.qq.com/s?__biz=MzAxMzg4NDg1NA==&mid=2247484357&idx=1&sn=56abfaa736805e22910c9e9e1f8d8c3a&chksm=9b9a8f1caced060a3fbb4ce29fbe0c3b0a7399c542406237ebd0e3de71c7c538b459ff2a0c09&mpshare=1&scene=1&srcid=1117arJqHdtyfF7tqRrWAE7C&sharer_sharetime=1605622054852&sharer_shareid=02fbf89adff5cec7c814f47e9e13caca&key=f7cb72e8598687c9e0bf26cdce26791146e76a0a1d0277ca876ac35edce171d423ab6ebbd4174b54d81928ff3eeecf7f396f99a245a3cc5b76ec063c5d5569fadfb257044bafedda4b2583ac941bea57ed294bbab33429b9ae9e71fab7ee6d49f049d2cde08e459f43cd378a2a6548311fea16848)