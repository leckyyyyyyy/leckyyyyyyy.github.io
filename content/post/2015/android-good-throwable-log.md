+++
date = "2015-07-13T23:20:09+09:00"
slug = "android-good-throwable-log"
title = "Android で Throwable を表示するなら printStackTrace() より Log.*()"
tags = ["Android"]

+++

Android で try-catch ステートメントを利用したときに Throwable 型の変数がセットでついてくるので、とりあえず `printStackTrace()` を呼び出していました。実際に呼び出されたときは Android Studio の LogCat では表示されず放置気味でした。(よろしくない習慣)

`Log.*()` を利用するときも第2引数までしか利用しておらず、デバッグのときにあまり役立っていませんでしたが、`Log.*()` の第3引数に catch ステートメントで捕捉したときに渡される Throwable 型の変数を渡せることに気付いたので、最近は第3引数に渡しています。

第3引数に渡すことで printStackTrace() を呼び出したときに出力される内容が LogCat で確認できます。  
ProGuard で難読化するときに削除することもできるので、扱いやすいかと思います。
