---
title: スライドショー
description: 画像スライドショーを作成して使用します。
---
# スライドショー

各スライドショーには、以下の場所に専用のディレクトリがあります。

```text
<game-directory>/config/fancymenu/slideshows/
```

`<game-directory>` は現在有効なランチャーインスタンスを指し、通常の `.minecraft` ディレクトリとは異なる場合があります。

# ディレクトリ構成

```text
<game-directory>/config/fancymenu/slideshows/
└── myslideshow/
    ├── properties.txt
    ├── overlay.png          # 任意
    └── images/
        ├── image_01.png
        └── image_02.jpg
```

画像は `.png` または `.jpg` を使用してください。`.jpeg` を含むその他の拡張子は無視されます。

`randomize = false` の場合、画像はファイル名のアルファベット順で再生されます（大文字小文字は区別されません）。`image_01.png`、`image_02.png`、`image_10.png` のようにゼロ埋めした名前を使ってください。

# `properties.txt`

```text
type = slideshow

slideshow-meta {
  name = cool_slideshow
  width = 1920
  height = 1080
  x = 0
  y = 0
  duration = 5.0
  fadespeed = 12.0
  randomize = false
}
```

| プロパティ | 意味 |
|---|---|
| `name` | 必須。実行時の識別子で、大文字小文字を区別します。必ず一意にしてください |
| `width`, `height` | GUI スケーリング後のピクセル単位での基準サイズと、元のアスペクト比 |
| `x`, `y` | 基準となる左上位置。通常の要素や背景はそれぞれ独自の位置を使用するため、`0` のままにしてください |
| `duration` | 画面切り替え開始間隔の最小秒数。フェード時間を含み、`0` より大きくする必要があります |
| `fadespeed` | フェード速度の倍率。`1.0` が既定で、値が大きいほど速くフェードし、`0` より大きい必要があります |
| `randomize` | ランダムに選択する場合は `true`、ファイル名順にする場合は `false` |

必須なのは `name` のみです。既定値は `width = 50`、`height = 50`、`x = 0`、`y = 0`、`duration = 10.0`、`fadespeed = 1.0`、`randomize = false` です。`type = slideshow` と `slideshow-meta` は変更しないでください。`key = value` は 1 行に 1 つずつ記述し、小数にはピリオドを使用してください。

レイアウトではディレクトリ名ではなく、`name` の値が参照されます。重複した名前は拒否されず、ディレクトリのスキャン順によってどのスライドショーが利用可能なまま残るかが決まります。スライドショーのディレクトリ内では、名前を一意にしてください。

ランダムモードでは、切り替えのたびに独立して選択され、複数の画像がある場合は直前と同じ画像が連続して表示されないようにします。タイミングは実時間で処理され、`duration` より長くかかるフェードは次の切り替えを遅らせます。また、非表示だったスライドショーを再び表示すると、すぐに次の切り替えへ進む場合があります。

# スライドショーの使用方法

**カスタマイズ -> FancyMenu を再読み込み** から FancyMenu を再読み込みするか、クライアントを再起動してください。[**Slideshow** 要素](./elements#slideshow)を使用するか、レイアウトエディタの背景を右クリックして [**メニュー背景**](./menu-backgrounds) -> **Slideshow** を選択します。
