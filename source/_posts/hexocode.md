title: "Hexo Blog Development--Color and Background"
date: 2015-04-06 15:34:36
categories: Blog
tags: Hexo
---
hexo优化之代码块的颜色与背景
hexo的代码块的浅色背景并不是受到很多人的喜欢，这个更改也很简单。
首先要更改/theme/light/css/_partial/article.styl中
pre 下面第一行
{% codeblock %}pre
	background #颜色
{% endcodeblock %}
<!--more-->
之后更改/theme/light/css/_partial/syntax.styl中
figure.highlight 下面第一行
{% codeblock %}figure.highlight
	background #颜色
{% endcodeblock %}

同文件下的.gutter下面的参数是调整左边的代码行数条，如果不喜欢行数和代码中间的白色分割线，那么把.gutter下的border-right和其下面.code的border-left宽度设为0或者颜色调成你所选用的背景色。那么就会有如下效果。当然也可以设成你喜欢的颜色。

之后,在下面有一个.code的标签可以更改代码的颜色,默认的颜色不适合深色的背景。最后为了代码在这个背景下不会有模糊感，要删除掉shadow。注释掉或者删除掉figure.highlight下的text-shadow ... 就可以了。

