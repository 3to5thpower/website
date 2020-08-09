---
title: "ブログ立てました"
date: 2020-08-09T00:17:04+09:00
tags: ["blog", "Hugo"]
categories: ["technologies"]
#description: "このブログを立てた経緯と作業の詳細"
#images: 
#    - src: "img/tech/gohugoio-card.png"
draft: false
---

初めまして。3^5です。  
今回初めてブログを立てたので
作業の詳細について書いていこうと思います。  
使ったのはGoで書かれた静的サイトジェネレータ[Hugo](https://gohugo.io/)です。
{{< figure src="/img/tech/gohugoio-card.png" class="center" >}}

個人的にRustが好きなので
Rust製の静的サイトジェネレータの[Zola](https://www.getzola.org/)を使おうとも考えたのですが、  
使っている人口的に資料やテーマの数が少なかったためHugoを選びました。  
実際ツール使うだけなので書かれてる言語は速度面以外だとほとんど関係ないですね。  
テーマはとりあえず[hugo-future-imperfect-slim](https://themes.gohugo.io/hugo-future-imperfect-slim/)を使っています。

ブログを立てるまでに行った作業はこんな感じです。
1. Hugoのインストール
2. リポジトリの初期化
3. ドメインを取る
4. GitHub Pagesの設定
5. 記事を書く

それぞれの詳細を解説していきます。

### 1.Hugoのインストール
僕は普段使っている環境がArch Linuxなのでそのままパッケージマネージャで導入しました。  
```
yay -S hugo
```
Ubuntuなんかでもaptに入ってるっぽいので多分大丈夫だと思います。

### 2.リポジトリの初期化
新しいサイトの生成は次のコマンドで行います。  
```
hugo new site mysite
```
mysiteのところは好きな名前にしてください。

次に、テーマの追加をします。  
https://themes.gohugo.io/で好きなテーマを選び、  
先ほど初期化したディレクトリ(ここではmysite)の中のthemes/に引っ張ってきます。
```
mkdir themes
cd themes
git submodule add https://github.com/pacollins/hugo-future-imperfect-slim.git
```

ここからは選んだテーマによって作業が大きく異なりそうですが、  
僕はダウンロードしてきたテーマのexampleSiteを書き換えながら作業を始めようと思い、  
まずこれを作業ディレクトリのルートに展開しました。
```
cp -r themes/hugo-future-imperfect-slim/exampleSite/* ./
```
cpで変なファイル消されると怖いので、  
-iコマンドを付けてファイルを上書きするときに確認させてもいいと思います。

これで`hugo server -D`を実行するとサンプルサイトがlocalhostで立ち上がります。  
contents以下が記事なので好きなように作り換えていきましょう。  
新しい記事は`hugo new blog/first.md`とかやると生成できます。

僕が採用したテーマは多言語対応だったので日本語を選択しそれ以外を消したのですが、  
日本語も微妙だったので書き換えました。  
(Aboutが約とかになっている時点でまあそうですよねーとなりました)

Hugoはユーザが書いた設定を優先して見に行くので  
`themes/hugo-future-imperfect-slim/layout/i18n/ja.toml`を  
`/i18n/ja.toml`にコピーしていろいろ書き換えています。  

### 3.ドメインを取る
好きに取ってください。
僕はGoogle Domainsで取りました。  
取ったらDNS設定のところでGitHubのレコードを登録します。  
{{< figure src="/img/tech/github-ip.png" >}}

登録するレコードはこの4つです。  
ただしこれは2020年8月のものなのでちゃんと確認してから追加しましょう。  


### 4.GitHub Pagesの設定
GitHub Pagesは静的サイトを無料で公開できるホスティングサービスです。  
独自ドメインも設定できるので、先程買ったものが使えます。  

今作業しているディレクトリをGitHubのリポジトリにpushしたら、  
リポジトリのsettings/options/GitHub Pagesから設定できます。  

{{< figure src="/img/tech/github-pages-settings.png" >}}

### 5.記事を書く
好きに書きましょう。  
あとは公開するだけです。

***
## 終わりに
こんな感じでブログ立てました。  
本当はVPS借りてサーバ立ててやろうという意気込みがあったのですが、  
~~そして実際に途中までやっていましたが、~~  
結局面倒くさくなってこっちにしました。  
まあコストが低いほうが長続きもしそうなので、ゆるーくやっていきたいと思います。  


読んでいただいてありがとうございました！