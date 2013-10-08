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

- SASS内に書いたコメントからドキュメントを作成
- sassdoc記法にそって書いた内容が整形されて表示される
- ドキュメント内のmixinやfunctionを検索できる
- 表示する内容のフィルター出来る(mixinのみ表示、functionのみ表示）
- テンプレートがカスタマイズ出来る ( [Dustjs](http://akdubya.github.com/dustjs)っていうテンプレートエンジン )
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

## インストール

```sh
[sudo] gem install sassdoc
```

---

## ディレクトリ構成

以下の様なディレクトリ構成

```
┣src
┃┣ style.scss
┃┗ _mixin.scss
┗docs/
```

---

## 生成してみた

- ``src``以下にある``scss``をもとに、``docs``にドキュメントを作成します。
- ドキュメントのタイトルは``俺の考えた最強のドキュメント``とします。

```
sassdoc src -d docs -n '俺の考えた最強のドキュメント'
```

---

## 生成された

```
┣src
┃┣ style.scss
┃┗ mixin.scss
┗docs/
　┣ css/
　┣ js/
　┣ tmpl/
　┣ index.html       #ドキュメントトップページ
　┃┣ nav.tmpl       #上部ナビゲーション
　┃┣ toc.tmpl       #左カラム
　┃┗ view.tmpl      #右カラム
　┗ sassdoc.json     #テンプレートで使用するデータ
```

生成された[サンプルはこちら](http://geckotang.github.io/sassdoc-tryout/docs/)

<small>※sassdoc.jsonを$.getJSONしてリッチなページにしているので、サーバー上でしか動きません。</small>

---

## まとめ

- SASSなどのプリプロセッサでできる事が他のプログラミング言語に近づいている
- ということは、他言語のようにドキュメント作成ツールは必要
- 詳しくはソース見てね！とかは悲しい…
- 既存のテンプレはどことなく見辛いので、自分で作ったほうが良さそう。




