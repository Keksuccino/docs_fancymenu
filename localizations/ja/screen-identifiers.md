---
title: 画面識別子
description: 画面識別子について、また画面の識別子を確認する方法を説明します。
sourceBlobSha: 64414e10bf5f532e075373a6a753e2f667448ceb
---
# 画面識別子

FancyMenuでは、レイアウト、バニラウィジェット、[画面アクション](/action-scripts#open-screen-or-custom-gui)、[カスタムGUIの上書き](/custom-guis#overriding-an-existing-screen)に画面識別子を使用します。識別子は大文字と小文字が区別されるため、デバッグオーバーレイから正確にコピーしてください。

組み込み画面では通常、`title_screen`のような短い共通識別子が使われます。ほかのModの画面では、Javaクラス名が使われる場合があります。カスタムGUIでは、管理画面で入力した識別子が使われます。これらはFancyMenuの画面識別子であり、Minecraftのリソースロケーションではありません。

# 画面の識別子を確認する

現在表示されているメニューの識別子は、**デバッグオーバーレイ**で確認できます。
現在の画面の識別子が表示され、そこを左クリックするとクリップボードにコピーできます。

>[!TIP]
>レイアウトエディターを開いていない状態で**CTRL + ALT + D**を押すと、**デバッグオーバーレイ**を有効にできます。

<br>

<img width="553" alt="Screenshot_3" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/1800351e-f042-4826-8eed-7725b78bc84d">

<br>

<img width="579" alt="Screenshot_4" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/9e0d1e61-7f2d-4817-9be1-b63ee61978dd">

# 画面を開く

[**画面またはカスタムGUIを開く**アクション](/action-scripts#open-screen-or-custom-gui)で開けるのは、現在のゲーム状態でFancyMenuが構築できる画面のみです。画面によっては、ワールド、接続、プレイヤー、または元の親画面が必要です。

FancyMenuが識別子から画面を構築できない場合は、エラーが表示されます。通常その画面を開くウィジェットに[**バニラ/Modボタンを模倣**](/action-scripts#mimic-vanillamod-button)を使用してください。
