+++
date = "2015-06-19T22:09:10+09:00"
slug = "jenkins-proxy-error-503"
title = "Jenkins で HTTP 503 が表示されたときの解決方法"
tags = ["Jenkins"]

+++

Jenkins にアクセスしたときに HTTP ステータスコード 503 が表示されたときに  
行った解決方法です。  
Jenkins は Apache のリバースプロキシーで運用しています。

```sh
# Jenkins のステータスを確認
sudo /sbin/service jenkins status
# Jenkins 再起動
sudo /sbin/service jenkins restart
# リバースプロキシで運用しているので、Apache 再起動
sudo /sbin/service httpd graceful
```
