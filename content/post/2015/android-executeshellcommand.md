+++
date = "2015-07-09T23:25:36+09:00"
slug = "android-executeshellcommand"
title = "UiAutomation#executeShellCommand は 5.0 から利用可能なメソッドだった"
tags = ["Android"]

+++

UI Automator(コード上) で `adb shell` を利用したいとき、ちょうど良いメソッド `UiAutomation#executeShellCommand` を見つけたのですが、利用できるのは __API level 21__ からでした。  
ビルドしようにもメソッドが存在しない旨のメッセージが表示されてエラーになって困っていましたが、落ち着いて確認するとターゲットにしているバージョンが違っていました。  
入力補完のメソッド一覧に表示されたけど利用できなかったのですね。失敗した。

調べている最中に見つけた URL 忘れるともったいないので  
[Android 5.0 API の紹介(テストとユーザー補助)](https://developer.android.com/intl/ja/about/versions/android-5.0.html#TestingA11y)  
[リファレンス UiAutomation#executeShellCommand(java.lang.String)][executeShellCommand]  
[Android API Differences Report](https://developer.android.com/intl/ja/sdk/api_diff/21/changes.html)

API の紹介や API の相違点のページにも今回欲しかった情報がありました。調べるときにネットでよく彷徨い続けることがあるので、気をつけないと。  
迷わないようにまずは公式から探します。

[executeShellCommand]: https://developer.android.com/intl/ja/reference/android/app/UiAutomation.html#executeShellCommand(java.lang.String)
