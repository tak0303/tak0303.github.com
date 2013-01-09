---
layout: post
title: fuelPHPで書いたアプリをherokuで動かす
tags: [heroku, fuelphp ]
---

PHPのフレームワークで言えばfuelPHPが一番好きです.

で、今回herokuを使ってアプリを公開しようとしたんですが色々と詰まったのでメモ代わりに.

1) heroku toolbeltの導入

herokuにアカウントを作ったら,heroku toolbeltを導入します.

herokuをコマンドラインから操作するとき(herokuコマンドを使う), heroku toolbeltを利用します.

公式サイトでダウンロードするか,

<img src="/images/heroku_1.png" alt="heroku">

gemからインストールします.

<pre>
  gem install heroku
</pre>

で,インストールできたら公開鍵の設定をします

<pre>
  heroku login
</pre>
ってやってemail,passwordを入力すると,herokuが自動的に公開鍵を探してくれて,設定してくれます(幾つかある場合は選びます)
これで公開鍵の設定は完了です

*公開鍵の作り方は,[こちらの方]("http://d.hatena.ne.jp/uco_twinkle/20080409/1207703829")などがまとめてくださっています

できたら,
fuelのアプリを作ります.

プロジェクトディレクトリに移動して,

<pre>
  oil create アプリ名
</pre>
oilコマンドの導入などは　こちら[公式ドキュメント日本語版]("http://search.net-newbie.com/fuel/")


できたら,アプリのrootディレクトリに移動して,

fuelは最初から.gitなどのフォルダがある(fuel自体がgitで管理されている)ので,そのままではいろいろとめんどくさい. ので[こちら](http://d.hatena.ne.jp/Kenji_s/20111202/1322783183)を参考にしながら環境構築します

できたら,
ローカルのリポジトリにcommit
<pre>
  git init
  git add .
  git commit -m "first commit"
</pre>

で,アプリを作る
<pre>
  heroku create --buildpack https://github.com/winglian/heroku-buildpack-php アプリ名
</pre>
でheroku上にアプリが作られます(アプリ名は省略可,あとで変えることもできます)

今回はphpを動かしたいのでbuiltpackを一緒につけました  *[こちら](http://d.hatena.ne.jp/hnw/20120603)を参考にしました


で,ここからがphpの設定です

herokuはrootディレクトリにindex.phpがないと,アプリをphpアプリだと認識してくれません.

なのでindex.phpは必須です.
しかし,fuelPHPのパブリックディレクトリは public/ 直下にあり,root直下のにはアクセスしたくありません.

なので今回は.htaccessを使い,rootへのアクセスを public/ 以下に変更しました.(root直下のindex.phpは何も書かずに置いておきます)

<pre>
  RewriteEngine on
  RewriteBase /
  RewriteRule ^(.+)-info\.php$ $1-info.php [L]
  RewriteCond %{SCRIPT_FILENAME} !^/app/www/public/
  RewriteRule ^(.*)$ public/$1 [L]
</pre>

これをroot直下に置いて,rootへのアクセスをpublic以下に以下にかえました(すいません詳しくわかってないです)


ここまでやったら git addとかしてから,

<pre>
  git push heroku master
</pre>

でherokuにpushします.すると自動でデプロイまでしてくれるので,

<pre>
  heroku open
</pre>

で　アプリを開きます,これでfuelPHPの画面が出たら完成!

<img src="/images/heroku_2.png" alt="fuel">

長かった...

もっといい方法などあればぜひ教えていただきたいです.
よろしくお願いします!





