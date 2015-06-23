+++
date = "2015-06-24T00:30:12+09:00"
slug = "android-espresso-ondata-indexoutofboundsexception"
title = "Android の Espresso.onData で java.lang.IndexOutOfBoundsException が発生したときは"
tags = ["Android"]

+++

Android の UI テストフレームワーク Espresso を利用しているときに Espresso.onData で `java.lang.IndexOutOfBoundsException` が発生したときは参照している Adapter の `getCount`、`getItem` の実装を確認してみましょう。

Espresso.onData で参照する Adapter の [データを取得している箇所][code] で `getCount` を呼び出しているのですが、例外が発生したコードでは getCount の返す値がデータのリストの長さを返していませんでした。  
getItem はデータのリストを参照していたので、つじつまが合わず例外が発生していました。

getCount、getItem は Adapter が保持するデータのリストを参照するはずなのですが、今回は全く異なる処理が組み込まれていたのでハマりました。  
メソッドをオーバーライドするときは、メソッドの本来の役割を理解した上で実装しないと痛い目にあいますね。

[code]: https://code.google.com/p/android-test-kit/source/browse/espresso/lib/src/main/java/com/google/android/apps/common/testing/ui/espresso/action/AdapterViewProtocols.java#49
