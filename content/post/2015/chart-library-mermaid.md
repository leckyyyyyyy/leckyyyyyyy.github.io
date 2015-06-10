+++
date = "2015-06-09T01:46:12+09:00"
slug = "chart-library-mermaid"
title = "Markdown でダイアグラム、フローチャートを作成できる JavaScriptライブラリ mermaid を使ってみた"

+++

<script type="text/javascript" src="https://rawgit.com/knsv/mermaid/0.4.0/dist/mermaid.full.min.js"></script>
<link rel="stylesheet" type="text/css" href="https://rawgit.com/knsv/mermaid/gh-pages/css/mermaid.css">
<script type="text/javascript">
mermaid.ganttConfig = {
  numberSectionStyles: 2
}
</script>

[mermaid.jsが素晴らしいけどなかなか使ってる人見かけないので実例晒す](http://qiita.com/uzuki_aoba/items/a01f8b0b52ced69c8092) を見て  
JavaScriptライブラリをインポートして早速チャートを mermaid で作成したときの内容です。

#### チャートを書く前に

`<script type="text/javascript" src="https://rawgit.com/knsv/mermaid/0.4.0/dist/mermaid.full.min.js"></script>`  
`<link rel="stylesheet" type="text/css" href="https://rawgit.com/knsv/mermaid/gh-pages/css/mermaid.css">`  
または上記2つのファイルをダウンロードしてリンク先に設定する。

```
<script type="text/javascript">
mermaid.ganttConfig = {
  // 1～ の場合はガントチャートで色分けされる。0 の場合はモノクロ。
  numberSectionStyles: 2
}
</script>
```
を追加

#### チャートを書く

```
<div class="mermaid">
// ここにチャートの定義を書くことで、この部分にチャートが描画されます。
</div>
```

#### チャートのデモ

フローチャート

```
<div class="mermaid">
graph LR
  画面1 --> 画面2
  画面2 --> 画面3
  画面1 --> 画面4
</div>
```

<div class="mermaid">
graph LR
  画面1 --> 画面2
  画面2 --> 画面3
  画面1 --> 画面4
</div>

ガントチャート

```
<div class="mermaid">
gantt
  title Webサイト作業スケジュール
  
  section 画面1
  デザイン       :a1, 2015-06-09, 10d
  プログラム開発 :a2, after a1, 10d
  テスト         :a3, after a2, 5d
</div>
```

<div class="mermaid">
gantt
  title Webサイト作業スケジュール
  
  section 画面1
  デザイン       :a1, 2015-06-09, 10d
  プログラム開発 :a2, after a1, 10d
  テスト         :a3, after a2, 5d
</div>

[mermaid](https://github.com/knsv/mermaid) の [セットアップ方法](http://knsv.github.io/mermaid/usage.html) やチャート作成に必要な定義、[デモ](http://knsv.github.io/mermaid/demos.html) も見ながら書いてみました。  

__チャートの定義が間違っていると描画する部分には何も表示されません__ 表示されないときはブラウザのコンソールにエラーが表示されるので手助けになるかもしれないです。

日本語を含めても表示されていました。  
チャートのスタイルは CSS で変更できるので、必要に応じて変更できますね。  
(今回、読み込んでいるのは mermaid のドキュメントを利用しています。デフォルトのスタイルが見つけられなかった。)

Chrome ではフローチャート、ガントチャートどちらも表示されていますが、他のブラウザでは日本語が表示されなかったり、チャート自体が表示されないようです。  
パスの矢印が Chrome, Firefox で表示されていないのですが、他のページで試したところ表示はされていたので、スタイルが要因かもしれません。

* フローチャート
    * IE11  
    日本語が表示されない
    * Chrome, Firefox  
    パスの矢印が表示されない?
* ガントチャート
    * Firefox  
    チャートが表示されず、定義した内容が表示される
