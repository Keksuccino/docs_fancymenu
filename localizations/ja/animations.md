---
title: アニメーション
description: FancyMenuでアニメーション画像を使う方法と、作成方法を紹介します。
sourceBlobSha: 76227b0d592e15bf10929c35d6a78e1eea6ee85a
---
# アニメーション

FancyMenuでは、画像を使えるほぼすべての場所でアニメーション画像を再生できます。[画像要素](/elements#image)、[画像メニュー背景](/menu-backgrounds#image)、ボタンやスライダーのテクスチャ、[ゲームイントロ](/game-intro)などで使用できます。

アニメーションには **APNG** または **GIF** ファイルを使用します。

- **APNG**（アニメーションPNG）は、より高画質です。通常のPNGと同じくすべての色を使え、境界が滑らかな透過にも対応しています。ロゴや背景など、透過が必要なものに最適です。
- **GIF** はより一般的なため、作成・編集ツールが豊富です。ただし、1フレームあたり256色までで、ピクセルは完全に透明か、不透明のどちらかです。

> [!NOTE]
> FancyMenu独自のアニメーション形式であるFMAとAFMAは非推奨です。既存のファイルは引き続き使えますが、新しいアニメーションにはAPNGまたはGIFを使用してください。[FMAとAFMA](#fma-and-afma)を参照してください。

# アニメーションの使用方法

1. ファイルを `<game-directory>/config/fancymenu/assets/` に配置すると、FancyMenuのファイル選択画面に表示されます。Web URLやリソースパック内のファイルも使用できます。詳しくは[リソース](/resources)を参照してください。
2. 画像要素の **画像ソース** などから、ほかの画像と同じように選択します。

> [!WARNING]
> APNGファイルの拡張子は `.apng` にする必要があります。多くのツールはAPNGを `.png` として保存するため、ファイル名を変更してください。変更しないと、FancyMenuでは静止画像として表示されます。Web URLも同様に、末尾を `.apng` にする必要があります。

## アニメーションの再生方法

- アニメーションは、ファイルで指定された回数だけ再生され、その後は最後のフレームで停止します。ループ回数はファイルの作成時に設定します。
- アニメーションは画面に表示されている間だけ再生されます。再び表示されると、停止したところから再生を続けます。
- **画面を開くときにアニメーションテクスチャを再スタート** を有効にすると、画面を開くたびに画像要素と画像メニュー背景のアニメーションが最初から再生されます。
- **ホバー時にアニメーションテクスチャを再スタート** を有効にすると、マウスがボタンやスライダーに乗るたびに、それらのテクスチャのアニメーションが最初から再生されます。
- [**アニメーションテクスチャの再生開始**](/listeners#animated-texture-started-playing)および[**アニメーションテクスチャの再生終了**](/listeners#animated-texture-finished-playing)リスナーを使うと、アニメーションの再生開始時や終了時にアクションを実行できます。

## パフォーマンス

FancyMenuは、APNGやGIFの再生中に必要な分だけデコードし、数フレーム先までしか読み込みません。そのため、長いアニメーションでもメモリ使用量を抑えられます。

ただし、フレームが大きい場合やフレームレートが高い場合は、パフォーマンスに影響します。フレームのサイズは、画面上で表示される大きさに合わせてください。詳しくは[テクスチャの最適化](/optimizing-textures)を参照してください。音声付きの長い動画には、代わりに[動画](/video)を使用してください。

# アニメーションの作成

次の無料ツールを使うと、複数のフレーム画像や動画からAPNGやGIFを作成できます。

- [ScreenToGif](https://www.screentogif.com/)（Windows）：**エディター** をクリックし、PNGフレームを読み込んで、フレーム間隔を設定します。アニメーションはAPNGまたはGIFとして保存できます。ループ回数は保存メニューで設定できます。
- [ezgif](https://ezgif.com/)（オンライン、ダウンロード不要）：画像から [GIF](https://ezgif.com/maker) または [APNG](https://ezgif.com/apng-maker) を作成したり、動画を [GIF](https://ezgif.com/video-to-gif) または [APNG](https://ezgif.com/video-to-apng) に変換したり、[GIFからAPNG](https://ezgif.com/gif-to-apng)、[APNGからGIF](https://ezgif.com/apng-to-gif) に変換したりできます。
- [FFmpeg](https://ffmpeg.org/download.html)（コマンドライン）：使い方は以下を参照してください。

## FFmpegを使う

`frame_0001.png`、`frame_0002.png` のような連番のPNGフレームから、無限にループするAPNGを作成します。`-framerate 20` は、1秒あたり20フレームで再生する設定です。

```bash
ffmpeg -framerate 20 -i frame_%04d.png -plays 0 animation.apng
```

動画からAPNGを作成します。`fps=20` は1秒あたり20フレームを維持し、`scale=960:-1` は幅を960ピクセルに設定します。

```bash
ffmpeg -i trailer.mp4 -vf "fps=20,scale=960:-1" -plays 0 trailer.apng
```

動画から無限にループするGIFを作成します。`palettegen` の部分で、動画に最適な256色を選びます。

```bash
ffmpeg -i trailer.mp4 -vf "fps=15,scale=640:-1:flags=lanczos,split[a][b];[a]palettegen[p];[b][p]paletteuse" -loop 0 trailer.gif
```

GIFをAPNGに変換します。

```bash
ffmpeg -i logo.gif -plays 0 logo.apng
```

# FMAとAFMA

FMAとAFMAは、FancyMenu独自のアニメーション形式です。どちらも非推奨ですが、引き続き再生できます。新しいアニメーションにはAPNGまたはGIFをおすすめします。

AFMAを作成する場合は、次の手順に従ってください。

1. フレームをPNGファイルとして1つのフォルダーに入れます。`frame_1.png`、`frame_2.png`、……、`frame_10.png` のように、ファイル名の順に再生されます。
2. **メニューバー -> ツール -> AFMA Creator** を開きます。
3. **メインフレームのディレクトリ** にフォルダーを指定します。**イントロフレームのディレクトリ** に指定したフレームは、メインフレームの再生前に1回だけ再生されます。
4. **メインフレームの表示時間（ms）** と **ループ回数** を設定します。ループ回数を `0` にすると、無限にループします。
5. **出力AFMAファイル** を指定し、**エクスポート** をクリックします。
