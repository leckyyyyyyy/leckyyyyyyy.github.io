+++
date = "2015-05-28T00:34:08+09:00"
slug = "confirm-installed-package-yum"
title = "yum でインストール済みのパッケージを確認する"

+++

`yum list installed`

検索文字列を指定することで条件に一致するパッケージを表示する

```
# パッケージ名の先頭が java と一致するもの(前方一致)
yum list installed "java*"

# パッケージ名の末尾が java と一致するもの(後方一致)
yum list installed "*java"

# パッケージ名に java が含まれるもの(部分一致)
yum list installed "*java*"
```
