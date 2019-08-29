## Overview

- [Parcel の公式ページ(日本語対応)](https://ja.parceljs.org)

Parcel は、使用されるファイルの拡張子をみて必要であればそのファイルのコンパイルをして自動で連携してくれるもの。  
Pug, Sass, SCSS, TypeScript はもちろん、CoffeeScript や Stylus や Elm, Vue.js や Rust や GraphQL まであるそうです。

爆速でコンパイルしてくれて、ちゃんとエラーも返してくれるし、ホットリロードのサーバーを立ち上げてくれるのでリロードする必要がないしロードも待たなくていい。  
それでいて、インストールもめちゃ簡単、一つグローバルにインストールするだけ。

今まで Gulp や Webpack はとても便利で一度設定ファイルを書けば、毎回それをコピーして使えばそこまで頑張らなくても開発環境はすぐに構築できる。  
しかし最初の開発環境の構築やちょっと違った構成を作りたいときに時間がかかりすぎる。これを解決してくれるツール

## Install

```bash
yarn global add parcel-bundler
# or
npm install -g parcel-bundler
```

## How to use

まず開発環境のディレクトリ構成は以下のようにします。

```
.
├── index.pug
├── page.pug
├── sass
│   └── style.sass
├── test
│   └── index.pug
└── ts
    └── script.ts
```

`index.pug`は以下のような感じです。

```
doctype html
html(lang="ja")
  head
    meta(charset="UTF-8")
    meta(name="viewport", content="width=device-width, initial-scale=1.0")
    meta(http-equiv="X-UA-Compatible", content="ie=edge")
    title Document
    link(rel="stylesheet", href="/sass/style.sass")
  body
    h1.red page
    script(src="/ts/script.ts")
```

### 実行

基本の使い方は 1 ファイルだけ実行

```bash
parcel index.pug
```

今回のように複数ファイル実行したいときは以下

```bash
❯ parcel src/**/*.pug
# 以下は出力結果
Server running at http://localhost:1234
✨  Built in 17ms.
```

### 注意点

ブラウザで index.html にアクセスするときは、ちゃんと index.html まで記入してアクセスする必要がある。

## オプション

ブラウザの起動をしなくてもいいとき

```
parcel watch src/**/*.pug
```

出力するディレクトリをデフォルトの dist から public に変えたいとき

```
parcel src/**/*.pug -d public
```
