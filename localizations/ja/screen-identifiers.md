---
title: 画面識別子
description: 画面識別子についてと、画面の識別子を見つける方法。
---
# 画面識別子

FancyMenu は、レイアウト、Vanilla ウィジェット、[画面アクション](./action-scripts#open-screen-or-custom-gui-opengui)、および [Custom GUI のオーバーライド](./custom-guis#overriding-an-existing-screen) に画面識別子を使用します。識別子は大文字と小文字を区別するため、デバッグオーバーレイから正確にコピーしてください。

組み込み画面では通常、`title_screen` のような短い汎用識別子を使用します。他の MOD の画面では、その Java クラス名が使われることがあります。Custom GUI では、マネージャーで入力した識別子を使用します。これらは Minecraft のリソースロケーションではなく、FancyMenu の画面識別子です。

# 画面の識別子を見つける

**デバッグオーバーレイ** を使うと、現在アクティブなメニューの識別子を確認できます。
ここには現在の画面の識別子が表示され、左クリックするとクリップボードにコピーできます。

>[!TIP]
>**レイアウトエディタ** を開いていない状態で **CTRL + ALT + D** を押すと、**デバッグオーバーレイ** を有効にできます。

<br>

<img width="553" alt="Screenshot_3" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/1800351e-f042-4826-8eed-7725b78bc84d">

<br>

<img width="579" alt="Screenshot_4" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/9e0d1e61-7f2d-4817-9be1-b63ee61978dd">

# 画面を開く

[**Open Screen or Custom GUI** アクション](./action-scripts#open-screen-or-custom-gui-opengui) は、現在のゲーム状態で FancyMenu が構築できる画面のみを開けます。画面によっては、ロード済みのワールド、接続、プレイヤー、または元の親画面が必要です。

FancyMenu がその識別子を構築できない場合は、エラーが表示されます。画面を通常開くウィジェットには、[**Mimic Vanilla/Mod Button**](./action-scripts#mimic-vanillamod-button-mimicbutton) を使用してください。
