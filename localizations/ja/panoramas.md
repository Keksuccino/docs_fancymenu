---
title: パノラマ
description: 6枚の画像を使った立方体パノラマを作成・使用します。
---

# 立方体パノラマ

各パノラマは、以下のディレクトリ内に個別に配置されます。

```text
<game-directory>/config/fancymenu/panoramas/
```

`<game-directory>` は現在有効なランチャーインスタンスを指し、通常の `.minecraft` ディレクトリとは異なる場合があります。

# ディレクトリ構成

```text
<game-directory>/config/fancymenu/panoramas/
└── mypanorama/
    ├── properties.txt
    ├── overlay.png          # optional
    └── panorama/
        ├── panorama_0.png
        ├── panorama_1.png
        ├── panorama_2.png
        ├── panorama_3.png
        ├── panorama_4.png
        └── panorama_5.png
```

6枚の各面画像は、上記とまったく同じ名前の PNG ファイルである必要があり、6枚すべてのサイズも同一でなければなりません。ファイル名の大文字・小文字は、OS によって重要になる場合があります。

`properties.txt` の隣に、ビネットやフルパノラマ用のオーバーレイとして任意の `overlay.png` を追加できます。

# `properties.txt`

```text
type = panorama

panorama-meta {
  name = name_of_your_panorama
  speed = 1.0
  fov = 85.0
  angle = 25.0
  start_rotation = 0
}
```

| プロパティ | 意味 |
|---|---|
| `name` | 必須。大文字・小文字を区別する実行時識別子。重複しないようにしてください |
| `speed` | 回転速度の倍率。`1.0` がデフォルトです |
| `fov` | 視野角（度） |
| `angle` | 垂直視点角（度） |
| `start_rotation` | 初期の水平回転角（度） |

必須なのは `name` のみです。省略した任意項目には、例に示した既定値が使用されます。`type = panorama` と `panorama-meta` は変更せず、そのまま使用してください。各行は `key = value` 形式で1つずつ記述し、小数点にはピリオドを使ってください。

同名のパノラマは拒否されず、ディレクトリのスキャン順によってどのパノラマが有効に残るかが決まります。パノラマディレクトリ内では、名前を一意にしてください。パノラマとスライドショーの名前は別々のリストで管理されます。

# パノラマの使用方法

**カスタマイズ -> FancyMenu を再読み込み** から FancyMenu を再読み込みするか、クライアントを再起動してください。その後、レイアウトエディターの背景を右クリックし、[**メニュー背景**](./menu-backgrounds) -> **立方体パノラマ** を選択します。
