+++
date = "2015-07-04T22:30:00+09:00"
slug = "android-uiautomator-get-started"
title = "Android UI Automator の始め方"
tags = ["Android"]

+++

ボタンをタップしたり、文字を入力するなどの操作をコードとして作成することで記述された内容が自動で実行されます。

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
