---
title: '引用符が表示されないのよぉ！'
excerpt: 'excerptexcerptexcerpt'
coverImage: '/assets/blog/dynamic-routing/cover.jpg'
date: '2022-07-03T05:35:07.322Z'
author:
  name: Pento
  picture: '/assets/blog/authors/jj.jpeg'
ogImage:
  url: '/assets/blog/dynamic-routing/cover.jpg'
---

このサイトはNext.jsの[ブログテンプレート](https://github.com/vercel/next.js/tree/canary/examples/blog-starter-typescript)を元に作成されています。

今回は引用符が表示されない問題を解決しました！
> ←こいつが引用符

Markdown記法では`>`を入力するとその後の文は引用として記載が可能です。このブログでも利用していたのですが、改めて確認すると引用表記になっておらず困っていました。このブログではMarkdownをHTMLに変換して運用しているのでおそらくCSS指定が無いと予想。ちなみに`>`は`<blockquote></blockquote>`に変換されます。

探してみると`/components`配下に`markdown-styles.module.css`なるものを発見。
中身はこんな感じ
```
.markdown {
  @apply text-lg leading-relaxed;
}

.markdown p,
.markdown ul,
.markdown ol,
.markdown blockquote {
  @apply my-6;
}

.markdown h2 {
  @apply text-3xl mt-12 mb-4 leading-snug;
}

.markdown h3 {
  @apply text-2xl mt-8 mb-4 leading-snug;
}
```

確かに`.markdown blockquote {...}`に装飾系のCSSがない！
そこで下記のように修正。
```

```
@applyの表記はtailwindcssのディレクティブです。
詳細は[こちら](https://tailwindcss.jp/docs/functions-and-directives)

引用符を多用していた下記ページも無事表示されるようになりました。

[【GitHub Pages】カスタムドメインがリセットされちゃうのよぉ！](https://pento.tech/posts/github-actions-create-cname/)

まとめ
無事引用符が表示されました。
インラインコード等も表示出来てないので引き続き整備していきたいと思います。
どっかに表示系のCSSを良い感じにしてくれてる神はいないだろうかそのまま使いたい。
Remarkで変換してるからその辺りを調べてみよう。