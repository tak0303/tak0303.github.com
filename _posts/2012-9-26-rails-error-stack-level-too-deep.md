---
layout: post
title: stack level too deep
tags: [programming, rails, error]
---

railsでmodelをsave!しようとした時に

{% highlight ruby %}
stack level too deep (SystemStackError)
{% endhighlight %}

こんなのが出た

どうも同じメソッドを無限に呼び出すと起こるエラーらしい→[http://d.hatena.ne.jp/rubyco/20060310/stack]("http://d.hatena.ne.jp/rubyco/20060310/stack")

こんな感じ
{% highlight ruby %}
def hoge
  hoge
end

hoge
{% endhighlight %}

当然こんなことはやってなかったのだがmodelの中に使いもしないpaperclipのメソッドを書いていた.
たぶんこれが無駄に呼ばれ続けていたのだろう！

消したら直った.
余計なものは書いてはいけない. まぁそうか...
