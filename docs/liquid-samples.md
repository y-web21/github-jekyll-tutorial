---
title: Step by Step tutorial
show_sidebar: true
---


[オプション設定](http://jekyllrb-ja.github.io/docs/configuration/options/)
[コマンドラインの使い方](http://jekyllrb-ja.github.io/docs/usage/)
[変数](http://jekyllrb-ja.github.io/docs/variables/)


## Liquid basiça 

### オブジェクト

- \{\{ page.title \}\} 
    - ページにpage.titleという変数の内容を出力します。
    - value: {{ page.title }}

### タグ

{% raw %}
- `{% %}`で扱うもの。ロジック。

**If statement**
```html
{% if page.show_sidebar %} <!-- front matter 変数 show_sidebar == true の場合 -->
  <div class="sidebar">
    sidebar content
  </div>
{% endif %}
```
{% endraw %}

{% if page.show_sidebar %}
  <div class="sidebar">
    sidebar content
  </div>
{% endif %}
<br>

**link** 
{% raw %}
- {% link _directory/name-of-document.md %}
    - 拡張子が必要
    - 文字列の出力なので`<a>`タグや`markdown`のリンク部に埋め込む
    - \[to home\]({% link index.markdown %})
        - {% endraw %}[to home]({% link index.markdown %}){% raw %}
    - リンクパスの構造がわからないうちは、{{ page.path }}パスを出力すると良いかもな。
    - `../index.md`のような相対パスは駄目らしい。本当かい？
    - `Liquid filter`での文字列の加工には非対応
- {% post_url 2010-07-21-name-of-post %}
    - 拡張子が不要。へぇ・・・。
{% endraw %}

### Liquid fileter

- フィルタ `|`

[filter](http://jekyllrb-ja.github.io/docs/liquid/filters/#standard-liquid-filters)
- 入力{% raw %}
    1. {{ "convert to uppercase first letter." \| capitalize }}
    1. {{ -17 \| abs }}
    1. {{ "/assets/style.css" \| absolute_url }}{% endraw %}
- 出力
    1. {{ "convert to uppercase first letter." | capitalize }}
    1. {{ -17 | abs }}
    1. {{ "/assets/style.css" | absolute_url }}
   
### code highlight

- Ruby
{% highlight ruby %}
def foo
  puts 'foo'
end
{% endhighlight %}

- Bash
{% highlight bash lineos %}
for i in $(seq 2 5 17)
do
  echo "$i"
done
{% endhighlight %}

- Python (markdown syntax)

```python
import os
print(r'{}/{}'.format(os.getcwd(),'file.txt'))
```
