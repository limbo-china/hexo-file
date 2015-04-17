title: "Fundamental Git Instructions"
date: 2015-04-07 22:15:58
tags: Git
categories: Blog
photos: 
---
在github上创建仓库：
{% codeblock %}
Create a new repository on the command line


touch README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/BrentHuang/MyRepo.git
git push -u origin master
{% endcodeblock %}
<!--more-->
在本地新建一个分支： `git branch Branch1`
切换到你的新分支: `git checkout Branch1`
将新分支发布在github上： `git push origin Branch1`
在本地删除一个分支： `git branch -d Branch1`
在github远程端删除一个分支： `git push origin :Branch1`   (分支名前的冒号代表删除)

直接使用git pull和git push的设置
{% codeblock %}
git branch --set-upstream-to=origin/master master 
git branch --set-upstream-to=origin/ThirdParty ThirdParty
git config --global push.default matching
{% endcodeblock %}