# よろしくsassdoc

[@GeckoTang](http://twitter.com/GeckoTang)

---

## sassdocとは

Ruby製のドキュメントジェネレーターです。

[https://github.com/eoneill/sassdoc](https://github.com/eoneill/sassdoc)

何種類かあるのですが、僕は記法がjsDocToolKitに似ている[/eoneill/sassdoc](https://github.com/eoneill/sassdoc)を使いました。

---

## styledoccoとの違い

- styleDoccoはあくまでスタイルガイドなので、jsDocToolKitなどのコードのドキュメントではありません。
- @mixinや@functionの説明をかけなくはないが、なんか見辛い。
- 検索もできないし。
- テンプレートのカスタマイズがしにくい

---

## sassdocができる事

- ドキュメント内からの検索
- 表示する内容のフィルター(mixinのみ表示、functionのみ表示）
- カスタマイズ出来るテンプレート [Dustjs](http://akdubya.github.com/dustjs)っていうテンプレートエンジン

---

## インストール

```sh
[sudo] gem install sassdoc
```

---

## 記法

styledoccoとは違い、コメントアウトの中に独自の記法でかく
jsDocToolKitっぽい書き方が出来ます。

---

## 使ってみた

生成された[サンプルはこちら](http://geckotang.github.io/sassdoc-tryout/docs/)

```
┣src
┃┣ style.scss
┃┗ mixin.scss
┗docs
```

``src``以下にある``scss``をもとに、``docs``にドキュメントを作成します。

ドキュメントのタイトルは``俺の考えた最強のドキュメント``とします。

```
sassdoc src -d docs -n '俺の考えた最強のドキュメント'
```

---


指定された記法で書かれたコメントの部分を抽出して、ページ表示用のjsonを作成します。

なのでsassdoc記法でかかれてないstyle.scssの内容はドキュメントには乗っていません。

SCSS内に書かれているコメント以外の物は使用してなさそうなので、styleDoccoとの共存も可能かと思います。

---

## さらにできる事

- StyleDoccoと違い、ドキュメントのカスタマイズが容易です！
