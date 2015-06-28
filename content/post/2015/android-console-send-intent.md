+++
date = "2015-06-28T17:02:12+09:00"
slug = "android-console-send-intent"
title = "オリジナルの URL スキームを設定したアプリをコンソールから Intent を投げて起動する"
tags = ["Android"]

+++

オリジナルの URL スキームを設定したアプリを起動するとき、ブラウザのリンクを開く方法がありますが、その場合 HTML を用意してブラウザからアクセスする必要があります。  
起動を確認するのが目的の場合、コンソールから Intent を送信することでアプリの起動を確認することができます。

__コンソールから Intent を送信する手順__

1. コンソールを起動
1. コンソールで `adb shell` を実行して端末に接続
1. コンソールで `am start -a android.intent.action.VIEW -d "test://example.com"` を実行

URL スキームに対応するアプリが起動するようになります。  
`-d` の後ろの文字列を `""` で囲っているのは URL に & が含まれている場合 & 以降の文字列が認識されないため、渡せるように囲っています。

__AndroidManifest.xml の設定例__

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="package" >

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:theme="@style/AppTheme" >
        <activity
            android:name=".MainActivity"
            android:label="@string/app_name" >
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
            <intent-filter>
                <action android:name="android.intent.action.VIEW" />

                <category android:name="android.intent.category.DEFAULT" />
                <category android:name="android.intent.category.BROWSABLE" />
                <data android:scheme="test" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```
