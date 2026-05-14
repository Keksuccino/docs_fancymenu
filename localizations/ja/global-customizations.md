---
title: グローバルカスタマイズ
description: すべての画面に影響する FancyMenu のグローバルな調整を適用します。
---

# グローバルカスタマイズ

グローバルカスタマイズは、ゲームの UI 全体に適用される FancyMenu の調整です。
各画面のレイアウトを個別に編集するのではなく、どこでも一貫した見た目や動作にしたいときに使います。

> [!INFO]
> ほとんどの FancyMenu のカスタマイズ機能とは異なり、グローバルカスタマイズは通常の画面カスタマイズが無効でも動作します。
> 画面ごとにカスタマイズを有効化する必要が**ない**ため、1つの変更がすべての画面にすぐ反映されます。

よくある例:

- すべての画面で共通のボタンやスライダーのスタイルを使う。
- メニュー背景、パノラマ、メニュー音楽をグローバルに置き換える。
- 起動時/ウィンドウの動作をグローバルに適用する（GUI スケール、全画面表示、ウィンドウタイトル/アイコン）。
- バニラのボタンテクスチャをリソースパックなしでグローバルに置き換える。
- バニラのメニュー音楽をリソースパックなしでグローバルに置き換える。

# 見つけ方

レイアウトエディタに**入っていない**状態で FancyMenu の**メニューバー**を開き、**Customization -> Global Customizations** を選択します。

# クイックスタート

1. **Customization -> Global Customizations** を開きます。
2. まず 1 つのカテゴリを選びます（たとえば **Custom Button Textures**）。
3. そのカテゴリのオプション（リソースピッカー、トグル、数値入力など）を設定します。
4. 複数の画面で結果をテストします。
5. 関連する設定（たとえば透明度、ラベルスタイル、9 スライスの境界）を微調整します。

# カスタマイズできる内容

## グローバルな動作と起動時設定

- **Game Intro**（タイトル画面が表示される前に再生されるイントロ動画またはアニメーション）
- **Singleplayer Screen World Icons**
- **Multiplayer Screen Server Icons**
- **Seamless World Loading**（ワールド読み込み画面の背景としてワールドのスクリーンショットを使用します）
- **Custom Window Icon**
- **Custom Window Title**
- **Default GUI Scale**
- **Force Fullscreen on Launch**

## ボタンの見た目

- **Custom Button Textures**（通常/ホバー/非アクティブ状態、透明モード、9 スライス + 境界サイズ）
- **Button Labels**（ホバー時の下線、基本/ホバー色、スケール、影）

## スライダーの見た目

- **Custom Slider Textures**
- **Slider Background Texture**（テクスチャ、透明モード、9 スライス + 境界サイズ）
- **Slider Handle Textures**（通常/ホバー/非アクティブ状態、9 スライス + 境界サイズ）
- **Slider Labels**（ホバー時の下線、基本/ホバー色、スケール、影）

## メニューの見た目と音

- **Custom Menu Background Texture**
- **Custom Menu Background Panorama**
- **Play Vanilla Menu Music**（バニラのメニュー音楽を再生するかどうかを切り替えます）
- **Custom Menu Music Tracks**
- **Custom Button/Slider Click Sound**

# Custom Menu Music Tracks

**Custom Menu Music Tracks** を使って、メニュー用のランダム再生トラック一覧を作成します。

設定したカスタムトラックは、メニュー内のバニラのメニュー音楽を置き換えます。

- **Custom Menu Music Tracks** を開くと、**Manage Menu Music Tracks** が開きます。
- **Add Track** で音源を追加します。
- **Remove Track** で 1 件削除します。
- **Clear Tracks** で全件削除します。
