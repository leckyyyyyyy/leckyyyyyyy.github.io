+++
date = "2015-07-01T00:24:56+09:00"
slug = "yum-package-exclude"
title = "yum でアップデートするときに指定のパッケージを除外する"

+++

yum でパッケージのアップデートをするときなどに指定のパッケージを除外したいことがありました。特定のバージョンを使い続ける事情があったので yum のオプションを探してみたところ `exclude` でパッケージの除外を行えるようです。  

```sh
-x, --exclude=package
Exclude a specific package by name or glob from updates on all repositories.  Configuration Option: exclude
```

コマンド例  
`yum update --exclude=[パッケージ名]`  
[パッケージ名]に `*` を含めることで前後/部分一致を行えるようです。
