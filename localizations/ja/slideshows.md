---
title: スライドショー
description: スライドショーの作成方法と使い方。
---

# スライドショー

FancyMenuでは、スライドショーを追加して、メニュー内やメニューの背景として表示できます。

> **重要**: Windowsを使っている場合は、後でファイル名の重要な部分が見えなくならないように、[ファイル拡張子](https://vtcri.kayako.com/article/296-view-file-extensions-windows-10)を必ず有効にしてください！
{.is-warning}

# スライドショーの作成

各スライドショーは、`/config/fancymenu/slideshows/` にある slideshows ディレクトリの**中**に、それぞれ専用のフォルダとして配置する必要があります。

![1](https://user-images.githubusercontent.com/35544624/105209961-b823e600-5b4a-11eb-8ed2-1016d3b05815.png)

スライドショーをシステムに認識させるには、スライドショーのフォルダ内に properties ファイルが必要です。たとえばスライドショーのフォルダ名を `myslideshow` にした場合、properties ファイルは `/config/fancymenu/slideshows/myslideshow/properties.txt` に置く必要があります。

**このファイル名は必ず `properties.txt` である必要があります！**
今は、**空**の properties ファイルだけを作成して、次の手順に進みましょう。

![2](https://user-images.githubusercontent.com/35544624/105210016-cbcf4c80-5b4a-11eb-84ad-9aa735340287.png)

## 画像の追加

スライドショーには画像が必要なので、追加していきましょう！

> スライドショーの画像は**PNG**ファイルである必要があります！ JPEG、GIF、APNG、FMAs は使えません！
{.is-danger}

スライドショー内のすべての画像は、スライドショーフォルダ（上の例では `myslideshow`）の**中**にある追加フォルダへ入れます。
このフォルダ名は `images` にする必要があります。

![3](https://user-images.githubusercontent.com/35544624/105210833-d9d19d00-5b4b-11eb-8ae7-528ad156e27a.png)

あとは、スライドショーの画像をすべて `images` フォルダに配置します。
画像はアルファベット順（数字も考慮）で並ぶので、`image_1.png`、`image_2.png` のような名前にするとよいでしょう。
この例では、`image_1.png` が最初に表示され、次に `image_2.png` が表示されます。

<br>
<img width="548" alt="Screenshot_2" src="https://github.com/user-attachments/assets/f58ecbfa-affa-4071-8a84-18ed27a6cfee">

## properties ファイルへの内容の追加

最初に、スライドショーフォルダ内に空の `properties.txt` ファイルを作成しました。
このファイルに、重要な内容を入力する必要があります。

各スライドショーの properties ファイルは、次のようになっている必要があります。

```
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
変更できるのは `slideshow-meta` セクション内の変数だけです！

### name

これはスライドショーの名前、より正確には識別子です。
スライドショー名は**一意**である必要があるため、同じ名前のスライドショーを2つ作ることはできません！

### width | height

スライドショーの基準となる `width` と `height` です。
FancyMenu がアスペクト比を計算するために使用します。

### x | y

スライドショーの `x` と `y` の位置です。
主にデバッグ用なので、両方とも `0` に設定しておけば問題ありません。

### duration

次の画像に切り替わるまで、各画像を表示する時間を**秒**で指定します。
小数も指定できます！

### fadespeed

次の画像へ切り替える際のフェードアニメーションの速度です。
この値は速度の倍率です。たとえば `1.0` は標準速度、`2.0` は2倍速、`0.5` は標準の半分の速度になります。
負の値はサポートされていません。

### randomize

スライドショーの画像をランダム順（`true`）で再生するかどうか、または通常順（`false`）にするかどうかです。

# スライドショーの使用

必要な手順はすべて完了したので、スライドショーの準備はできているはずです。試してみましょう！

新しい（または編集した）スライドショーを FancyMenu に読み込むには、**Customization -> Reload FancyMenu** から mod を再読み込みしてください。

これで、スライドショーを **Slideshow** 要素として使ったり、メニュー背景として使ったりできます（レイアウトエディタの背景を右クリック -> **Menu Background**）。
