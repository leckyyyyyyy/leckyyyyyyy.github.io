+++
date = "2015-05-30T16:19:48+09:00"
slug = "android-product-flavor-unavailable-name"
title = "Android Product Flavor で利用できない名前"
tags = ["Android"]

+++

Product Flavor の名前に BuildType で定義している名前は利用できない。  
`ProductFlavor names cannot collide with BuildType names` のエラーが出る。

`release` はデフォルトで定義されているので気付いたけど、  
`debug` を定義してみると同じエラーが出たので、予約されているようです。
