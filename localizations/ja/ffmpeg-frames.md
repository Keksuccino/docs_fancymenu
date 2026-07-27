---
title: 動画からフレームを取得する
description: FFmpegを使って動画からPNGフレームを抽出します。
---

# FFmpegで動画フレームを抽出する

1. [FFmpeg](https://ffmpeg.org/download.html) をインストールし、`ffmpeg` コマンドが使えることを確認します。
2. 動画があるディレクトリでターミナルを開きます。
3. 出力先ディレクトリを作成します。

   ```bash
   mkdir output_frames
   ```

4. 必要なフレームに合ったコマンドを実行します。`input.mp4` は動画ファイル名に置き換えてください。

## すべてのフレームを抽出する

```bash
ffmpeg -i input.mp4 output_frames/frame_%04d.png
```

## 固定フレームレートで抽出する

この例では、1秒あたり10フレームを作成します。必要に応じて `10` を変更してください。

```bash
ffmpeg -i input.mp4 -vf "fps=10" output_frames/frame_%04d.png
```

## 抽出したフレームのサイズを変更する

この例では、すべてのフレームを `1280×720` に拡大縮小します。

```bash
ffmpeg -i input.mp4 -vf "scale=1280:720" output_frames/frame_%04d.png
```

`output_frames` 内の番号付き PNG ファイルは、[AFMA またはクラシック FMA アニメーション](./fma) の作成に使用できます。フレーム数を少なくし、サイズを小さくすると、ファイルサイズとメモリ使用量を削減できます。
