# JCG-JHR-N835R-后台命令执行漏洞

## 漏洞描述

JCG JHR-N835R 后台存在命令执行，通过 ; 分割 ping 命令导致任意命令执行

## 漏洞影响

> [!NOTE]
>
> JCG JHR-N835R

## Shodan

> [!NOTE]
>
> JHR-N835R

## 漏洞复现

登录页面 admin admin登录

![](JCG-JHR-N835R-后台命令执行漏洞.assets/1627363617998795.jpg)

在后台系统工具那使用 PING工具，使用 ; 命令执行绕过

![](JCG-JHR-N835R-后台命令执行漏洞.assets/1627363618320132.jpg)

![](JCG-JHR-N835R-后台命令执行漏洞.assets/16273636186147351.jpg)