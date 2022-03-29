---
title: "Color palette tips"
date: 2022-03-30T00:50:00+09:00
image: "2022-3-30-0-38-28-2472.png"
categories:
    - "programming"
tags:
    - "p5js"
    - "javascript"
draft: false
---

p5js のプロジェクトでカラーパレットを生成するときに便利なツールの1つに [Coolors](https://coolors.co/palettes/trending) というサイトがあります。

そこで生成したカラーパレットを以下のように定義するのはよくあるパターンだと思います。

```js
// https://coolors.co/d9ed92-b5e48c-99d98c-76c893-52b69a-34a0a4-168aad-1a759f-1e6091-184e77
const palette = ["#D9ED92", "#B5E48C", "#99D98C", "#76C893", "#52B69A", "#34A0A4", "#168AAD", "#1A759F", "#1E6091", "#184E77"];
```

いちいちコピーして配列を作成するのは面倒だなと感じていたときに、[watabo_shi](https://openprocessing.org/user/240456?view=sketches) さんの[作品のソースコード](https://openprocessing.org/sketch/1528585)を見ていたときに良いアイデアを見つけたのでここで共有しておきます。 watabo_shi さんには本当に感謝です。


watabo_shi さんのソースコードを読んだあとに気づいたのですが、CoolorsのURLには以下の規則があります。

例: `https://coolors.co/d9ed92-b5e48c-99d98c-76c893-52b69a-34a0a4-168aad-1a759f-1e6091-184e77`
- `https://coolors.co/` 以降のパスがハイフン区切りの`#`なし16進数カラーコードで表現されている

上記の規則性より以下のようなプログラムで上のソースコードで示したようなカラーパレットを生成することができます。

```js
// refs: https://openprocessing.org/sketch/1528585
const url = "https://coolors.co/d9ed92-b5e48c-99d98c-76c893-52b69a-34a0a4-168aad-1a759f-1e6091-184e77"
const palette = url.split('/')[3].split('-').map(c => '#' + c);
```

あとはこのパレットを使って以下のようにいい感じにやります。

{{< openprocessing 1530028 >}}