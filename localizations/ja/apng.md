---
title: APNG
description: FancyMenu に対応した APNG 画像の作り方。
---

# アニメーション PNG 画像

> [!NOTE]
> 大きなアニメーションや複雑なアニメーションには、[AFMA ファイル](./fma) の使用をおすすめします。Watermedia V3 と Watermedia Binaries V3 は利用可能な場合、APNG/GIF のデコードを高速化できますが、FancyMenu のアニメーション形式としては引き続き AFMA が推奨です。


APNG は PNG 画像のアニメーション版で、GIF と同じような機能を、完全な非可逆なしの PNG 品質で使うことができます！

FancyMenu には APNG の組み込みサポートがありますが、対応する APNG には少し条件があります。
必要なのは、**非圧縮** かつ **インターレースされていない** APNG です。

# APNG アニメーションの作成

圧縮やインターレースを無効にできるオプションまで備えた、使いやすい APNG エディタを見つけるのは意外と難しいものです。

エディタとしておすすめなのは [ScreenToGif](https://www.screentogif.com/) です。これは本来、画面の GIF や APNG を録画するためのツールですが、録画せずに直接エディタを開いて通常の APNG を作るのにもとても便利です。

## エディタを開く

[ScreenToGif](https://www.screentogif.com/) を開いて最初に表示されるのがこの画面です。ここで **Editor** をクリックします。

![screentogif_2](https://github.com/Keksuccino/FancyMenu/assets/35544624/a8d34313-b841-4fb6-bf3a-ff02c39792cb)

## フレームを読み込む

次に PNG フレームが必要です。エディタへドラッグ＆ドロップしてください。

![screentogif_dragndrop](https://github.com/Keksuccino/FancyMenu/assets/35544624/ba4ad4a5-484e-46f1-8efd-90ba764462d8)

## フレームの遅延時間

フレーム間の遅延を設定するには、編集したいフレームを選択し、**Edit** タブに切り替えて、**Delay (Duration)** セクションの **Override** をクリックします。

![screentogif_delay](https://github.com/Keksuccino/FancyMenu/assets/35544624/a5d93139-3192-4090-b243-e5c0fe299963)

## ループ設定

ループ動作は **Save As** メニューで設定できます。次の手順でこのメニューを開く方法を確認してください。

## APNG を書き出す

準備ができたら、もう一度 **File** タブに切り替えて **Save As** をクリックします。

保存メニューでは、次の点を確認してください。
- ファイル形式を **APNG** にする（最初の設定。必要ならメニューの一番上までスクロールしてください）
- **Detect Unchanged Pixels** を無効にする

> [!NOTE]
> このメニューでは **ループ動作** も設定できます。**Looped Apng** を無効にすると APNG はまったくループしなくなり、有効にすると特定回数のループまたは無限ループを選べます。

![screentogif_save](https://github.com/Keksuccino/FancyMenu/assets/35544624/954353da-45ed-4df8-9f06-c78a0a469fc8)

## FancyMenu で APNG を使う

APNG ファイルを `<game-directory>/config/fancymenu/assets/` にコピーします。これで、画像を受け付けるほとんどの場所で使えるようになります。

> [!WARNING]
> APNG ファイル名の末尾が **必ず** `.apng` で終わっていることがとても重要です！
> `.apng` で終わっていない場合、FancyMenu はその画像を APNG として識別できません。

![screentogif_use_apng](https://github.com/Keksuccino/FancyMenu/assets/35544624/2322da62-4013-451e-9a8b-3df0bf92df54)
