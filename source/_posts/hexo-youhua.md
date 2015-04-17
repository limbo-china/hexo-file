title: "Hexo Development"
date: 2015-04-06 18:14:34
categories: Blog
tags: Hexo
---
**hexo博客的优化技巧**
后面的修改优化主要是针对 `theme/light` 的，如果你想偷懒直接使用配置好的主题，欢迎使用我的Lightum。如果你想使用其他主题，可以去Wiki挑选一款喜欢的。
<!--more-->
**添加“多说”评论**
hexo默认使用国外比较流行的disqus，不过，按照“因地制宜”的原则，我们修改为国内用的多又好用的“多说”评论系统。步骤非常简单：
在多说进行注册，获得通用代码。
将通用代码粘贴到`themes\light\layout\_partial\comment.ejs`里面，如下：
{% codeblock %}
<% if ( page.comments){ %>
<section id="comment">
通用代码
</section>
<% } %>
{% endcodeblock %}
很多网友反映自己使用的非 light 主题中找不到相应的文件。我的这些修改都是在 light主题中，其他主题请参考《Hexo使用多说教程》。
**添加『页面导航』**
在刚才添加「多说」评论的文件中，加入一段代码，如下：
{% codeblock %}
<% if ( page.comments){ %>

 <nav id="pagination" >
    <% if (page.prev) { %>
    <a href="<%- config.root %><%- page.prev.path %>" class="alignleft prev" ><%= __('prev') %></a>
    <% } %>
    <% if (page.next) { %>
    <a href="<%- config.root %><%- page.next.path %>" class="alignright next" ><%= __('next') %></a>
    <% } %>
    <div class="clearfix"></div>
</nav>

<section id="comment">
{% endcodeblock %}
**添加“百度分享”**
到百度分享获得代码，在`themes/light/layout/_partial/article.ejs`中，将`<%-partial('post/share')%>`删掉，替换为百度分享的代码。
**添加小图标**
在`themes/light/layout/_partial/head.ejs`里将`<link href="<%- config.root %>favicon.png" rel="icon">`替换为`<link href="<%- config.root %>favicon.ico" rel="icon" type="image/x-ico">`。将`favicon.ico`图标文件放在source目录下。*制作图标的网站*，<http://www.faviconer.com>。
**添加分类、标签云widget**
很简单，在`themes/light/_config.yml`中，添加如下：
{% codeblock %}
widgets:
- category
- tagcloud
-
{% endcodeblock %}
__添加友情链接widget__#  #
在`themes/light/layout/_widget`中新建名为`blogroll.ejs`的文件，编辑内容如下：
{% codeblock %}
<div class="widget tag">
<h3 class="title">友情链接</h3>
<ul class="entry">
<li><a href="http://zipperary.com/" title="Zippera's Blog">Zippera</a></li>
</ul>
</div>
{% endcodeblock %}
在`themes/light/_config.yml`中，添加如下：
{% codeblock %}
widgets:
- blogroll
- 
{% endcodeblock %}
生成post时默认生成categories配置项
在`scaffolds/post.md`中，添加一行categories:。同理可应用在page.md和photo.md。
__添加新浪微博widget(微博秀)__
去新浪微博开放平台设置和生成微博秀代码。
在`themes/light/layout/_widget`中新建名为`weibo.ejs`的文件，将刚才的代码直接保存到这里。
在`themes/light/_config.yml`中，添加如下：
{% codeblock %}
widgets:
- weibo
-
{% endcodeblock %}
__导航栏添加”关于”__
hexo new page "about"
到`source/about/index.md`编辑内容。
在`themes/light/_config.yml`中，添加如下：
{% codeblock %}
menu:
  关于: /about
{% endcodeblock %}
__主页文章显示摘要__
编辑md文件的时候，在要作为摘要的文字后面添加`<!--more-->`即可。
优化是无止境的，今天先写这些。