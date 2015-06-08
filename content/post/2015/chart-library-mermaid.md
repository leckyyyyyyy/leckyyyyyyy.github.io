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
```
<script type="text/javascript">
mermaid.ganttConfig = {
  numberSectionStyles: 2
}
</script>
```
を追加

#### チャートを書く

```
<div class="mermaid">
// ここにチャートの定義を書きます
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
