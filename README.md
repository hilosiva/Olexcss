# Olexcss

俺のフレキシブル CSS グリッドシステム
(Ore no Flexible CSS Grid System)

## Overview

Flexbox を活用したグリッドシステム

## Install

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

```html
<div class="olex" data-gutter="normal">
  <div class="olex__item" data-grid="sp12 tab4 lap6">A</div>
  <div class="olex__item" data-grid="sp6 tab4 lap3">B</div>
  <div class="olex__item" data-grid="sp6 tab4 lap3">C</div>
</div>
```

## Alignment

Olex Item 全体の位置揃えをするには、Olex Container に `data-align`属性を使って揃える位置を表すキーワードを指定する。
なお、水平方向と垂直方向を同時に指定する場合は、半角スペースで区切る

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
- Safari 3.1+
- Internet Explorer 11+

## ライセンス

MIT License.
