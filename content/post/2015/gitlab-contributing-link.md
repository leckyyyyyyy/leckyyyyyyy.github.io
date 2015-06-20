+++
date = "2015-06-20T20:14:59+09:00"
slug = "gitlab-contributing-link"
title = "GitLab で issue や MargeRequest の新規作成時にガイドラインを表示するには"

+++

issue や MargeRequest を作成するとき、ルールやフォーマットなどガイドラインがあるプロジェクトではメンバーとして参加するとき説明をうけたり、別途ドキュメントとかをもらったりするかもしれませんが、作成するときには、そのガイドラインに沿っていなかったり忘れたりするときもあると思います。  

そのようなことを防ぐため？に GitHub や GitLab にはガイドライン用のファイルを指定のファイル名で作成することで、issue や MargeRequest を新規作成するときにリンクとして表示してくれます。

GitHub でのガイドラインのリンクを表示する方法は [ヘルプページ][github-help] にあります。  
GitLab では [リリースノート][gitlab-link] に機能の説明は載っていたのですが、手順については今回調べることになったのでまとめました。

リポジトリのルートディレクトリ直下にファイル名 __CONTRIBUTING.md__ または __CONTRIBUTING__ で作成。  
<small>CONTRIBUTING.md と CONTRIBUTING の両方が存在したときは CONTRIBUTING が優先されるようです。</small>

Markdown 形式のほうがファイル単体で表示するときにも見やすいので、作成するときには CONTRIBUTING.md が良さそうです。

[github-help]: https://github.com/blog/1184-contributing-guidelines
[gitlab-link]: https://about.gitlab.com/2014/03/21/gitlab-6-dot-7-released/
