# よろしくsassdoc

[@GeckoTang](http://twitter.com/GeckoTang)

---

## sassdocとは?

Ruby製のSASSドキュメントジェネレーターです。

[https://github.com/eoneill/sassdoc](https://github.com/eoneill/sassdoc)

何種類かあるのですが、僕は記法がjsDocToolKitに似ている[eoneill/sassdoc](https://github.com/eoneill/sassdoc)を使いました。

---

## styleDoccoとの違い

- styleDoccoはあくまでスタイルガイドなので、jsDocToolKitなどのコードのドキュメントではありません。
- @mixinや@functionの説明をかけなくはないが、なんか見辛い。
- 自由度が低い（テンプレートのカスタマイズがしにくい）

---

## sassdocができる事

- ドキュメント内のmixinやfunctionを検索できる
- 表示する内容のフィルター(mixinのみ表示、functionのみ表示）
- カスタマイズ出来るテンプレート ( [Dustjs](http://akdubya.github.com/dustjs)っていうテンプレートエンジン )

---

## インストール

```sh
[sudo] gem install sassdoc
```

---

## こんな記法

styleDoccoとは違い、行コメントの中に独自の記法でかく

``` javascript
// @mixin pointer-events
// @param $value {String} [none|auto]
// @usage:
// .link.disabled{
//  =pointer-events(none);
// }
@mixin pointer-events($value:none) {
  -webkit-pointer-events: $value;
  pointer-events: $value;
}
```

jsDocToolKitっぽい書き方が出来ます。
<small>（=pointer-events..と書いているのは@usageの中に@が使えない都合でSASS記法になっています）</small>

---

## 生成してみた

以下の様なディレクトリ構成

```
┣src
┃┣ style.scss
┃┗ mixin.scss
┗docs
```

- ``src``以下にある``scss``をもとに、``docs``にドキュメントを作成します。
- ドキュメントのタイトルは``俺の考えた最強のドキュメント``とします。

```
sassdoc src -d docs -n '俺の考えた最強のドキュメント'
```

生成された[サンプルはこちら](http://geckotang.github.io/sassdoc-tryout/docs/)

---


- 指定された記法で書かれたコメントの部分を抽出して、ページ表示用のjsonを作成します。
- なのでsassdoc記法でかかれてないstyle.scssの内容はドキュメントには反映されません
- SCSS内に書かれているコメント以外の物は使用してなさそうなので、styleDoccoとの共存も可能かと思います。

