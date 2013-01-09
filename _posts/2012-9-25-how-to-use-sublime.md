---
layout: post
title: Sublime Text 2がプログラミング人生を変えるかも知れない
tags: [programming, sublime, editor]
---

# はじめに

最近話題のエディタ,SublimeText2,ボクもかなり気に入っています.
なんといってもその豊富なプラグイン(vim,emacsには劣るが),そしてそれらの導入コストの低さなどが優れてSublimeTextの優れた点ではないでしょうか.

今回はボクがSublimeを使い始めてから入れたプラグイン,設定,よく使うキーバインドなどをまとめて行こうと思います.

# インストール,初期設定
SublimeTextは本家のサイトからダウンロードできます.

[http://www.sublimetext.com/]("http://www.sublimetext.com/")

headerのdownloadから自分の環境にあったものをダウンロードしてください.

今回,記事中ではボクの環境がmacなのでmacのキーバインド,操作方法で紹介します.windowsの方は脳内変換をよろしくお願いします.


で、インストールできたら,次はプラグインのインストールの準備.

プラグインのインストールにはSublime Package Controlが便利すぎるのでまずそれをインストールする.

<pre>
ctrl + shift + @
</pre>
でコンソールを開き,

<pre>
import urllib2,os; pf='Package Control.sublime-package';ipp=sublime.installed_packages_path(); os.makedirs(ipp) if not os.path.exists(ipp) else None; urllib2.install_opener(urllib2.build_opener(urllib2.ProxyHandler())); open(os.path.join(ipp,pf),'wb').write(urllib2.urlopen('http://sublime.wbond.net/'+pf.replace(' ','%20')).read()); print 'Please restart Sublime Text to finish installation'
</pre>

これをそのままコピーアンドペースト
で、実行されたのを確認したら再起動する.

Package Controlは

<pre>
Command + Shift + p
</pre>
でCommand Pallet開き,その後, installとタイプすると起動する.

ここでSublimeTextにインストールするプラグインなどを検索し、その場でインストールが出来ます.(便利！)

# 覚えておきたいショートカット

<pre>
Command + Shift + p
</pre>
さっきも書いたんですがこれを起動することでSublimeTextにインストールされた機能(package control含む)や,snippetなどの検索ができます


<img src="/images/sublime_1.png" >

<pre>
 Command + Shift + f
</pre>
プロジェクト内検索, 結果はこんなかんじで帰ってきます

<img src="/images/sublime_2.png" >


<pre>
  Command + Ctrl + ↓ or ↑
</pre>
選択した範囲を動かせます

<pre>
  Command + /
</pre>
選択範囲(選択していない場合はカーソルのある行)をコメントアウトorインします


<pre>
  Command + Option + 2
</pre>
windowを縦に分割(Command + Option + 1で元に戻す)

<pre>
  Command + Ctrl + f
</pre>
フルスクリーンモード, 個人的に見やすくて好きです

<pre>
  Command + p
</pre>
でいま開いているファイル一覧が検索でき,開ける

<pre>
  Command + r
</pre>
でファイル内の関数に飛べる
ちなみに@を#または.に変えるとhtmlならそれぞれidまたはclass一覧が検索出来る


などなど..
もっと詳しくは[こちらの方](http://kachibito.net/software/sublime-text-2-shortcuts.html)も(windows版です)とても詳しく紹介されているので参考までに.


# おすすめのプラグインなどなど

packege controlからインストールできるプラグイン,テーマなどを紹介します

### html,css,javascript関連

   - **HTML5**

        html5のsnippet,自動補完,シンタックスハイライトなど.

----------------------
   - **jQuery**

        jQueryのsnippet,自動補完,シンタックスハイライトなど.

----------------------


   - **CSS snippet**

        CSSのsnippet,自動補完,シンタックスハイライトなど.
        CSS3にも対応しています

        試しにaniと打ってtabを押すと

        <img src="/images/sublime_3.png" alt="">

        こんな感じに書くブラウザごとの記述を一気に出してくれ,またそれらを同時に編集できます

----------------------


   - **CoffeeCompile**

        Command + Shift + cでcoffee scriptをjsにコンパイル,同じ階層にjsファイルを作る

----------------------

   - **ZenCoding**

        ZenCodingをインストールします.これは絶対入れるべき!
        マークアップの速度が2倍ぐらいになります

        Zencodingは便利なので[ここ]("http://code.google.com/p/zen-coding/")とかをみるといいかも

----------------------

   - **Tag**

        HTML関連の機能の追加.
        タグのインデントなどを追加.スラッシュでタグを閉じるなどなど

----------------------

   - **Sass**

        Sassのシンタックスハイライト

----------------------

   - **Twitter Bootstrap Snippets**

        [TwitterBootstrap]("http://twitter.github.com/bootstrap/")のsnippet.

        便利です. コマンド一つ叩くだけでtwitterBootstrapによるサイトができてしまいます

        コマンド一覧はインストール後,command palletからbootstrapと打って検索できます

-----------------------

### programming言語,開発環境関連

  - **SublimeLinter**

      ruby,php,javascript,html,cssなど様々な言語のシンタックスをチェックしてくれます.

      間違っている場所は

      <img src="/images/sublime_4.png" alt="">

      こんな感じで四角でかこって表示してくれます(図はcoffee script)

      javascriptなどは設定が必要なので
      [こちらのサイト]("http://perl.no-tubo.net/2012/05/03/mac%E3%81%AE%E3%83%86%E3%82%AD%E3%82%B9%E3%83%88%E3%82%A8%E3%83%87%E3%82%A3%E3%82%BF-sublime-text2%E3%81%A7javascript%E3%81%AE%E3%82%B7%E3%83%B3%E3%82%BF%E3%83%83%E3%82%AF%E3%82%B9%E3%82%A8%E3%83%A9/")
      などが参考になります

----------------------

  - **RSpec (snippets and syntax)**

      Rspecのsnippetとシンタックスハイライト.

----------------------


  - **Git**

    command palletからGitが操作できます(Gitのinstallは予め必要です)

----------------------

  - **SideBarEnhancements**

    View → Side Barで出せるSideBarの機能を追加します,

    SublimeTextの残念なところとしてSideBarの機能がまだほとんど動いていない(バグ?)のでこれは必須です.

----------------------

###その他

  - **Terminal**

    Command + Shift + t でterminalが開けます,それだけです

---------------------

  - **Markdown Preview**

    SublimeTextで編集中のmarkdownをブラウザでpreviewすることができます

---------------------

  - **Sublime Tweet**

    Command palletからtweetすることができたりタイムラインを見たりできます.

---------------------

まだまだ沢山のプラグインがありますが,いまボクがメインで使っているものを紹介してみました.


###テーマ

  SublimeTextはテーマとカラースキームを簡単に変えることができます.

  カラースキームはシンタックスハイライトの色を変えるもの, テーマはSublimeText全体の色合いを変えるもの,という感じです.

  どちらもpackage managerから入れることができ,簡単です.

  カラースキームは上部メニューのSublimeText2から,
  Preference →　ColorScheme　
  で変更することができます.

  テーマは少し違い,テーマをインストールしたら
  Preference → Settings Userから編集します

  そこにダウンロードしたテーマの名前を記述します.

  <pre>"theme": "Soda Dark.sublime-theme",</pre>

  こんな感じです

  ボクの使ってるテーマはこんな感じです

  <img src="/images/sublime_5.png" alt="theme">


#キーバインド


  SublimeTextはキーバインドも一つの設定ファイルで管理するので,自由にキーバインドを増やすor変えることができます.

  SublimeText2 → Preference → Key Bindings - User　から設定できます.

  Key Bindings - Defaultも変えることができますが,その場合はUserの方で上書きするほうが良いと思います.

  僕自身それほど設定をしているわけではないのですが設定しているのは,

  <pre>
  // タブの切替を表示順にする
  { "keys": ["ctrl+tab"], "command": "next_view" },
  { "keys": ["ctrl+shift+tab"], "command": "prev_view" }
  </pre>

  SublimeTextはなぜかタブの切替が表示されている順番でないので,これで設定しています.

  このように簡単に設定が行えるので,ぜひやってみましょう.




#Tips


- 設定の同期

    SublimeTextの設定はすべて
    <pre>
    ~/Library/Application Support/Sublime Text 2/
    </pre>
    に保存されているので,複数のPCで設定を引き継ぎたい場合はこれらのファイルを同期させればよい.

- Vim操作を使う

    Vim風操作(nomalモードとinsertモードなど)が使いたい場合は
    Settings -Defaultの最後の行の

    <pre>"ignored_packages": ['vintage']</pre>を

    <pre>"ignored_packages": []</pre>にする







長くなりましたがこんな感じで多機能で使えやすいエディタであるのではないでしょうか.

主にフロントサイドエンジニアに人気なようですがバックエンドエンジニアでも遜色なく使えるのでは,と思います.

ぜひ一度試してみてはいかがでしょう！


















