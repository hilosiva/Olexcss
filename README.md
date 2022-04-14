# Olexcss

俺のフレキシブル CSS グリッドシステム
(Ore no Flexible CSS Grid System)

## Overview

Olex は Ore no Flexible CSS Grid System の略で、Web ページのレイアウトを比較的簡単に組むことができる僕流、いや俺流の CSS ライブラリです。

## Demo

デモサイトはこちら。
https://shibajuku.net/demo/olex/

このページのレイアウトは Olex のみで出来上がっています。（装飾やアニメーションは別）

Olex を使えばこの様なレイアウトの Web ページでしたら容易に形にすることができます。

## Install

Olex を使いたい HTML ファイルに「olex.min.css」を読み込む

```html
<link rel="stylesheet" href="olex.min.css" />
```

## How to Use

Olex Container と Olex Item を用意する
![olex-container@2x](https://user-images.githubusercontent.com/46587015/107589678-df516d00-6c49-11eb-849e-7cf20e94c74f.png)

```html
<div class="olex">
  <div class="olex__item">A</div>
  <div class="olex__item">B</div>
  <div class="olex__item">C</div>
</div>
```

## Grid

12 カラムを基準としたグリッドシステム。

Olex Item に `data-cols `属性を使ってデバイスのプレフィクスとグリッド数を指定します。

ブレイクポイントはカスタマイズしやすいよう、sass ファイルに変数で設定できるようにしてます。

| プレフィックス | 適用画面サイズ |
| -------------- | -------------- |
| `min`          | 0px ~          |
| `xxs`          | 360px ~        |
| `xs`           | 414px ~        |
| `sm`           | 576px ~        |
| `md`           | 768px ~        |
| `lg`           | 992px ~        |
| `xl`           | 1200px ~       |
| `xxl`          | 1400px ~       |

メディアクエリを `min-width` しか使ってないので、`min`というプレフィックスはスマホだけじゃなく、横幅 `0px` 以上のブラウザ全てに適用されて、同様に`md` は、横幅 `768px` 以上のブラウザ全てに適用されるような仕様になってます。

で、例えばどの画面幅でもピッタリ半分半分の 2 段組みにしたかったら、12 分割のグリッドシステムなので、1 段につき 6 グリッド（列）ずつ使えばちょうど半分になるわけです。（12 分割 ÷ 2 段 = 6 グリッド）

つまり`data-cols`属性に `xxs:6`と指定すると、どのデバイスでも 2 つのボックスをちょうど半分ずつにわけることができます。

このように１行の合計が 12 グリッドになるように調整するように、グリッド数を指定すれば OK です。

なので、3 段組みにしたければ、`xxs:4` を 3 つ並べればいいですし、4 段組みにしたければ、`xxs:3` を 4 つ並べれば OK です。`xxs:8` と `xxs:4` などの組み合わせで 12 グリッドを使っても大丈夫です。

![olex-grid – 4@2x](https://user-images.githubusercontent.com/46587015/111059594-272e1300-84da-11eb-9823-a0c2ea3da07a.png)

あとは各デバイス（ブレークポイント）ごとで必要なグリッド数（列数）が異なる場合は、各ブレークポイントごとのプレフィックスとグリッド数（列数）を半角スペース区切りで指定すれば自由にレイアウト可能です。

```html
<div class="olex">
  <div class="olex__item" data-cols="xxs:12 md:4 lg:6">A</div>
  <div class="olex__item" data-cols="xxs:6 md:4 lg:3">B</div>
  <div class="olex__item" data-cols="xxs:6 md:4 lg:3">C</div>
</div>
```

## Gutter

Olex Item 間にスペースを設ける場合は、Olex Container に`data-gutter`属性を使ってスペースの量を表す値を指定する。

スペースのサイズはプロジェクトによって様々だと思いますので、カスタマイズしやすいよう、sass ファイルに変数で設定できるようにしてます。

ブレイクポイントごとに切り替えたい場合は、カスタマイズしてください。

| サイズ     | スペース |
| ---------- | -------- |
| `xxsmall`  | 16px     |
| `xsmall`   | 32px     |
| `small`    | 48px     |
| `medium`   | 64px     |
| `large`    | 88px     |
| `xlarge`   | 136px    |
| `xxlarge`  | 160px    |
| `xxxlarge` | 260px    |

```html
<div class="olex" data-gutter="xxs:normal">
  <div class="olex__item" data-cols="xxs12 md4 lg6">A</div>
  <div class="olex__item" data-cols="xxs6 md4 lg3">B</div>
  <div class="olex__item" data-cols="xxs6 md4 lg3">C</div>
</div>
```

## Alignment

Olex Item 全体の位置揃えをするには、Olex Container に `data-align`属性を使って揃える位置を表すキーワードを指定する。
なお、水平方向と垂直方向を同時に指定する場合は、半角スペースで区切る。

### Olex Container の位置揃え

![olex-align-1@2x](https://user-images.githubusercontent.com/46587015/107589505-871a6b00-6c49-11eb-85d5-5513d4f6d905.png)

![olex-align-2@2x](https://user-images.githubusercontent.com/46587015/107589461-69e59c80-6c49-11eb-8a8c-1fd9bf44abd2.png)

| 属性値    | 役割                   |
| --------- | ---------------------- |
| `start`   | 左揃え（逆順の時は右） |
| `center`  | 中央揃え               |
| `end`     | 右揃え                 |
| `justify` | 両端揃え               |
| `top`     | 上揃え                 |
| `middle`  | 中央（優柔不断）       |
| `bottom`  | 模擬揃え               |

### Olex Item の位置揃え

![olex-grid – 2@2x](https://user-images.githubusercontent.com/46587015/107589798-1b84cd80-6c4a-11eb-8cdf-fb22bf674f2b.png)

![olex-grid – 3@2x](https://user-images.githubusercontent.com/46587015/107589649-d06aba80-6c49-11eb-9f81-000d30e07f51.png)

| 属性値   | 役割                   |
| -------- | ---------------------- |
| `start`  | 左揃え（逆順の時は右） |
| `center` | 中央揃え               |
| `end`    | 右揃え                 |
| `top`    | 上揃え                 |
| `middle` | 中央（優柔不断）       |
| `bottom` | 模擬揃え               |

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

![olex-order@2x](https://user-images.githubusercontent.com/46587015/107589785-16c01980-6c4a-11eb-9e42-ad2edb9372e1.png)

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

## Over the Container

Olex Item を コンテナー幅から飛び越えさせるには Olex Item に `data-over`属性を使って飛び越える位置を表すキーワードを指定する。

| 属性値       | 役割         |
| ------------ | ------------ |
| `left`       | 左に超える   |
| `right`      | 右に超える   |
| `clearLeft`  | 左越えの解除 |
| `clearRight` | 右越えの解除 |

```html
<div class="olex" data-gutter="xxs:xxsmall">
  <div class="olex__item" data-over="xxs:left">A</div>
  <div class="olex__item">B</div>
  <div class="olex__item" data-over="xxs:right lg:clearRight">C</div>
</div>
```

## ブラウザサポート

- Google Chrome (latest)
- Opera (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

## ライセンス

MIT License.
