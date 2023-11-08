<!--
 * @Name: 
 * @Data: YYYY-MM-DD HH:mm:ss
 * @Input: 
-->

# how to quickly deploy your mkdocs environment  

https://xuscode.github.io/enovia/

```batch
cd /d %~dp0
git clone https://github.com/xuscode/enovia.git enovia.github.io
cd /d enovia.github.io
rem pip freeze > requirements.txt
pip install -r requirements.txt --upgrade -i https://pypi.tuna.tsinghua.edu.cn/simple
```

##  video

If the video can't be fast-forward. You can open it using Firefox.