---
title: NBTデータプレースホルダー
description: NBTデータプレースホルダーの使い方。
---


# NBTデータの取得

これらのプレースホルダーは FancyMenu v3.8.0+ で利用できます。

**Client NBT Data Get** と **Server NBT Data Get** のプレースホルダーを使うと、Minecraft のエンティティやブロックから NBT（Named Binary Tag）データを取得できます。これは `/data get` コマンドに似ています。ゲーム状態、プレイヤーのステータス、またはワールドの条件に応じて変化する動的なレイアウトを作成するのに非常に便利です。

> このプレースホルダーは、モッドがエンティティやプレイヤーに追加するカスタム NBT データにアクセスできるため、特にモッド環境のゲームプレイで強力です。マナシステムを追加する魔法系モッド、カスタムステータスを持つRPG系モッド、エネルギー値を扱う技術系モッドなどを使っている場合でも、これらのモッド値を UI レイアウトに表示できます。
{.is-info}

## 概要

これらのプレースホルダーは、NBT パスを使って NBT データ構造から特定の値を取得します。プレイヤーの体力、空腹度、インベントリのアイテム、ブロックの状態、マナやエネルギーのようなモッド由来の属性など、さまざまな情報を取得できます。

クライアント側のプレースホルダーの大きな利点は、純粋にクライアント側だけで動作するため、サーバーに FancyMenu を入れる必要がないことです。ただし、その代わり、NBT データに関するすべての情報が常にすべてのクライアントから見えるわけではないため、対応範囲はかなり限られます。

サーバー側のバージョンはサーバーに FancyMenu をインストールする必要がありますが、NBT として保存されているほぼ**すべて**に対して**完全対応**できます。

このページではクライアント側のバージョン（`nbt_data_get`）に焦点を当てますが、サーバー側のバージョン（`nbt_data_get_server`）でも基本的には同様に動作します。

## プレースホルダーの構文

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

## 必須値

| 値 | 説明 | オプション |
|-------|-------------|---------|
| `source_type` | データソースの種類 | `entity` または `block` |
| `nbt_path` | 取得する NBT パス | 例: `Health`、`foodLevel`、`Pos[0]`、`Inventory[0].id` |

## 条件付き値

`source_type` に応じて、次のいずれかが必要です。

| 値 | 必要になる条件 | 説明 | 形式 |
|-------|--------------|-------------|--------|
| `entity_selector` | `source_type` が `entity` のとき | どのエンティティを取得するかを選択します | `@s`（自分自身）、`@p`（最寄りのプレイヤー）、`@e`（最寄りのエンティティ）、UUID、またはエンティティ名 |
| `block_pos` | `source_type` が `block` のとき | ブロックの座標 | `x y z`（例: `100 64 -200`） |

## 任意の値

| 値 | 説明 | デフォルト | オプション |
|-------|-------------|---------|---------|
| `scale` | 数値の倍率 | `1.0` | 任意の小数 |
| `return_type` | 返されたデータの形式 | `value` | `value`（数値/サイズ）、`string`（テキスト）、`snbt`（整形された NBT）、`json`（JSON 形式） |

## 返り値の種類の説明

- **`value`** - 数値またはサイズを返します（デフォルト）
  - 数値の場合: 数値を返します（必要に応じて倍率を適用）
  - 文字列の場合: 文字列の長さを返します
  - リスト/配列の場合: 要素数を返します
  - 複合タグの場合: タグ数を返します

- **`string`** - NBT データの実際の文字列値を返します

- **`snbt`** - データを SNBT（Stringified NBT）形式で返します

- **`json`** - データを JSON 形式で返します（複合タグのみ）

## 例

### プレイヤーの体力を取得
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

### プレイヤーの空腹度を取得
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel"}}
```

### プレイヤーの X 座標を取得
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Pos[0]"}}
```

### ホットバーの最初のスロットのアイテムを取得
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Inventory[{Slot:0b}].id","return_type":"string"}}
```

### 特定の位置のブロックデータを取得
```json
{"placeholder":"nbt_data_get","values":{"source_type":"block","block_pos":"100 64 -200","nbt_path":"Items[0].Count"}}
```

### 体力の割合を倍率付きで取得（Health * 5）
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health","scale":"5"}}
```

## 利用可能な NBT パスを見つける方法

### 方法 1: `/data get` コマンドを使う（推奨）

利用可能な NBT パスを調べる最も簡単な方法は、ゲーム内でパスを指定せずに `/data get` コマンドを使うことです。

