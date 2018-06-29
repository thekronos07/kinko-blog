+++
author = "kinko25"
categories = ["Hugo"]
tags = ["hugo"]
date = "2014-09-28"
description = "Github Pagesにブログを開設してみた。"
featured = "pic03.jpg"
featuredalt = "Pic 3"
featuredpath = "date"
linktitle = ""
title = "Hugo + Github Pagesで作ってみた"
type = "post"

+++

## Github Pagesにブログを開設してみた。

別に、はてなブログでも良かったのですが、

どうせ作るなら、なんか身につけたい。と思い。。。

最初、Jekyllでやろうとしたが、Windowsとの相性が悪いため、

Hugoでやることにした。

テーマ一覧を見ると、Jekyllの方充実してると思う。

Hugoテーマリスト：

https://themes.gohugo.io/

jekyllテーマリスト ：

http://jekyllthemes.org/

Hugoはデザイン的に、なんだかイケてないというか・・・。ｗ

というわけで、早速インストールした手順をざっくり紹介していきます。

きっかけはこれ。

https://onoxeve.com/posts/hugo-on-github-pages/


しかし、WindowsではHomebrewを使えないため、chocolateyをコマンドプロンプトから入れた。

インストール後、VS codeの再起動を行い、ターミナルでchocolateyコマンドを叩けば、VS codeでも使えることがわかる。

https://chocolatey.org/install#installing-chocolatey

あとは好きなテーマを選択して

pullして指定の場所にファイルを移動すれば、おｋ

移動が完了したら、hugoのコマンドたたけば表示される

例:

```
## build 本番公開用
$ hugo

## Watch　ローカル用
$ hugo server
```

gitにあげる時にこことか参考になりました。

http://blog.syati.info/post/create_hugo_2/

詳細は、ぐぐってください。

これから色々いじっていきます

