---
title: グローバルカスタマイズ
description: すべての画面に影響する FancyMenu のグローバルな調整を適用します。
---

# グローバルカスタマイズ

グローバルカスタマイズは、各画面のレイアウトを編集せずに共有の UI や起動設定を適用します。通常の画面カスタマイズが無効でも機能します。

よくある例:

- すべての画面で同じ共有ボタンとスライダーのスタイルを使う。
- メニューの背景、パノラマ、メニュー音楽をグローバルに置き換える。
- グローバルな起動時/ウィンドウ挙動（GUI スケール、全画面、ウィンドウタイトル/アイコン）を適用する。
- リソースパックなしでバニラのボタンテクスチャをグローバルに置き換える。
- リソースパックなしでバニラのメニュー音楽をグローバルに置き換える。

# 見つけ方

レイアウトエディタを**開いていない**状態で FancyMenu の **メニューバー** を開き、**Customization -> Global Customizations** を選択します。

# カスタマイズできる内容

## グローバルな動作と起動設定

- [**Game Intro**](./game-intro)（タイトル画面の前に再生されるイントロ動画またはアニメーション）
- **Singleplayer Screen World Icons**
- **Multiplayer Screen Server Icons**
- [**Seamless World Loading**](./seamless-world-loading)（最近のワールドのスクリーンショットをロード画面の背景として使用します）
- [**Custom Window Icon**](./window-customization#custom-icon)
- [**Custom Window Title**](./window-customization#custom-title)
- **Default GUI Scale**
- **Force Fullscreen on Launch**

## ボタンの見た目

- **Custom Button Textures**（通常/ホバー/無効の状態、透明モード、[9-slice](./nine-slicing-and-tiling) + 境界サイズ）
- **Button Labels**（ホバー時の下線、基本/ホバー色、スケール、影）

## スライダーの見た目

- **Custom Slider Textures**
- **Slider Background Texture**（テクスチャ、透明モード、[9-slice](./nine-slicing-and-tiling) + 境界サイズ）
- **Slider Handle Textures**（通常/ホバー/無効の状態、[9-slice](./nine-slicing-and-tiling) + 境界サイズ）
- **Slider Labels**（ホバー時の下線、基本/ホバー色、スケール、影）

## メニューの見た目と音声

- [**Custom Menu Background Texture**](./menu-backgrounds)
- [**Custom Menu Background Panorama**](./panoramas)
- **Play Vanilla Menu Music**（バニラのメニュー音楽の再生を有効/無効にします）
- [**Custom Menu Music Tracks**](./background-music)
- **Custom Button/Slider Click Sound**

# Custom Menu Music Tracks

**Custom Menu Music Tracks** を使って、メニュー用のランダム再生トラック一覧を作成します。

> [!IMPORTANT]
> グローバルなカスタムメニュートラックは、ワールドが読み込まれていないとき、たとえばタイトル画面でのみ再生されます。ワールド内のメニュー音声には [**Audio** 要素](./elements#audio) を使用してください。

設定されたトラックは Music サウンドチャンネルを使用し、対応するワールド外メニューではバニラのメニュー音楽を置き換えます。

- 最初のトラックは約 5 秒後に再生されます。
- 以降のトラックは約 1〜30 秒のランダムな遅延の後に再生されます。
- トラックはランダムに選択されます。
- 複数のトラックがある場合、直前のトラックが連続して再選択されることはありません。

トラック一覧は **Custom Menu Music Tracks** から管理します:

- **Custom Menu Music Tracks** を開いて **Manage Menu Music Tracks** を開きます。
- **Add Track** で音声ソースを追加します。
- **Remove Track** で 1 件削除します。
- **Clear Tracks** で全件削除します。
