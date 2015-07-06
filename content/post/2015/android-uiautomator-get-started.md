+++
date = "2015-07-04T22:30:00+09:00"
slug = "android-uiautomator-get-started"
title = "Android UI Automator の始め方"
tags = ["Android"]

+++

UI Automator は Android 標準の UI テストツールです。  
UI テストは主にボタンをタップしたり、文字を入力するなどの操作をして特定のメッセージが表示される / 指定の画面が表示されるなど期待した結果になっているか確認することです。  
ボタンをタップする、文字を入力するなどの操作部分をコードとして記述できるよう UI Automator がサポートしてくれます。

テキストボックスに文字を入力してボタンを押すと次の画面を表示する、エラーメッセージを表示するなど決まった動作を確認 / テストする場合は導入しやすくコードとして記述しやすいです。  
一度コードにしたものは「実行」するだけで同じ操作を繰り返し行ってくれるので、アプリケーションコードに変更を加えたタイミングで「実行」するなど定期的に行うことで何か間違いがあっても気付きやすくなると思います。  
単調な操作を手動で複数回行うことはツライものがありますし、アプリケーションによっては操作するパターンが何十ともあると時間的にも精神的にもツラくなります。

UI に関する操作でもスクロールが遅い / 速いやボタンをタップしたときのエフェクトなど直感的な内容に影響する部分はコードとして記述したり確認することは難しいため、手動で対応するしたほうが良い場合もあります。

コードに置き換えが可能な部分は置き換えて、手動で行う必要がある部分に時間を割けるようにすることで、開発がより良くなると思います。

### 実行環境

UI Automator は 4.3 (API level 18) 以上のデバイスのみで利用できます。

### 導入方法

UI Automator を導入するには Gradle で定義します。
```gradle
android {
  defaultConfig {
    testInstrumentationRunner "android.support.test.runner.AndroidJUnitRunner"
  }

  packagingOptions {
    // 同じパスのファイルが複数のライブラリに存在するときビルドでエラーとなるため除外するパスを指定
    exclude 'LICENSE.txt'
  }
}

dependencies {
  androidTestCompile 'com.android.support.test:runner:0.3'
  androidTestCompile 'com.android.support.test:rules:0.3'
  androidTestCompile 'com.android.support.test.uiautomator:uiautomator-v18:2.1.1'
}
```
