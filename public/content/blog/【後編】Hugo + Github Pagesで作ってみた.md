+++
author = "kinko25"
categories = ["Hugo","Github","Github Pages"]
tags = ["hugo"]
date = "2018-07-02"
description = "Github Pagesにブログを開設してみた。"
featured = "pic01.png"
featuredalt = "Pic 1"
featuredpath = "date"
linktitle = ""
title = "【後編】Hugo + Github Pagesで作ってみた"
type = "post"

+++

# Github Pagesにブログを開設してみた。
## ブログの基本設定をカスタムしてみる。
私がいじった設定は、主にconfig.tomlのSNSシェアボタンの表示・非表示設定や、
アイコンなどの設定、サイトのタイトル名などを変更してあります。

あまりボタンが多すぎても邪魔くさいと感じてしまう人間なので、かなり削ってる方だと思います。

## サイトをローカルで見てみる

カスタムしていると、「どこが、どんな風に変わったのか」がわからないので、
ローカルサーバーを立てて確認したいと思います。
ターミナルを開いて、下記コマンドをblogディレクトリ内で叩いてみましょう。
```
$ hugo server
Building sites …
                   | EN
+------------------+----+
  Pages            | 31
  Paginator pages  |  1
  Non-page files   |  0
  Static files     | 35
  Processed images |  0
  Aliases          |  7
  Sitemaps         |  1
  Cleaned          |  0
```
コマンドを実行すると、「Building sites …」といった感じで、
ローカルサーバーが立ちます。
localhost:1313/で見れるかと思います。
問題なければ、本番反映しましょう。
```
$ ./deploy.sh # このコマンドだけ叩けば、本番反映されます。
```

## Google Analyticsを設定する
Downloadしたテーマにもよりますが、
config.tomlの最初の方に
```
googleAnalytics = ""
```
という項目ありますので、
```
googleAnalytics = "UA-000000-1"
```
と、ご自身のUAから始まるものをいれてビルドしてあげるだけです。

もし、「そんなのなーい＞＜」という方は、

こちらを参考にしてみてください。

下記リンク先のやり方であれば、アドセンスのタグ設置も容易だと思います。

https://bash-prompt.net/guides/custom-html-jugo/


## Google Adsense対応方法
アドセンスを利用するには、独自ドメインが必須。

githubのsettingのページでできちゃうのかなって思ったのですが、

出来なかったので、お名前.comなどでドメインを契約してください。

ドメインをゲットしたら、そのドメイン名をgithubのsetting画面に登録すれば、ドメイン変更は完了です。


## 独自ドメインをSSL化する
今月の20日くらいにSSL化しないとChromeで見れなくなってしまうようなので、

対応しようとしてましたが、SSL対応まだしておりません。※7月2日時点

SSL化対応するには、色々やり方があると思いますが、
どうせなら無料がいいですよね。
CloudFlareというサービスがあるので、
これでSSL対応が可能のようです。

ただ、今年に入ってからgithubが独自ドメインに対してもSSL化対応をしてくれるみたいな記事をちらほら。
おそらく全体にまで追いついていない様子。

SSL対応はどこでもいいが、しておいたほう良さそうですね。

## 最後に
ここまで構築できたら、あとはコンテンツを増やしながら、

色々カスタムしていけるので、ワクワクしますし、
技術的な面でも色々勉強になります。

1個サイトを作るだけで、得られるものは多いと思います。

ぜひ、この機会に触れてみてはいかがでしょうか？

ちなみに、1年ぶりにほったらかしにしていたアドセンスを見たら、

136円の収益が発生しておりましたｗ

早くドメインを取得してアドセンス貼りたいですなぁ

Hugo+GithubPagesの紹介は、この辺で。
読んでいただき、ありがとうございました。