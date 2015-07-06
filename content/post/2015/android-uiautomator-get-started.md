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
}

dependencies {
  androidTestCompile 'com.android.support.test:runner:0.3'
  androidTestCompile 'com.android.support.test:rules:0.3'
  androidTestCompile 'com.android.support.test.uiautomator:uiautomator-v18:2.1.1'
}
```

Android Studio から実行するときは __Edit Configurations...__ から __Android Tests__ を選択し __+__ を押して追加後「Name:」に任意の名前を入力「Module:」に app を選択して作成します。  
メニューの __Select Run/Debug Configuration__ で作成した Android Tests を選択し「実行」します。

コンソールから実行するときは `./gradlew connectedCheck` を実行します。  
`[プロジェクト]/app/build/reports` 下にレポートも作成されます。  
<small>gradlew で実行できるのは UI Automator バージョン 2 からです</small>

### サンプルコード

```java
package com.example.android.testing;

import android.content.Context;
import android.content.Intent;
import android.support.test.InstrumentationRegistry;
import android.support.test.filters.SdkSuppress;
import android.support.test.runner.AndroidJUnit4;
import android.support.test.uiautomator.By;
import android.support.test.uiautomator.UiDevice;
import android.support.test.uiautomator.UiObject2;
import android.support.test.uiautomator.Until;
import android.support.v7.widget.LinearLayoutCompat;
import android.test.suitebuilder.annotation.LargeTest;

import org.hamcrest.CoreMatchers;
import org.junit.Assert;
import org.junit.Before;
import org.junit.Test;
import org.junit.runner.RunWith;

@RunWith(AndroidJUnit4.class)
@SdkSuppress(minSdkVersion = 18)
@LargeTest
public class UIAutomatorTest {

    private static final String APP_PACKAGE = "com.example.android.testing";

    private static final int LAUNCH_TIMEOUT = 5000;

    private static final int UI_TIMEOUT = 5000;

    private UiDevice device;

    /**
     * アプリケーション起動に必要なIntentを作成
     *
     * @param context     {@link InstrumentationRegistry#getContext()} テスト実行のアプリケーション
     * @param packageName アプリケーションのパッケージ名
     * @return アプリケーション起動用Intent
     */
    public static Intent createLaunchIntent(Context context, String packageName) {
        final Intent intent = context.getPackageManager()
                .getLaunchIntentForPackage(packageName);
        intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TASK);

        return intent;
    }

    @Before
    public void setUp() {
        device = UiDevice.getInstance(InstrumentationRegistry.getInstrumentation());

        device.pressHome();

        Context testContext = InstrumentationRegistry.getContext();
        final Intent intent = createLaunchIntent(testContext, APP_PACKAGE);
        testContext.startActivity(intent);

        device.wait(Until.hasObject(By.pkg(APP_PACKAGE).depth(0)), LAUNCH_TIMEOUT);
    }

    @Test
    public void 前提条件() {
        Assert.assertThat(device, CoreMatchers.is(CoreMatchers.notNullValue()));
    }

    @Test
    public void Hello_worldが表示されること() {
        UiObject2 textView
                = device.wait(Until.findObject(By.text("Hello world!")), UI_TIMEOUT);

        Assert.assertThat(textView.getText(), CoreMatchers.is("Hello world!"));
    }

    @Test
    public void Action_overflowを押してSettingsが表示されること() {
        UiObject2 actionOverflow
                = device.wait(Until.findObject(By.clazz(LinearLayoutCompat.class)), UI_TIMEOUT);

        actionOverflow.click();
        device.waitForIdle();

        UiObject2 menu
                = device.wait(Until.findObject(By.text("Settings")), UI_TIMEOUT);

        Assert.assertThat(menu.getText(), CoreMatchers.is("Settings"));
    }
}
```

参考 URL  
https://developer.android.com/intl/ja/tools/testing-support-library/index.html#UIAutomator  
https://plus.google.com/+AndroidDevelopers/posts/WCWANrPkRxg
