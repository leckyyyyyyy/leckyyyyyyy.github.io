+++
date = "2015-07-11T23:54:32+09:00"
slug = "git-pushpull-https-self-signed"
title = "Git push/pull を HTTPS でアクセスすると自己署名ではエラーになる"

+++

Git の push/pull を HTTPS のアクセスで行うと自己署名のサーバ証明書ではデフォルトはエラーになり、アクセスできない。  
アクセスできるようにするためには設定を変更する必要がある。

__特定のリポジトリのみ変更__  
`git config --local http.sslVerify false`

__デフォルトの設定を変更__  
`git config --global http.sslVerify false`

意図的にセキュリティに関する設定を変更するので、実際に行うときは留意する必要があります。  
HTTPS に利用するサーバ証明書は自己署名ではないものを利用するのが望ましいですが、やむを得ないときもあるので、そのようなときにはこの対応が必要になるかと思います。
