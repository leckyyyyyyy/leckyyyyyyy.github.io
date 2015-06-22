+++
date = "2015-06-23T02:14:46+09:00"
slug = "centos-jdk6-to-jdk7-update"
title = "CentOS5 で JDK6 から JDK7 へのアップデート"

+++

CentOS5 環境の JDK6 を JDK7 にアップデートするときの手順です。

今回の JDK のアップデートでは一度パッケージをアンインストールしてから目的のパッケージをインストールするため、アンインストール時に __依存しているパッケージもアンインストール__ されます。  
依存しているパッケージはアンインストール時に __Removing for dependencies__ として表示されます。

```sh
# JDK6 をアンインストール
sudo yum remove java

# JDK7 をインストール
sudo yum install java-1.7.0-openjdk

# Java のバージョンを表示
java -version

# アンインストールしたパッケージが必要な場合は再インストール
```

`/var/log/yum.log` でパッケージの追加/削除/更新の確認ができるので、ログから依存していたパッケージを探せます。
