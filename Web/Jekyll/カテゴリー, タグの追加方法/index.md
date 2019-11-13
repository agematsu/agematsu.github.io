---
title: カテゴリー, タグの追加方法
categories: Jekyll
---
ブログ記事にカテゴリーを設定するのが、CMSを使う目的の一つでもありますので、Jekyllでカテゴリー分けする手順を見ていこうと思います。  
まず、**_config.yml**ファイルに以下のテキストを追加してください。

```
permalink: /:categories/:title/
```
パーマリンクについての説明は、<a href="http://jekyllrb-ja.github.io/docs/permalinks/">公式サイト</a>にあります。
簡単に説明すると、

## カテゴリーページを作る
まずはじめに、カテゴリー用のページを作る必要があります。
テンプレートは以下にあるので、categories.htmlというファイルをrootフォルダに作って保存してください。
```
---
layout: page
permalink: /categories/
title: Categories
---


<div id="archives">
{% for category in site.categories %}
  <div class="archive-group">
    {% capture category_name %}{{ category | first }}{% endcapture %}
    <div id="#{{ category_name | slugize }}"></div>
    <p></p>

    <h3 class="category-head">{{ category_name }}</h3>
    <a name="{{ category_name | slugize }}"></a>
    {% for post in site.categories[category_name] %}
    <article class="archive-item">
      <h4><a href="{{ site.baseurl }}{{ post.url }}">{{post.title}}</a></h4>
    </article>
    {% endfor %}
  </div>
{% endfor %}
</div>
```
## Jekyllのポストにカテゴリーを表示する
それぞれのポストにカテゴリーを追加するには、以下のコードを**post layout**のカテゴリーを表示したいところに追加します。
```
<div class="post-categories">
  {% if post %}
    {% assign categories = post.categories %}
  {% else %}
    {% assign categories = page.categories %}
  {% endif %}
  {% for category in categories %}
  <a href="{{site.baseurl}}/categories/#{{category|slugize}}">{{category}}</a>
  {% unless forloop.last %}&nbsp;{% endunless %}
  {% endfor %}
</div>
```
## 参考文献 
<a href="https://blog.webjeda.com/jekyll-categories/">3 Simple steps to setup Jekyll Categories and Tags</a>
