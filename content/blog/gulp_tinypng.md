+++
author = "kinko25"
categories = ["Gulp","Node.js","画像圧縮"]
tags = ["Gulp","Node.js","画像圧縮"]
date = "2018-08-01"
description = "大量の画像を圧縮していくのって面倒。"
featured = "pic06.png"
featuredalt = "Pic 6"
featuredpath = "date"
linktitle = ""
title = "画像圧縮をGulpとTinyPNG APIで自動化しよう！"
type = "post"
+++

# 画像圧縮を自動化しよう！
## 大量の画像を圧縮していくのって面倒。

前回の更新から大分、経ってしまいました。。。

今回は、画像圧縮について

画像を圧縮して、サイズ容量を減らすことでサイトの表示速度に大きく影響します。

表示速度を軽視してる人が多いので、そういう人は3G回線で生活してみてはどうでしょう。

ストレスでしかないと思いますｗ

それでは、大量の画像圧縮を一回のコマンドを叩くだけで500枚まで圧縮する方法をご紹介したい。

## どうやって圧縮するか？
実際、どうやって圧縮するのかはいろんなやり方がありますが、

今回は、gulpと画像圧縮で有名な「TinyPNG」のAPIを使って行きます。
TinyPNGと言っても、名前すら覚えてない人がおおいので、
パンダのやつって言えばわかると思います。


## TinyPNG APIを取得しよう。
下記、リンク先でメールアドレスを入力して「Get your API key」を押しましょう。

https://tinypng.com/developers


APIキーが取得出来たら、メモ帳などにコピペしておいてください。

## 圧縮するための準備をする
```
環境
Windows7
Node.js 最新版 ※Nodeは予め、インストールしておきましょう。
gulp 3系
```

Macならターミナル、Windowsならgitbashなどを開いてください。

あとは下記コマンドを叩きまくっていけばいけます。
```
$ pwd
$ ls -la
$ mkdir tpng
$ cd tpng
$ mkdir img
$ mkdir tpng_img
$ npm init
$ npm install gulp
$ npm install gulp-tinypng-compress
$ touch gulpfile.js

## ここでgulpfile.jsをエディターで開きましょう
## 開いたら下記の内容をコピペ。
###################################################
var gulp = require('gulp')
var tinyping = require('gulp-tinypng-compress')

// TinyPNG APIを使用した画像圧縮
gulp.task('tpng', function() {
  gulp
    .src('./img/**/*.{png,jpg,jpeg}')
    .pipe(
      tinyping({
        key: 'APIキー' // TinyPNGのAPI Keyを入力
      })
    )
    .pipe(gulp.dest('./tpng_img'))
})
###################################################

$ gulp tpng
```
これで動けばあとはコンパイルを待つだけです。

「動かない」、「壊れた」など言ってる人は出直してください。

## 最後に
ブラウザ上のTiny PNGに一枚一枚画像ぶん投げてるのを見ると、めっちゃ非効率でイケてないと思うので、

gulpコマンド叩いて圧縮が終わるまで、のんびり他の事に時間を費やすことをオススメします。

それでは、GulpとTiny PNG APIを使った画像自動圧縮については、この辺で。

ありがとうございました。