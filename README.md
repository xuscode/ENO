

```bat

@echo off
cd /d %~dp0
mkdocs -i https://mirrors.aliyun.com/pypi/simple/                  
mkdocs-material -i https://mirrors.aliyun.com/pypi/simple/          
mkdocs-material-extensions -i https://mirrors.aliyun.com/pypi/simple/
mkdocs-video -i https://mirrors.aliyun.com/pypi/simple/

```
