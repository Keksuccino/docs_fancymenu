---
title: 高度な位置調整とサイズ調整
description: 要素の高度な位置調整とサイズ調整の使い方。
---
# 高度な位置調整とサイズ調整

高度な位置調整とサイズ調整を使うと、要素の座標と寸法を直接制御できます。

> [!WARNING]
> GUIスケールへの適応には、まずレイアウト全体の **Auto-Scaling** を試してください。エディターの背景を右クリックしてGUIスケールを強制し、同じメニューで **Auto-Scaling** を有効にします。

# 高度な位置調整/サイズ調整モードの切り替え

要素で高度な位置調整またはサイズ調整を有効にするには、**右クリック**して **Advanced Positioning** または **Advanced Sizing** を選択します。
高度な位置またはサイズの値を設定すると、その要素は自動的に高度なモードに切り替わります。

通常の位置調整/サイズ調整に戻して **無効化** するには、**すべての位置/サイズの値を削除** します。

> [!WARNING]
> 要素が Advanced Sizing/Positioning モードの間は、その要素のサイズ変更や移動が無効化されるか、制限される場合があります。

# 位置/サイズの計算

高度な位置とサイズの値は [プレースホルダー](./placeholders) をサポートしています。

これにより、[**Calculator**](./placeholders#calculator-calc) プレースホルダーと、[**Screen Width**](./placeholders#screen-width-guiwidth)、[**GUI Scale**](./placeholders#gui-scale-guiscale)、[**Element Width**](./placeholders#element-width-elementwidth) などのGUIプレースホルダーを組み合わせられます。

> [!NOTE]
> テキストエディター右上の **Placeholders** ボタンをクリックすると、プレースホルダーを追加できます。このボタンが表示されない場合、編集したいコンテンツはプレースホルダーを**サポートしていません**。

[**Calculator プレースホルダー**](./placeholders#calculator-calc) を使って計算するには、サンプル式を自分の式に置き換えてください。入れ子のプレースホルダーで画面や要素の寸法を指定できます。

この例は `2` を返します。

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

整数ピクセル単位の位置とサイズを計算する場合は、`decimal` を `false` のままにしてください。

次のCalculatorは [**Screen Width** プレースホルダー](./placeholders#screen-width-guiwidth) を使い、`2` で割ります。

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`

> [!IMPORTANT]
> **Advanced Positioning** は要素のアンカーを無視し、左上の画面角 (`X0 Y0`) を原点として使用します。**Stay on Screen** は引き続き適用されます。
