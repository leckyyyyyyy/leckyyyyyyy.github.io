+++
date = "2015-06-07T00:53:59+09:00"
slug = "read-github-contents"
title = "GitHub のコンテンツをリンクで読み込めるようにする"

+++

GitHub で公開されている JavaScript ライブラリや CSSファイルを利用したいとき  
zip ダウンロードして必要なファイルを抜き出す。GitHub で Raw モードで開いて保存。  
ということをしておりましたが、これだとファイルを手元に置いておく必要があるので  
試用するときにファイルとして置くのは避けたいなと感じていました。

GitHub で Raw モードで開いたときの URL を読み込み先のリンクに利用できるカナと  
思ったのですが、Content-Type が `text/plain` で返ってくるのでブラウザに解釈して  
もらうには都合が悪いです。

その辺りも含めてお助けしてくれるサービス [RawGit][home] を知りました。

使い方は

1. 読み込むファイルを Raw モードで開き、URL をコピー
1. コピーした URL を [RawGit][home] の `Paste a GitHub file or gist URL here.` に貼り付け
1. __Use this URL for dev/testing__ のテキストボックスに URL が現れるのでコピー

コピーした URL を読み込み先の URL として設定するだけ。

開発やテストなど小さな規模での利用用途なら良さそうです。  
[FAQ][faq] に用途に関することも載っていました。

[home]: https://rawgit.com/
[faq]: https://rawgit.com/faq
