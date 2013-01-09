---
layout: post
title: Backbone.Collectionのfetch methodでstatus codeは200なのにerror
tags: [programming, backbone, JavaScript]
---

Backbone.jsを使っていてあれ？ってなったこととその解決方法

Backbone.Collectionを使ってJavaScriptソース内のマジックナンバーの定数、エラー表示の文章などをjsonから取り出すものを作っていた。


{% highlight coffeescript %}
Backbone.Config extends Backbone.Collection
  url: 'hogehoge/piyo.json'

  load: ->
    @fetch
      success: (data) ->
        alert 'hoge'
      error: (data)
        alert 'piyo'
{% endhighlight %}

ざっくりこんな感じでjsonファイルにアクセスして、そこからデータを引っ張ってこようと思ってた。

でも```@fetch```のcallbackがずっとerrorに飛ばされて？って感じになっていた。

```data.status``` を見ても200なのでrequest自体はちゃんと通ってる、なのにerror。なにこれって思っていたら。

[Backbone.js: Save Method Always Return Error Callback]("http://stackoverflow.com/questions/10674564/backbone-js-save-method-always-return-error-callback")

こんなものが。

つまり、successが呼ばれる条件？は```status code```が200で、かつ帰ってくるjsonのsybtaxが正しい(valid json)こと。

そんな馬鹿な、と思ってjsonファイルを見直すと、ミスってた。 , が一個多かった。

まぁsuccessにいく条件がちょっとわかったし、よしとするか！！





泣きたい