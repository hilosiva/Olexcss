# Olexcss

俺のフレキシブル CSS グリッドシステム
(Ore no Flexible CSS Grid System)

## Overview

Olex は Ore no Flexible CSS Grid System の略で、Web ページのレイアウトを比較的簡単に組むことができる僕流、いや俺流の CSS ライブラリです。

## Demo

[デモサイト]](
https://shibajuku.net/demo/olex/) はこちら。

このページのレイアウトは Olex のみで出来上がっています。（装飾やアニメーションは別）

Olex を使えばこの様なレイアウトの Web ページでしたら容易に形にすることができます。

## Install

Olex を使いたい HTML ファイルに「olex.min.css」を読み込む

```html
<link rel="stylesheet" href="olex.min.css" />
```

## How to Use

Olex Container と Olex Item を用意する

```html
<div class="olex">
  <div class="olex__item">A</div>
  <div class="olex__item">B</div>
  <div class="olex__item">C</div>
</div>
```

## Grid

12 カラムを基準としたグリッドシステム。

Olex Item に `data-grid `属性を使ってデバイスのプレフィクスとグリッド数を指定します。

ブレイクポイントはカスタマイズしやすいよう、sass ファイルに変数で設定できるようにしてます。

| プレフィックス | 適用画面サイズ |
| -------------- | -------------- |
| `sp`           | 1px ~          |
| `tab`          | 768px ~        |
| `lap`          | 1024px ~       |
| `desk`         | 1200px ~       |

メディアクエリを `min-width` しか使ってないので、`sp`というプレフィックスはスマホだけじゃなくスマホ以上全てに適用されて、同様に`tab` は、タブレット以上全てに適用されるような仕様になってます。

で、例えばどの画面幅でもピッタリ半分半分の 2 段組みにしたかったら、12 分割のグリッドシステムなので、1 段につき 6 グリッド（列）ずつ使えばちょうど半分になるわけです。（12 分割 ÷ 2 段 = 6 グリッド）

つまり`data-grid`属性に `sp6`と指定すると、どのデバイスでも 2 つのボックスをちょうど半分ずつにわけることができます。

このように１行の合計が 12 グリッドになるように調整するように、グリッド数を指定すれば OK です。

なので、3 段組みにしたければ、`sp4` を 3 つ並べればいいですし、4 段組みにしたければ、`sp3` を 4 つ並べれば OK です。`sp8` と `sp4` などの組み合わせで 12 グリッドを使っても大丈夫です。

```html
<div class="olex">
  <div class="olex__item" data-grid="sp12 tab4 lap6">A</div>
  <div class="olex__item" data-grid="sp6 tab4 lap3">B</div>
  <div class="olex__item" data-grid="sp6 tab4 lap3">C</div>
</div>
```

## Gutter

Olex Item 間にスペースを設ける場合は、Olex Container に`data-gutter`属性を使ってスペースの量を表す値を指定する。

スペースのサイズはプロジェクトによって様々だと思いますので、カスタマイズしやすいよう、sass ファイルに変数で設定できるようにしてます。

ブレイクポイントごとに切り替えたい場合は、カスタマイズしてください。

| サイズ   | スペースサイズ |
| -------- | -------------- |
| `small`  | 1vw            |
| `normal` | 2vw            |
| `large`  | 3vw            |

```html
<div class="olex" data-gutter="normal">
  <div class="olex__item" data-grid="sp12 tab4 lap6">A</div>
  <div class="olex__item" data-grid="sp6 tab4 lap3">B</div>
  <div class="olex__item" data-grid="sp6 tab4 lap3">C</div>
</div>
```

## Alignment

Olex Item 全体の位置揃えをするには、Olex Container に `data-align`属性を使って揃える位置を表すキーワードを指定する。
なお、水平方向と垂直方向を同時に指定する場合は、半角スペースで区切る。

| 属性値    | 役割                   |
| --------- | ---------------------- |
| `start`   | 左揃え（逆順の時は右） |
| `center`  | 中央揃え               |
| `end`     | 右揃え                 |
| `justify` | 両端揃え               |
| `top`     | 上揃え                 |
| `middle`  | 中央（優柔不断）       |
| `bottom`  | 模擬揃え               |

```html
<div class="olex" data-align="center">
  <div class="olex__item">A</div>
  <div class="olex__item">B</div>
  <div class="olex__item">C</div>
</div>
```

Olex Item を個別に位置揃えをするには、Olex Item に `data-align`属性を使って揃える位置を表すキーワードを指定する。
なお、水平方向と垂直方向を同時に指定する場合は、半角スペースで区切る

```html
<div class="olex">
  <div class="olex__item">A</div>
  <div class="olex__item">B</div>
  <div class="olex__item" data-align="end middle">C</div>
</div>
```

## Direction

Olex Item の並び順を指定するには Olex Container に `data-dir`属性を使って、方向を表すキーワードを指定する。

| 属性値    | 役割 |
| --------- | ---- |
| `normal`  | 通常 |
| `reverse` | 逆順 |

```html
<div class="olex" data-dir="reverse">
  <div class="olex__item">A</div>
  <div class="olex__item">B</div>
  <div class="olex__item">C</div>
</div>
```

## ブラウザサポート

- Google Chrome (latest)
- Opera (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)
- Internet Explorer 11+

## ライセンス

MIT License.
