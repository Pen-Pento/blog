---
title: '【GitHub Pages】カスタムドメインがリセットされちゃうのよぉ！'
excerpt: 'excerptexcerptexcerpt'
coverImage: '/assets/blog/dynamic-routing/cover.jpg'
date: '2022-03-26T05:35:07.322Z'
author:
  name: Pento
  picture: '/assets/blog/authors/jj.jpeg'
ogImage:
  url: '/assets/blog/dynamic-routing/cover.jpg'
---

このブログはGitHub Pagesを利用して配信しているのですが、配信するたびにカスタムドメイン設定がリセットされるため困っていました。
再設定は簡単なのでまあいいかと思っていましたが、記事の投稿、サイトの改修頻度が上がるにつれて煩わしくなってきたのでようやく重い腰を上げて修正しました。

下記のように毎度設定が空に
![GitHub Pagesセッティング](/assets/blog/github-actions-create-cname/github-actions-create-cname_1.png)

そもそも都度設定をしなきゃいけないわけないので確実に設定漏れ。とりあえずGitHub Pagesの[トラブルシューティング](https://docs.github.com/ja/pages/configuring-a-custom-domain-for-your-github-pages-site/troubleshooting-custom-domains-and-github-pages)を確認

![GitHubリファレンス](/assets/blog/github-actions-create-cname/github-actions-create-cname_2.png)

ど頭にあったw 確認ミスも確認ミス。

> サイトが正しいドメインをレンダリングするには、CNAME ファイルがまだリポジトリに存在していることを確認します。 たとえば、静的サイトジェネレータの多くはリポジトリへのプッシュを強制するので、カスタムドメインの設定時にリポジトリに追加された CNAME ファイルを上書きすることができます。 ローカルでサイトをビルドし、生成されたファイルを GitHub にプッシュする場合は、CNAME ファイルをローカルリポジトリに追加したコミットを先にプルして、そのファイルがビルドに含まれるようにする必要があります。

とりあえずCNAMEファイルというのが生成されて、GitHub Pages対象のブランチ(デフォルトはgh-pages)に存在する必要があるみたい。

![GitHubリポジトリ](/assets/blog/github-actions-create-cname/github-actions-create-cname_3.png)

ホントだ。ない...

![GitHubコミット履歴](/assets/blog/github-actions-create-cname/github-actions-create-cname_4.png)

コミット履歴にはある...

![GitHubコミット履歴詳細](/assets/blog/github-actions-create-cname/github-actions-create-cname_5.png)

純粋にCNAMEというファイル名にドメイン記載したものがgh-pagesブランチにあれば良いのか

> CNAMEファイルをローカルリポジトリに追加したコミットを先にプルして、そのファイルがビルドに含まれるようにする必要があります。

の部分がGitHub Actions内でやらなくてはならない感じもするけど、とりあえずファイル存在すればOKでしょうということで作成して普通にmerge

このサイトはNEXT.jsのブログテンプレートを利用しているのでpublic/配下に配置すれば静的ファイルとしてデプロイ後のルートディレクトリに配置されるはず

![GitHubリポジトリ設定後](/assets/blog/github-actions-create-cname/github-actions-create-cname_6.png)
OK！

![GitHub Pagesセッティング後](/assets/blog/github-actions-create-cname/github-actions-create-cname_7.png)
設定の方もOK

まとめ
GitHubのトラブルシューティングは優秀