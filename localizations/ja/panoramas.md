---
title: パノラマ
description: Minecraftのタイトル画面のように、6枚の画像から回転する背景パノラマを作成できます。
sourceBlobSha: e1f9ab155301f1b88df58dd8414eeee5714cfba6
---

# パノラマ

パノラマとは、Minecraftのタイトル画面にあるもののように、周囲をゆっくりと回転する背景です。見る人を囲む立方体を形作る6枚の画像でできています。

レイアウトの[メニュー背景](/menu-backgrounds)として独自のパノラマを表示したり、すべてのメニューでMinecraftのパノラマの代わりに表示したりできます。

<img width="800" alt="夕暮れの森の空き地にある丸太小屋、庭、薪小屋、鶏小屋を映した、ゆっくり回転するパノラマを背景にしたタイトル画面" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/panoramas_title.gif?raw=true">

> [!TIP]
> このページのパノラマは、テスト用にも自分のModパック用にも無料で利用できます: [forest_homestead.zip](https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/forest_homestead.zip)（4 MB）。`config/fancymenu/panoramas/` に解凍し、FancyMenuを再読み込みしてください。

# パノラマの作成

1. ゲームのディレクトリにある `config/fancymenu/` 内の `panoramas` フォルダーを開きます。**メニューバー -> Tools -> Open FancyMenu Directory** を選ぶと `config/fancymenu/` が開きます。
2. その中に `forest_homestead` のようなパノラマ用フォルダーを作成します。名前は自由です。
3. フォルダー内に `properties.txt` と、[6枚の画像](#6枚の画像)を入れた `panorama` というフォルダーを配置します。`overlay.png` は任意です。
4. **メニューバー -> Customization -> Reload FancyMenu** または `Ctrl + Alt + R`（macOSでは `Cmd + Alt + R`）でFancyMenuを再読み込みするか、ゲームを再起動します。

```text
config/fancymenu/panoramas/
└── forest_homestead/
    ├── properties.txt
    ├── overlay.png
    └── panorama/
        ├── panorama_0.png
        ├── panorama_1.png
        ├── panorama_2.png
        ├── panorama_3.png
        ├── panorama_4.png
        └── panorama_5.png
```

# 6枚の画像

それぞれの画像が立方体の1面になります:

<img width="796" alt="展開した立方体の形に並べたforest_homesteadパノラマの6枚の画像。正面画像の上に上面画像、左・正面・右・背面の画像が横一列に並び、正面画像の下に底面画像がある" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/panoramas_cube.png?raw=true">

| 画像 | 面 |
|---|---|
| `panorama_0.png` | 正面 |
| `panorama_1.png` | 右 |
| `panorama_2.png` | 背面 |
| `panorama_3.png` | 左 |
| `panorama_4.png` | 上面 |
| `panorama_5.png` | 底面 |

- 4つの側面はこの順番で周囲を囲みます。各画像の右端は次の画像の左端につながり、`panorama_3.png` の右端は `panorama_0.png` の左端につながります。
- 上面画像の下端は正面画像の上端につながります。底面画像の上端は正面画像の下端につながります。
- 6枚すべてを同じサイズのPNGファイルにしてください。1024 × 1024のように正方形にします。
- FancyMenuは画像を滑らかに補間しないため、ピクセルアートもくっきり表示されます。

Minecraftのパノラマと同じ配置なので、Minecraft用に作られたパノラマも使用できます。

# properties.txt

```text
type = panorama

panorama-meta {
  name = forest_homestead
  speed = 2.0
  fov = 85.0
  angle = 25.0
  start_rotation = 0
}
```

| 設定 | 説明 |
|---|---|
| `name` | パノラマを選ぶときに使う名前です。パノラマごとに異なる名前を付けてください。 |
| `speed` | 回転速度です。`1.0` では約4分で1周し、`2.0` ではその2倍の速さになります。`0` にすると静止します。`10.0` を超えても速くなりません。 |
| `fov` | 画面に表示されるパノラマの範囲を、画面の上端から下端までの角度で指定します。値を小さくすると拡大表示になります。 |
| `angle` | 下を向く角度です。`0` では水平線をまっすぐ見ます。負の値にすると上を向きます。 |
| `start_rotation` | 回転を始める位置を、`0` から `360` までの角度で指定します。`0` では正面画像が中央に来た状態から始まります。 |

必須なのは `name` だけです。省略した設定には、`speed = 1.0`、`fov = 85.0`、`angle = 25.0`、`start_rotation = 0` が使われます。`type = panorama` と `panorama-meta {` の行はそのままにし、設定は1行に1つずつ記述します。小数には `1.5` のようにピリオドを使ってください。

# オーバーレイ

`properties.txt` と同じ階層に `overlay.png` を置くと、画面全体に引き伸ばされてパノラマの上に描画されます。パノラマと一緒には回転しないため、ビネットやフレーム、色合いの調整などに適しています。透明な部分からはパノラマが見えます。

# パノラマの使用

## メニュー背景として使う

<img width="800" alt="メニュー背景を開き、レイアウトエディターでCubic Panoramaを選択してShow Backgroundをオンにし、Choose Panoramaでforest_homesteadを選ぶと、タイトル画面のボタンの背後で回転する様子" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/panoramas_background.gif?raw=true">

1. [レイアウトエディター](/layout-editor)で背景を右クリックし、**Menu Backgrounds -> Cubic Panorama** を開きます。
2. **Show Background** をクリックして有効にします。
3. **Panorama Name** をクリックし、使用するパノラマを選んで **Done** をクリックします。右側のプレビューで回転を確認できます。

**Clear Panorama** をクリックすると、パノラマが解除されます。他の背景と組み合わせる方法については、[メニュー背景](/menu-backgrounds)を参照してください。

## すべてのメニューで使う

**メニューバー -> Customization -> Global Customizations -> Custom Menu Background Panorama -> Choose Panorama** を選ぶと、ワールドに参加する前のタイトル画面を含むすべてのメニューで、Minecraftのパノラマの代わりに選択したパノラマが表示されます。[グローバルカスタマイズ](/global-customizations#menu-backgrounds)を参照してください。

## 事前読み込み

サイズの大きなパノラマは、初回表示まで少し時間がかかることがあります。ゲームの起動中に読み込むには、**メニューバー -> Customization -> Pre-Load Resources** にある **Add Cubic Panorama** から追加します。[リソースの事前読み込み](/preload-layouts#pre-loading-slideshows--panoramas)を参照してください。

# 知っておくと便利なこと

- パノラマは右方向に回転します。正面画像は左へ移動し、右側の画像が見えてきます。
- 同じパノラマを表示するすべてのメニューで回転状態が共有されるため、メニューを切り替えても滑らかに回り続けます。どのメニューにも表示されていない間は一時停止します。
- FancyMenuを再読み込みすると、すべてのパノラマは `start_rotation` の位置から再開します。
- パノラマは、読み込まれている[プロファイル](/profiles)に属します。
- **Choose Panorama** に表示されないパノラマは、読み込みに失敗しています。ゲームのログ `logs/latest.log` に、`name` や画像の不足など、失敗の理由が記録されます。
- 紫と黒の市松模様が表示される場合、パノラマがまだ選択されていない、6枚の画像のサイズがそろっていない、またはレイアウトで指定されているパノラマ名が存在しなくなっています。
- 同じ `name` のパノラマが2つある場合、表示されるのはそのうち1つだけです。
