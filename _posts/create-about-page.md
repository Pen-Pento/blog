---
title: 'Aboutページを作りたいよー！'
excerpt: 'excerptexcerptexcerpt'
coverImage: '/assets/blog/dynamic-routing/cover.jpg'
date: '2022-03-21T05:35:07.322Z'
author:
  name: Pento
  picture: '/assets/blog/authors/jj.jpeg'
ogImage:
  url: '/assets/blog/dynamic-routing/cover.jpg'
---

今回は大抵のサイトにあるAboutページを作成したいと思います。
このサイトはNext.jsの[ブログテンプレート](https://github.com/vercel/next.js/tree/canary/examples/blog-starter-typescript)を元に作成されていますので早速Next.jsの[ドキュメント](https://nextjs.org/docs/basic-features/pages)を確認。

![Pages](/assets/blog/create-about-page/create-about-page_1.png)

ブログページは_postsにMarkdownファイルを作成すればいいようなのですが、固定ページはpages配下にabout.tsxを作成すれば/aboutでページが作成されるようですね！よく考えればindex.tsxもpages配下にありました。
![pages配下](/assets/blog/create-about-page/create-about-page_2.png)

出来た！
![Aboutページ画像](/assets/blog/create-about-page/create-about-page_3.png)

まとめ
Next.jsのドキュメントはかなり綺麗にまとまっているのでこれからもブログをガンガン進化させていければと思います。個人的に見返す時も記事にタグつけて一覧性、検索性高めておくといいなぁ