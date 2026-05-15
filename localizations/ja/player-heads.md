---
title: プレイヤーヘッド
description: メニュー内でプレイヤーの頭を2Dまたは3D画像として表示する方法。
---

# メニュー内のプレイヤーヘッド

Image 要素を使ってプレイヤーの頭を 2D または 3D 画像として表示するには、"Minotar" というサードパーティの Web API を使用できます。

## 2D画像

### 1. Image 要素を追加する

FancyMenu エディターで、背景を右クリックし、"New Element" を選択してから "Image"（または "Picture"）を選びます。

### 2. Web ソースを設定する

Image 要素を右クリックしてプロパティを開きます。ソースタイプとして "Web" を選択します。

### 3. 正しいプレースホルダーを使ってURLを作成する

"Source" フィールドには、次の URL を入力します:
`https://minotar.net/avatar/{"placeholder":"playername"}.png`

FancyMenu は `{"placeholder":"playername"}` を使用して、現在のプレイヤー名を URL に動的に挿入します。これにより、Image 要素は Minotar からその頭部画像を取得して表示できます。

## 3D画像

こちらは 2D 版とかなり似ていますが、別の URL を使う必要があります:

`https://minotar.net/cube/{"placeholder":"playername"}/200.png`

この場合の `200` はピクセルサイズです。より小さいサイズにしたい場合は、たとえば `100` に置き換えてください。逆に大きくしたい場合は、`300` などに変更できます。