1. **エンティティの場合:** `/data get entity @p`
2. **ブロックの場合:** `/data get block <x> <y> <z>`

これにより対象の利用可能な NBT データがすべて表示され、使える正確なパスを確認できます。

#### 出力の見方

`/data get entity @p` を実行すると、次のような出力が表示されます。

```
Player616 has the following entity data: {Brain: {memories: {}}, 
HurtByTimestamp: 0, SleepTimer: 0s, Invulnerable: 0b, FallFlying: 
0b, PortalCooldown: 0, AbsorptionAmount: 0.0f, abilities: 
{invulnerable: 1b, mayfly: 1b, instabuild: 1b, walkSpeed: 0.1f, 
mayBuild: 1b, flying: 1b, flySpeed: 0.05f}, FallDistance: 0.0f, 
recipeBook: {recipes: ["minecraft:crafting_table"]}, 
DeathTime: 0s, XpSeed: -380875747, XpTotal: 0, UUID: [I; 1379890089, -1732753738, 
-2135065633, -718799804], playerGameType: 1, seenCredits: 
0b, Motion: [0.0d, 0.0d, 0.0d], Health: 20.0f, foodSaturationLevel: 
5.0f, ...}
```

この出力から有効なパスを抽出するには、次のようにします。

1. **単純な値** - キー名をそのまま使います:
   - `Health: 20.0f` → パス: `Health`
   - 例: `{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}`

2. **入れ子の値** - ドット記法で入れ子のデータにアクセスします:
   - `abilities: {walkSpeed: 0.1f}` → パス: `abilities.walkSpeed`
   - 例: `{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"abilities.walkSpeed"}}`

3. **配列の値** - インデックス番号を角括弧で指定します:
   - `Motion: [0.0d, 0.0d, 0.0d]` → Y 方向のモーションのパス: `Motion[1]`
   - 例: `{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Motion[1]"}}`

### 方法 2: NBT Autocomplete モッド

NBT パスをより簡単に見つけるには、**NBT Autocomplete** モッドの導入を検討してください。
- Fabric と Forge に対応（Minecraft 1.21.x）
- コマンド入力中にゲーム内でオートコンプリート候補を表示
- 利用可能なタグ名と型を表示
- [Modrinth](https://modrinth.com/mod/nbt-autocomplete) | [CurseForge](https://www.curseforge.com/minecraft/mc-mods/nbt-autocomplete)

## よく使う NBT パス

### プレイヤーエンティティ
- `Health` - 現在の体力（float）
- `foodLevel` - 空腹度（int、0-20）
- `foodSaturationLevel` - 満腹度（float）
- `XpLevel` - 経験値レベル（int）
- `XpP` - 経験値進行度（float、0.0-1.0）
- `Pos[0]`、`Pos[1]`、`Pos[2]` - X、Y、Z 座標
- `Inventory` - プレイヤーのインベントリ配列
- `SelectedItemSlot` - 現在選択中のホットバーのスロット（int、0-8）

### よくあるブロックの NBT
- `Items` - コンテナの中身（チェスト、かまどなど）
- `CustomName` - ブロックのカスタム名
- `Lock` - コンテナのロック文字列

### よくあるモッド由来の NBT 例
- **魔法系モッド**: `playerMana`、`mana.current` などの形式でマナを保存していることが多い
- **技術系モッド**: `energy`、`forgeEnergy`、`energyStorage.energy` などのエネルギー値
- **RPG系モッド**: `customStats.strength`、`rpgAttributes.level` などのカスタムステータス

モッド由来の NBT パスを見つけるには、モッドを有効にした状態で `/data get entity @p` を使い、モッドが追加したカスタムタグを確認してください。

## 制限事項

- **クライアントでは storage にアクセス不可** - storage データソースはクライアント側ではサポートされません（サーバー側のみ）
- **パフォーマンス** - NBT データへ頻繁にアクセスするとパフォーマンスに影響する場合があります
- パスが無効、またはデータにアクセスできない場合は空文字列を返します

## ヒント

1. まずは必ずゲーム内で `/data get` を使って NBT パスをテストしましょう
2. `scale` パラメータを使うと、値をパーセンテージなどの便利な形式に変換できます
3. 一部の NBT データはクライアントに同期されない場合があることを覚えておきましょう
4. エンティティセレクターは描画距離内のエンティティに限定されます
5. モッドコンテンツについては、モッドのドキュメントを確認するか `/data get` を使ってカスタム NBT パスを見つけてください
