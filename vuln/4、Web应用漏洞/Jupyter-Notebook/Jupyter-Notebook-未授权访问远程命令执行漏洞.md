# Jupyter-Notebook-未授权访问远程命令执行漏洞

## 漏洞描述

Jupyter Notebook（此前被称为 IPython notebook）是一个交互式笔记本，支持运行 40 多种编程语言。

如果管理员未为Jupyter Notebook配置密码，将导致未授权访问漏洞，游客可在其中创建一个console并执行任意Python代码和命令。

## 漏洞影响

> [!NOTE]
>
> Jupyter Notebook

## FOFA

> [!NOTE]
>
> app="Jupyter-Notebook" && body="Terminal"

## 漏洞复现

访问目标, 点击 Terminal 打开命令行界面

![](Jupyter-Notebook-未授权访问远程命令执行漏洞.assets/1627363109198459.jpg)

执行命令并反弹shell

![](Jupyter-Notebook-未授权访问远程命令执行漏洞.assets/1627363109548886.jpg)