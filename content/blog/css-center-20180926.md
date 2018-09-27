+++
author = "kinko25"
categories = ["CSS","CSSテクニック"]
tags = ["CSS","CSSテクニック"]
date = "2018-09-27"
description = "色んなやり方で、中央寄せにする方法をご紹介。"
featured = "pic07.png"
featuredalt = "Pic 7"
featuredpath = "date"
linktitle = ""
title = "中央寄せにしたい時のCSSテクニック集"
type = "post"

+++

# 中央寄せにしたい時の様々なCSSテクニック集
## 中央寄せについて
前回の記事からだいぶ期間が空いてしまいました。。。。

今回は、中央寄せのやり方についての記事となります。

私も時々、忘れてしまいググることが多いので、
まとめておきたいと思います。

上から順番に
・左右中央寄せのやりかた
・上下中央寄せのやりかた
・上下左右中央寄せのやりかた

上記の3つを抑えておけば、だいたいの案件では困らないかと。

## 左右中央寄せにするやり方
### ①text-align:centerで画像を左右中央寄せ

デモ：https://codepen.io/thekronos07/pen/JmPRwj

```
HTML:
<p class="thumb">
  <img src="https://dummyimage.com/600x400/000/fff">
</p>

CSS:
.thumb {
  text-align: center;
}
img {
  /* reset.css */
  max-width: 100%;
  height: auto;
  vertical-align: middle;
}
```

### ②marginを使ったやり方で画像を左右中央寄せ

デモ：https://codepen.io/thekronos07/pen/NOKREy

```
HTML:
<p class="thumb">
  <img src="https://dummyimage.com/600x400/000/fff">
</p>

CSS:
.thumb {
  width: 250px;
  margin-left: auto;
  margin-right: auto;
}
img {
  /* reset.css */
  max-width: 100%;
  height: auto;
  vertical-align: middle;
}
```

### ③marginを使ったやり方で左右中央寄せ

デモ：https://codepen.io/thekronos07/pen/zmOKjX

```
HTML:
<div class="wrapper">
  <div class="contents">
    <h2>タイトル</h2>
    <p>内容</p>
  </div>
</div>

CSS:
.wrapper {
  width: 100%;
  background-color: #cccccc;
}
.contents {
  width: 250px;
  background-color: #008000;
  color: #ffffff;
  margin-left: auto;
  margin-right: auto;
}
```

### ④positonを使ったやり方で左右中央寄せ

デモ：https://codepen.io/thekronos07/pen/dgbpjY

```
HTML:
<div class="wrapper">
  <div class="contents">
    <h2>タイトル</h2>
    <p>内容</p>
  </div>
</div>

CSS:
.wrapper {
  width: 100%;
  height: 800px;
  background-color: #cccccc;
  position: relative;
}
.contents {
  width: 950px;
  max-width: 950px;
  height: 500px;
  background-color: #008000;
  color: #ffffff;
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%); /* X軸 マイナス50% */
}
```

## 上下中央寄せにするやり方
### ①positonを使ったやり方で上下中央寄せ

デモ：https://codepen.io/thekronos07/pen/bmbwzL

```
HTML:
<div class="wrapper">
  <div class="contents">
    <h2>タイトル</h2>
    <p>内容</p>
  </div>
</div>

CSS:
.wrapper {
  width: 100%;
  height: 500px;
  background-color: #cccccc;
  position: relative;
}
.contents {
  width: 100px;
  height: 100px;
  background-color: #008000;
  color: #ffffff;
  position: absolute;
  top: 50%;
  transform: translateY(-50%); /* Y軸 マイナス50% */
}
```



## 上下左右中央寄せにするやり方
### ①flexを使ったやり方で上下左右中央寄せ

デモ：https://codepen.io/thekronos07/pen/MPgjpG

```
HTML:
<div class="wrapper">
  <div class="contents"></div>
</div>

CSS:
.wrapper {
  width: 100%;
  height: 550px;
  background-color: #cccccc;
  display: flex;
  align-items: center;
  justify-items: center;
}
.contents {
  /* テキストのみの場合は、text-align: center;でok */
  width: 250px;
  height: 250px;
  background-color: #333333;
  margin-left: auto;
  margin-right: auto;
}
```


### ②positonを使ったやり方で左右中央寄せ

デモ：https://codepen.io/thekronos07/pen/mzbrgW

```
HTML:
<div class="wrapper">
  <div class="contents">
    <h2>タイトル</h2>
    <p>内容</p>
  </div>
</div>

CSS:
.wrapper {
  width: 100%;
  height: 500px;
  background-color: #cccccc;
  position: relative;
}
.contents {
  width: 100px;
  height: 100px;
  background-color: #008000;
  color: #ffffff;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%); /* X軸とY軸 マイナス50% */
}
```

## 最後に
パッと思いつく対処はこれくらいですが、
中央寄せにmargin-left:-200px;みたいな指定をされてるのを見るので、
そういうのは、あまりしてほしくないですよね。

という感じで、今回は簡単に中央寄せのやり方をまとめてみました！
解説付きで、もっと詳しく知りたいという方は下記のリンク先でご覧ください。


CSSで中央寄せする9つの方法（縦・横にセンタリング）

https://saruwakakun.com/html-css/basic/centering#section1