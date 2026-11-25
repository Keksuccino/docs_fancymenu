---
title: 画像
description: FancyMenu が対応している画像ファイルと、ほかの形式を変換する方法。
sourceBlobSha: 382f9ed2d99b0df29018dc4abf0b9b842ff01dec
---
# 画像

FancyMenu では、画像要素、メニューの背景、ボタンのテクスチャなど、さまざまな場所に画像を表示できます。対応しているファイル形式は次のとおりです。

- PNG (`.png`): 透明度に対応した静止画に最適です。
- JPEG (`.jpg` または `.jpeg`): 写真向けのファイルサイズが小さい形式ですが、透明度には対応していません。
- APNG (`.apng`) および GIF (`.gif`): アニメーション画像です。[アニメーション](/animations)をご覧ください。

FancyMenu はファイルの拡張子で画像の種類を判別するため、ファイル名の末尾には正しい拡張子を付けてください。

> [!TIP]
> FancyMenu は画像を加工せず、そのまま使用します。画像の鮮明さと読み込み速度を保つ方法については、[テクスチャの最適化](/optimizing-textures)をご覧ください。

# 画像の変換

WebP などのほかの形式は FancyMenu では使用できません。たとえば、次のサイトであらかじめ変換してください。

- [WebP から PNG への変換](https://convertio.co/webp-png/)
- [JPEG から PNG への変換](https://jpg2png.com/)
- [PNG から JPEG への変換](https://www.freeconvert.com/png-to-jpeg): 大きな画像のファイルサイズを小さくできますが、透明度は失われます。

アニメーションの作成や変換については、[アニメーションの作成](/animations#making-animations)をご覧ください。
