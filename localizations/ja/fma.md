---
title: アニメーション (FMA/AFMA)
description: FancyMenu のアニメーションファイルの作成方法と使用方法。
---
# アニメーション

AFMA と FMA ファイルは、FancyMenu 用に作成されたアニメーション付きテクスチャ形式です。

# AFMA ファイル

**AFMA**（Advanced FancyMenu Animation）は、従来の FMA ファイルの後継です。

AFMA は ZIP ではない形式を採用しており、従来の FMA よりもファイルサイズが小さく、メモリ使用量が少なく、パフォーマンスも優れています。

大きなアニメーションテクスチャや複雑なアニメーションテクスチャには、従来の FMA ではなく **AFMA** を使用してください。

内蔵の作成ツールで AFMA ファイルを作成します。

1. FancyMenu のメニューバーを開きます。
2. **Tools -> AFMA Creator** に移動します。
3. 作成ツールでフレームをインポート/変換します。

> [!IMPORTANT]
> AFMA ファイルは手動でパックできません。**Tools -> AFMA Creator** を使用してください。

従来の FMA ファイルも引き続きサポートされているため、既存のレイアウトをすぐに変換する必要はありません。

# 従来の FMA ファイル

## FMA の作成

従来の FMA ファイルは、`.fma` 拡張子を持つ ZIP アーカイブです。

### ファイル拡張子

以下のファイルを作成または名前変更する前に、ファイルマネージャーでファイル拡張子を有効にしてください。

Windows では、エクスプローラーを開いて **View -> File name extensions** を有効にします。

<br>
<img width="764" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/1f0a0864-1ad8-4f63-be3a-ab18385539e6"> 

### 準備

アーカイブの内容用に `fancymenu_animation` という名前のフォルダを作成します。

その中に、必須の `frames` ディレクトリと、任意の `intro_frames` ディレクトリを作成します。

同じフォルダ内に `metadata.json` を作成します。ファイル拡張子が `.txt` ではなく `.json` になっていることを確認してください。

これで、フォルダには `frames/`、`intro_frames/`、`metadata.json` が含まれている必要があります。

<br>
<img width="700" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/e29f6666-ee4a-4d79-b7e2-1b640f40ce78">

### メタデータ JSON

`metadata.json` をテキストエディタで開き、次のテンプレートを使用します。

```json
{
  "loop_count": 0,
  "frame_time": 41,
  "frame_time_intro": 41,
  "custom_frame_times": {
  },
  "custom_frame_times_intro": {
  }
}
```

必要に応じて値を編集してください。

#### `loop_count`

アニメーションを何回再生するかを制御します。`0` にすると無限ループします。正の値を指定すると、その回数だけ再生したあと、最後のフレームで停止します。

#### `frame_time`

各通常フレームを何ミリ秒表示するかを設定します。

#### `frame_time_intro`

任意の **intro** フレームのフレーム時間を設定します。

#### `custom_frame_times`

通常フレーム個別の表示時間を任意で上書きします。この例では、フレーム `0` と `1` を `5000` ミリ秒表示し、それ以外のフレームは `frame_time` を使用します。

```json
{
  "loop_count": 0,
  "frame_time": 41,
  "frame_time_intro": 41,
  "custom_frame_times": {
    "0": 5000,
    "1": 5000
  },
  "custom_frame_times_intro": {
  }
}
```

フレームのインデックスは 0 から始まります。最初のフレームは `0`、2 番目は `1` です。

各カスタムフレーム時間のエントリの末尾には、最後の 1 つを除いてカンマを付けてください。

#### `custom_frame_times_intro`

`custom_frame_times` と同じ形式ですが、任意の intro フレームに適用されます。

`metadata.json` を保存します。

### フレーム

> [!CAUTION]
> 従来の FMA アニメーションは 200 フレーム以下、1080p 以下にしてください。長時間のコンテンツや高フレームレートのコンテンツには [Video](./video) を使用してください。

通常フレームは `frames/` に配置します。PNG ファイルで、`0.png`、`1.png`、`2.png` のように 0 から連番で命名する必要があります。その他の形式や名前はサポートされていません。

動画からフレームを抽出する方法については、[FFmpeg を使ったフレームの抽出](./ffmpeg-frames) を参照してください。

<br>
<img width="574" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/eac54695-b57a-4919-8740-4e5c8aad649c">

### intro

任意の intro フレームは `intro_frames/` に配置します。通常フレームと同じ PNG の命名規則に従い、通常シーケンスの前に 1 回だけ再生され、ループしません。

### FMA ファイルのパッキング

フォルダの内容を含む ZIP を作成します。`metadata.json`、`frames/`、および任意の `intro_frames/` ディレクトリは、別のディレクトリの中ではなく ZIP のルートに置く必要があります。

Windows では、`fancymenu_animation` の内容を選択し、選択範囲を右クリックして **Send to -> Compressed (zipped) folder** を選びます。

<br>
<img width="752" alt="Screenshot_6" src="https://gist.github.com/assets/35544624/5b7e7670-5403-410e-943c-283bfe6d585c">

作成された ZIP ファイルを見つけます。

<br>
<img width="700" alt="Screenshot_7" src="https://gist.github.com/assets/35544624/987f7989-dff7-43b4-a54c-0898969827f5">

ルートの内容は次のようになっているはずです。

<img width="700" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/f1642a39-e14c-47a7-90f6-8a737e8ec75f">

ファイル名を `fancymenu_animation.fma` に変更し、`.zip` 拡張子を置き換えます。ベース名は変更できますが、`.fma` 拡張子は必須です。

名前を変更したアーカイブは、FMA ファイルとして使用できる状態になります。

# FancyMenu で AFMA & FMA ファイルを使用する

> [!IMPORTANT]
> AFMA/FMA ファイルはアニメーション付きテクスチャなので、[**Image** 入力](./elements#image) から追加してください。画像を受け付けるほとんどの場所で、AFMA および FMA ファイルも使用できます。

AFMA/FMA ファイルは、[Image 要素](./elements#image) や [Image メニュー背景](./menu-backgrounds) など、画像を受け付けるあらゆる場所で使用できます。

AFMA/FMA ファイルは `<game-directory>/config/fancymenu/assets/` に保存すると、FancyMenu のローカルリソース選択画面に表示されます。
