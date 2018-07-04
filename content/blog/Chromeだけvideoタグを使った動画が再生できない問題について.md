+++
author = "kinko25"
categories = ["Hugo","Github","Github Pages"]
tags = ["hugo"]
date = "2018-07-04"
description = "videoタグで動画を扱う際に注意すること"
featured = "pic02.jpg"
featuredalt = "Pic 2"
featuredpath = "date"
linktitle = ""
title = "Chromeだけvideoタグを使った動画が再生できない問題について"
type = "post"

+++

# videoタグで動画を扱う際に注意すること
## なぜかChromeだけ初期表示で動画再生がされない事件
最近、なぜかサイト内の背景動画がChromeブラウザだけ、

動かないという問題起きていました。

しかし、意外にも簡単に解決できたので、ご紹介したいと思います。

## Chrome以外のブラウザでは、動画再生が可能。
まず、検証して気づきました。

FirefoxやIE11でさえ、動くのにChromeでは動かないということに。

最初はJSなどの影響を受けてるのではないかと思い、

調査してみましたが、何の問題もなく。。。

リンクをコピペで飛ぶと、

初期表示では、再生されず。

二回目以降で再生されるという不思議なものでした。

## ググってみると

下記のサイトが参考になりました。

Chrome最新版にて背景動画が自動再生されない事象：原因と対処方法 
http://souken-blog.com/2018/05/08/chrome-movie/

今回は、ここに記載されている

videoタグにmutedを追加するというだけでした。
```
<video autoplay loop muted src="movie.mp4"></video>
```
背景動画で使っている動画はそもそも無音なので、

これで解決できました。

## 最後に
数ヶ月前まで再生されていたのに、再生されなくなるのは怖いですね。


Chrome最新版にて背景動画が自動再生されない事象：原因と対処方法 
http://souken-blog.com/2018/05/08/chrome-movie/

上記のリンク先で、

"広告動画からの音声を制限するのが主たる目的だそうです。"

を見て「なるほどー！」と納得しました。

今回はこの辺で。

ありがとうございました。