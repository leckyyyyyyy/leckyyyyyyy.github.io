+++
date = "2015-06-02T22:49:58+09:00"
slug = "checkstyle-idea-4.15.0-jdk8"
title = "CheckStyle-IDEA 4.15.0 は JDK8 が必要みたい"

+++

CheckStyle-IDEA のアップデート通知があったのでプラグインのアップデートを行うと  
`Unsupported major.minor version 52.0` のエラーが表示されました。

GitHub で公開されているので [README][link1] を確認するとエラーメッセージの対応方法が載っていました。  
どうやらバージョンアップの影響で JDK8 にアップデートする必要があるとのことです。

このままでは IDE の起動が失敗するので、JDK8 にアップデートするか、  
プラグインの一覧から `CheckStyle-IDEA` を選択してプラグインの実行を無効にする必要があります。

[link1]: https://github.com/jshiell/checkstyle-idea/blob/4.15.0/README.md#i-see-a-cannot-load-project-error-stating-unsupported-majorminor-version-520
