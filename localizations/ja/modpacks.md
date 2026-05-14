---
title: Modpack
description: Modpack にレイアウトを含める方法。
---

# Modpack での FancyMenu

FancyMenu のセットアップを modpack に含めるのはとても簡単で、いくつかの基本的な手順だけで済みます。

> このページは、**FancyMenu v3+** で完全に作成された FancyMenu セットアップ**のみ**を対象としています。旧方式のセットアップ（v2 で作成され、v3 に変換されたもの）を使っている場合、一部の手順が異なることがあります。
{.is-warning}

# FancyMenu セットアップを Modpack に含める

最初に行うことは、FancyMenu がすべてのデザインを保存している特別なフォルダを 1 つコピーすることです。

## 探す必要があるもの

1. **「Minecraft インスタンス」フォルダ:** これは、特定の Minecraft セットアップ（メニューを作成した環境など）に関するすべてのファイルが保存されている、PC 上のメインフォルダです。CurseForge や Modrinth などのランチャーでは、これを「インスタンス」または「プロファイル」と呼びます。
2. **`config` フォルダ:** Minecraft インスタンスのフォルダ内には、通常 `config` という名前のフォルダがあります。多くの mod が設定を保存する場所です。
3. **`fancymenu` フォルダ:** その `config` フォルダの中で、FancyMenu は `fancymenu` という独自のフォルダを作成します。これが必要な重要なフォルダです！

## インスタンスの保存場所を見つける方法

### CurseForge App を使っている場合

1. CurseForge を開きます。
2. 一覧から Minecraft のプロファイル/インスタンスを見つけて開きます。
3. 三点メニューをクリックします。
4. 「Open Folder」を選択します。これで、その Minecraft インスタンスのメインフォルダが開きます。

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### Modrinth App を使っている場合

1. Modrinth App を開きます。
2. 一覧から Minecraft のプロファイル/インスタンスを見つけて開きます。
3. 三点メニューをクリックします。
4. 「Open Folder」を選択します。これで、その Minecraft インスタンスのメインフォルダが開きます。

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### その他のランチャーの場合

使用している Minecraft セットアップに応じて、同様の「Open Folder」「Open Instance Folder」「View Files」などのオプションを探してください。

## FancyMenu セットアップをコピーする

1. セットアップをコピーしたい先の **MODPACK インスタンス** の `config` フォルダに移動します。
2. その中に `fancymenu` フォルダがあれば、**削除**します。
3. セットアップの元となる **SOURCE インスタンス** の `config` フォルダを開きます。
4. SOURCE インスタンスの `config` フォルダ内にある `fancymenu` フォルダを、MODPACK インスタンスの `config` フォルダへコピーします。
5. これで完了です。modpack インスタンスを再起動すると、セットアップが読み込まれるはずです。

> なお、FancyMenu v2 で作成された古い旧方式のセットアップ（v3 に変換済みでも）は、レイアウトのアセットを FancyMenu の `/config/fancymenu/assets/` フォルダ外に保存できました。そのため、その場合は modpack にすべてのアセットも含めるようにしてください。
{.is-danger}

# メニューバーとホットキーを無効にする

modpack 内で FancyMenu のメニューバーを表示したままにしたくはないはずなので、無効化しておきましょう。ただし、ホットキーを押すと再び表示できてしまうので、もう少し *強め* の対策をしましょう。

`/config/fancymenu/options.txt` に移動して、テキストエディタでファイルを開きます。

次に `modpack_mode` を `true` に設定して保存します。
これで、すべてのオーバーレイとホットキーが完全に無効になります。

再びレイアウトを編集できるようにするには、この設定を `false` に戻してください。

# ウェルカム画面を無効にする

多くの場合は不要ですが、まだウェルカム画面を閉じていない場合（ドキュメントを読むよう案内する画面）、`/config/fancymenu/options.txt` の `show_welcome_screen` を `false` に設定してください。

この画面は一度だけ表示され、**Open Documentation** ボタンをクリックすると自動で無効になります。そのため、手動で行う必要はほとんどありません。

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
