---
title: レイアウトのローカライズ
description: レイアウトの内容をローカライズする方法。
---

# レイアウトのローカライズ

FancyMenu を使うと、テキスト内容だけでなく、要素全体やレイアウト全体までローカライズできます！

# テキスト内容

FancyMenu では、ゲームに独自のローカライズを追加できます。
これらは **Localize Text** プレースホルダーと一緒に使うことで、現在のゲーム言語に合わせてテキストをローカライズできます。

## バニラ Minecraft のローカライズキーを使う

独自のローカライズを作成する前に、既存の Minecraft のローカライズキーを使いたいかもしれません。これにより時間を節約でき、バニラ Minecraft のテキストとの一貫性も保てます。

### バニラのローカライズキーを見つける

Minecraft のローカライズキーを見つける最も簡単な方法は、オンラインでゲームのアセットファイルを閲覧することです。

1. **MCAsset.cloud を開く:**  
   [https://mcasset.cloud/](https://mcasset.cloud/) にアクセスしてください。このサイトでは、ゲームからファイルを抽出しなくても Minecraft のアセットを閲覧できます。

2. **言語ファイルへ移動する:**  
   - ドロップダウンから Minecraft のバージョンを選択する
   - 次へ移動: `assets` → `minecraft` → `lang`
   - `en_us.json` を開くと、英語のローカライズ一覧を確認できます

3. **必要なキーを見つける:**  
   - ブラウザの検索機能（Ctrl+F または Cmd+F）で特定のテキストを探す
   - 形式は `"key": "text"` です。コロン (`:`) の前の最初の引用符内の部分がキーです
   - 例: `"menu.singleplayer": "Singleplayer"` - キーは `menu.singleplayer` です

### Mod のローカライズキーを使う

他の Mod を導入している場合は、そのローカライズキーも使えます。

1. 利用可能なキーについて Mod のドキュメントを確認する
2. オープンソースであれば、Mod の言語ファイルを閲覧する

## カスタムローカライズファイル

ローカライズファイルは、複数の言語で利用できるようにするすべてのテキスト内容を含むテキストファイルです。翻訳可能な各テキストには一意のキーがあり、Minecraft はローカライズファイル内から正しい翻訳テキストを見つけられます。

- **デフォルトファイル (en_us.json):**  
  英語（米国）です。他の言語ファイルが選択されていない場合に使用される、バックアップ用の言語ファイルです。

- **その他の言語ファイル:**  
  たとえば、ドイツ語を使うプレイヤー向けに `de_de.json` というドイツ語ファイルを作成できます。

### カスタムローカライズファイルの作成方法

必ず `en_us.json` ファイルが必要です！ これがないと、何か問題が起きたときや未対応の言語が設定されたときにゲームのフォールバック先がなくなります。

1. **テキストエディタを開く:**  
   メモ帳（Windows）、TextEdit（Mac）、または任意のシンプルなテキストエディタを使用します。

2. **JSON コードを書く:**  
   独自のキーを使ってファイルを作成します。キーとは、Minecraft がテキストを見つけるために使う一意の名前です。たとえば:
   
   ```json
   {
     "modpack_name.custom.localization.key": "ここに独自のテキストを入力",
     "modpack_name.another.key": "別のメッセージ"
   }
   ```

3. **ファイルを保存する:**  
   デフォルトの英語テキスト用として `en_us.json` という名前で保存します。

その後、ドイツ語のような翻訳版を追加したい場合は、`en_us.json` の内容を新しいファイルにコピーし、実際のテキストだけを翻訳してください。キーは翻訳しないでください！ ゲームがテキストを見つけられるように、キーは同じままにしておく必要があります。

ドイツ語の場合は、ファイル名を `de_de.json` にします。他の言語については、正しい言語コードを [この Minecraft wiki のページ](https://minecraft.wiki/w/Language) で確認し、それに合わせてファイル名を付けてください。自分の言語の **"in-game locale code"** を探してください。

## MC 1.21.4 用の Minecraft リソースパックを作成する

ローカライズファイルの準備ができたので、Minecraft でそれを読み込む方法が必要です。そのためにリソースパックを使います。このパックはデフォルトで有効化し、必要であれば Modpack のユーザーが触れられないように隠すこともできます。

**リソースパック** は、ゲームの見た目や雰囲気を変えるファイルをまとめた ZIP ファイルです。

### リソースパックの作成手順

1. **新しいフォルダを作成する:**  
   `my_custom_pack` のような名前のフォルダを作成し、その中にカスタムローカライズファイルを追加します。

2. **パックファイル (`pack.mcmeta`) を作成する:**  
   フォルダの中に `pack.mcmeta` というファイルを作成し、以下の内容を記述します:
   
   ```json
   {
     "pack": {
       "pack_format": 16,
       "description": "ローカライズを含む自作パック"
     }
   }
   ```
   
   *注意: `pack_format` 16 は Minecraft 1.21.4 用です。*

3. **ローカライズファイルを追加する:**  
   リソースパックフォルダ内に、次のフォルダ構成を作成します:
   
   ```
   my_custom_pack/
   ├── assets/
   │   └── minecraft/
   │       └── lang/
   │           ├── en_us.json
   │           └── de_de.json
   └── pack.mcmeta
   ```
   
   独自の `en_us.json`（および `de_de.json` のような他の言語ファイル）を `lang` フォルダに配置します。

4. **リソースパックを ZIP 化する:**  
   フォルダの準備ができたら、**フォルダ全体を ZIP ファイルに圧縮**します。ZIP ファイル名は **my_custom_pack.zip** にしてください。これはこのガイド全体で使う例の名前です。

## リソースパックを配置する場所

**my_custom_pack.zip** を **Minecraft の Resourcepacks フォルダ** に配置します。このフォルダは通常、次の場所にあります。

- **Windows:** `%appdata%\.minecraft\resourcepacks`
- **Mac:** `~/Library/Application Support/minecraft/resourcepacks`
- **Linux:** `~/.minecraft/resourcepacks`

> Modpack の場合、`resourcepacks` フォルダはパックのインスタンスディレクトリ内にあります。
{.is-warning}

## 「Resource Pack Overrides」でパックを自動読み込みする

**Resource Pack Overrides** Mod を使うと、リソースパックをデフォルトで有効化できます。

### パックを自動読み込みする手順

1. **Mod をインストールする:**  
   [CurseForge](https://www.curseforge.com/minecraft/mc-mods/resource-pack-overrides) または [Modrinth](https://modrinth.com/mod/resource-pack-overrides) からダウンロードしてインストールします。

2. **設定ファイルを見つける:**  
   `.minecraft/config/resourcepackoverrides.json` にあるファイルを探します。  
   *ファイルが存在しない場合は、手動で作成してください。*

3. **設定ファイルを編集する:**  
   ファイルを開き、ファイル名を使って `default_packs` リストにリソースパックを追加します。
   
   ```json
   {
     "schema_version": 2,
     "default_packs": [
       "file/my_custom_pack.zip"
     ]
   }
   ```
   
   これにより、ゲーム起動時に Minecraft がリソースパックを自動的に読み込むようになります。

   **`file/` プレフィックスを付けることが重要です！**


*注意: リスト内のリソースパックは逆順に適用されます。つまり、リストの一番上にあるパックは、ゲーム内のリソースパックメニューでは他のパックの下に表示されます。*

## 選択画面でリソースパックを非表示にする

プレイヤーにリソースパック選択画面で見せたくない場合は、リソースパックを非表示にできます。

### 非表示にする方法

1. **もう一度設定ファイルを編集する:**  
   同じ `.minecraft/config/resourcepackoverrides.json` に、パック用の上書き設定を追加します:
   
   ```json
   {
     "schema_version": 2,
     "default_packs": [
       "file/my_custom_pack.zip"
     ],
     "pack_overrides": {
       "file/my_custom_pack.zip": {
         "hidden": true
       }
     }
   }
   ```
   
   この設定により、**my_custom_pack.zip** は選択画面から非表示になりますが、引き続き自動で読み込まれます。

## FancyMenu で新しいローカライズキーを使う

カスタムローカライズファイルが読み込まれたら、FancyMenu のレイアウトで新しいキーを使えます。

1. **テキストベースの要素を編集する:**  
   FancyMenu を開き、ボタンやテキスト要素などを選びます。

2. **Placeholders ボタンをクリックする:**  
   テキストエディタの右上にある Placeholders ボタンを探します。（表示されない場合、その要素はプレースホルダーに対応していない可能性があります。）

3. **Localize Text プレースホルダーを挿入する:**  
   Localize Text プレースホルダーは JSON スニペットとして表示されます。次のようになります:
   
   ```json
   {"placeholder":"local","values":{"key":"localization.key"}}
   ```
   
   `localization.key` を自分のカスタムキーに置き換えます。たとえば、ローカライズファイル内のキーを使いたい場合は次のようにします:
   
   ```json
   {"placeholder":"local","values":{"key":"modpack_name.custom.localization.key"}}
   ```

以上です！ テキストエディタで編集中でない限り、このプレースホルダーは実際のローカライズ済みテキストに置き換えられます。

プレースホルダーは常に、現在のゲーム言語に合わせてテキスト内容をローカライズすることを覚えておいてください。

# 非テキスト内容（画像など）

FancyMenu では、画像や基本的に任意の要素もローカライズできます。

そのためには **loading requirements** を使う必要があります。より具体的には **Is Game Language** requirement を使います。

**Is Game Language** requirement を使うと、特定のゲーム言語が設定されている場合にのみ要素やレイアウトを表示できます。たとえば、テキストを含む画像要素を 2 つ用意し、言語が日本語なら日本語テキスト版、英語なら英語テキスト版を表示する、といったことができます。

要素に loading requirements を設定するには、右クリックして **Loading Requirements** をクリックします。

レイアウト全体に loading requirements を設定するには、レイアウトエディタの背景を右クリックして **Loading Requirements [Layout-Wide]** をクリックします。
