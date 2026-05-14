---
title: APNG
description: FancyMenu に対応した APNG 画像の作り方。
---

# アニメーション PNG 画像

> 新しく大きい、または複雑なアニメーションには、[AFMA/FMA ファイル](/fma) をおすすめします。FancyMenu 3.9.0 では、利用可能な場合に Watermedia V3 + Watermedia Binaries V3 を使って APNG/GIF のデコードを高速化できますが、それでも FancyMenu のアニメーション形式としては AFMA が推奨です。
{.is-info}


APNG は PNG 画像のアニメーション版で、GIF のような機能を、完全なロスレス PNG 品質で実現できます！

FancyMenu には APNG の標準サポートがありますが、対応する APNG には少し制限があります。
必要なのは、**非圧縮** で **インターレースされていない** APNG です。

# APNG アニメーションの作成

良い APNG エディタ、特に圧縮やインターレースを無効にできるものを見つけるのは、かなり難しいです。

おすすめのエディタは [ScreenToGif](https://www.screentogif.com/) です。これは本来、画面の GIF や APNG を録画するためのツールですが、録画部分を使わずにそのままエディタへ読み込んで、通常の APNG を作るのにもとても便利です！

## エディタを開く

[ScreenToGif](https://www.screentogif.com/) を開いて最初に表示されるのがこの画面です。ここで **Editor** をクリックします。

![screentogif_2](https://github.com/Keksuccino/FancyMenu/assets/35544624/a8d34313-b841-4fb6-bf3a-ff02c39792cb)

## フレームを読み込む

次に、PNG フレームが必要です。エディタにドラッグ＆ドロップしてください。

![screentogif_dragndrop](https://github.com/Keksuccino/FancyMenu/assets/35544624/ba4ad4a5-484e-46f1-8efd-90ba764462d8)

## フレーム間隔

フレーム間の遅延を設定するには、編集したいフレームを選択し、**Edit** タブに切り替えて、**Delay (Duration)** セクションの **Override** をクリックします。

![screentogif_delay](https://github.com/Keksuccino/FancyMenu/assets/35544624/a5d93139-3192-4090-b243-e5c0fe299963)

## ループ設定

ループの動作は **Save As** メニューで設定できます。このメニューの開き方は次の手順を見てください。

## APNG を書き出す

準備ができたら、もう一度 **File** タブに切り替えて **Save As** をクリックします。

保存メニューでは、以下を必ず設定してください。
- ファイルタイプを **APNG** にする（最初の設定です。メニューの一番上までスクロールする必要があるかもしれません）
- **Detect Unchanged Pixels** を無効にする

> このメニューでは **ループ動作** も設定できます！ **Looped Apng** を無効にすると APNG は一切ループしなくなり、有効にすると特定回数のループか無限ループを選べます。
{.is-info}

![screentogif_save](https://github.com/Keksuccino/FancyMenu/assets/35544624/954353da-45ed-4df8-9f06-c78a0a469fc8)

## FancyMenu で APNG を使う

これで APNG ファイルを `/config/fancymenu/assets/` にコピーできます。すると、画像を受け付けるほとんどすべての場所で使えるようになります。

> APNG ファイル名の末尾が **`.apng`** であることが **非常に重要** です！
> 末尾が `.apng` でない場合、FancyMenu はその画像を APNG として認識できません。
{.is-warning}

![screentogif_use_apng](https://github.com/Keksuccino/FancyMenu/assets/35544624/2322da62-4013-451e-9a8b-3df0bf92df54)
