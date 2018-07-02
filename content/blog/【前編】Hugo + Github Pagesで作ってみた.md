+++
author = "kinko25"
categories = ["Hugo","Github","Github Pages"]
tags = ["hugo"]
date = "2018-06-29"
description = "Github Pagesにブログを開設してみた。"
featured = "pic01.png"
featuredalt = ""
featuredpath = "date"
linktitle = ""
title = "【前編】Hugo + Github Pagesで作ってみた"
type = "post"

+++

# Github Pagesにブログを開設してみた。
## 無料サーバーでブログを運営したい。

「金払ってワードプレスで作るのも、勿体無い。。。」
「はてなブログなどは楽だけど、自由度が。。。。」と思い、Github Pagesを使って、
ブログを開設してみました。

最初、Jekyllでやろうとしましたが、Windowsとの相性が悪いって書かれてたので、

Hugoでやることに。

出来上がってから、Jekyllをchocolateyでできるっぽいことを知ったのですが、
もう作ってしまったものはしょうがないので、

「Jekyllでやりたい！」という人は試してみてはどうでしょう。


テーマ一覧を見ると、Jekyllの方が充実してると思う。

Hugoテーマリスト：

https://themes.gohugo.io/


jekyllテーマリスト ：

http://jekyllthemes.org/

Hugoはデザイン的に、なんだかイケてないというか・・・。ｗ


## Hugoとは？

・golangで作られた静的ジェネレーター

・他のツールのように、デプロイコマンドがない

・HTML/CSSを出力する動作が早い

かなりざっくりですが。

## メリット

・ワードプレスのようなログインがない

・テーマの自由度

・記事作成後にコマンド一回叩けば本番反映される

・Github Pagesを使ってるので無料

・デフォルトのドメインであれば、SSL化されてる

などなどｗ

## 環境

・Windows7 64bit

・git

・chocolatey

・ターミナルはbash

## まず、環境構築

では、早速インストールした手順をざっくり紹介していきます。

Hugoを使うきっかけはこれ。

https://onoxeve.com/posts/hugo-on-github-pages/


上記の記事内では、Homebrewを紹介しているが、WindowsではHomebrewを使えないため、

この記事では、Windowsを使っている人向けになります。

Homebrewの代わりとなるchocolateyをコマンドプロンプトから入れた。
```

## 下記のコマンドをコピペで入力。
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
```
参考URL：https://chocolatey.org/install#installing-chocolatey
インストール後、VS codeの再起動を行い、ターミナルでchocolateyコマンドを叩けば、VS codeでも使えることがわかる。


## Hugoを入れる

chocolateyコマンドが使えるのを確認後、
```
# 上記の工程が完了したら、ターミナルで下記コマンドを叩いてください。
$ choco install hugo
```

hugoのインストールが完了したら
ターミナルでgit管理するディレクトリを作成していきます。
```

##「blog」の部分は、ディレクトリ名になるので任意で
$ mkdir blog

## 現在いる階層の全ディレクトリを表示
## 表示された一覧の中にblogがあれば作成完了です。
$ ls -la

## 作成されたのが確認できたら、
## 下記、コマンドで作成したディレクトリに入ります。
$cd blog

```

## Hugoのテーマを入れる

あとは好きなテーマを選択して
「Download」クリックして、
githubの「Clone or download」をクリック。
出てきたURLをコピー。

ターミナルで、themeの中に入り、
```
$ cd theme
$ git clone https://github.com/jpescador/hugo-future-imperfect.git
```

cloneしたファイルの一部を指定のディレクトリにコピペしていく。

こちらを参考にしてください。
```
https://qiita.com/bake0937/items/e0914efbd9434be474a4#examplesite%E3%83%87%E3%82%A3%E3%83%AC%E3%82%AF%E3%83%88%E3%83%AA%E3%81%AE%E3%82%B3%E3%83%B3%E3%83%86%E3%83%B3%E3%83%84%E3%82%92%E3%82%B3%E3%83%94%E3%83%BC
```

移動が完了したら、hugoのコマンドたたけば表示される

例:

```
## build 本番公開用
$ hugo

## Watch　ローカル用　※ローカルで確認するならこれ
$ hugo server
```

## githubにSSH公開鍵を登録する。
実際、私はここで少しだけ詰まってましたｗ
本番公開する際に、必要になってくるので、
登録しておいてください。

下記、リンク先を参考にしていただければ、うまく行きます。

gitHubでssh接続する手順~公開鍵・秘密鍵の生成から~ 

https://qiita.com/shizuma/items/2b2f873a0034839e47ce


## blogディレクトリをgit管理する

```
$ git init #blogディレクトリ内で、このコマンドを実行。
$ git remote add origin git@github.com:ユーザー名/リポジトリ名.git # remoteのリポジトリを設定する
$ git pull origin master
$
$ rm -rf public # このディレクトリは git subtree を利用して管理するので削除
$ git add -A
$ git commit -m "Add hugo template"
$ git push origin master
```
上記のコマンドをコピペでいけます。
※コメントは消してくださいね。

## gh-pagesブランチを作成する

```
$ git checkout --orphan gh-pages   # orphan ブランチ 作成
$ git rm --cached $(git ls-files)  # 要らないので、全て管理対象からすべて外す
$ git add README.md                # README.md だけいれておく
$ git commit -m "initial commit on gh-pages branch"
$ git push origin gh-pages

$ git checkout master
$ git subtree add --prefix=public git@github.com:ユーザー名/リポジトリ名.git gh-pages --squash
$ git subtree pull --prefix=public git@github.com:ユーザー名/リポジトリ名.git gh-pages

$ hugo # buildします
$ git add -A
$ git commit -m "Updating site"
$ git push origin master
$ git subtree push --prefix=public git@github.com:ユーザー名/リポジトリ名.git gh-pages
```

## 更新を自動化する
./blog/の階層で
```
touch deploy.sh
deploy.sh　←これをエディターで開いてください。
```

開いたら、下記の内容をコピペして保存。
```
# !/bin/bash

echo -e "\033[0;32mDeploying updates to GitHub...\033[0m"

# Build the project. 
hugo

# Add changes to git.
git add -A

# Commit changes.
msg="rebuilding site `date`"
if [ $# -eq 1 ]
  then msg="$1"
fi
git commit -m "$msg"

# Push source and build repos.
git push origin master
git subtree push --prefix=public git@github.com:[username]/yourblog.git gh-pages
```
上記の内容を保存したら、
下記のコマンドを実行してリモートのリポジトリに反映する
```
$ chmod +x deploy.sh
$ ./deploy.sh
```

これが完了したら
```
https://ユーザー名.github.io/リポジトリ名/
```
で、ちゃんと開けば、本番反映成功です。


## Hugoのテーマをカスタムする
サイト名などをいじっていきましょう。
基本的に、config.tomlのファイルをいじるので、
下記のリンク先を参考にしていじってみてもいいと思います。
まぁ、ぐぐればこの辺のことは大体出てきますので。
```
https://qiita.com/bake0937/items/e0914efbd9434be474a4#%E3%82%AC%E3%83%81%E3%83%A3%E3%82%AC%E3%83%81%E3%83%A3%E5%8B%95%E3%81%8B%E3%81%97%E3%81%A6%E3%81%BF%E3%82%8B
```
長いので、今回はこの辺で。
ありがとうございました。