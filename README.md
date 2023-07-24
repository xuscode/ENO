
# how to quickly deploy your mkdocs environment  

you can use code to install dependency packages.
```batch
pip install -r C:\Temp\requirements.txt --upgrade -i https://pypi.tuna.tsinghua.edu.cn/simple
```

the following libraries are required to be installed including some theme styles.

```bash
mkdocs==1.4.2
mkdocs-glightbox==0.3.1
mkdocs-material==9.1.3
mkdocs-material-extensions==1.1.1
mkdocs-video==1.5.0
```

Use the following command to generate all library names and versions in the current python environment

```bash
pip freeze > C:\Temp\requirements.txt

```

```bat

@echo off
cd /d %~dp0
mkdocs -i https://mirrors.aliyun.com/pypi/simple/                  
mkdocs-material -i https://mirrors.aliyun.com/pypi/simple/          
mkdocs-material-extensions -i https://mirrors.aliyun.com/pypi/simple/
mkdocs-video -i https://mirrors.aliyun.com/pypi/simple/

```

##  video

If the video can't be fast-forward. You can open it using Firefox.