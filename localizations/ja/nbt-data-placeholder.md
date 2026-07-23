---
title: NBT データプレースホルダー
description: エンティティ、ブロック、ストレージの NBT データを読み取ります。
---
# NBT データプレースホルダー

FancyMenu には 2 つの NBT プレースホルダーがあります:

| プレースホルダー | 実行先 | 利用可能なデータ |
|---|---|---|
| `nbt_data_get` | クライアント | クライアントから見えるエンティティとブロックエンティティ |
| `nbt_data_get_server` | サーバー | バニラの `/data get` の対象; サーバー側に FancyMenu が必要 |

# クライアント側プレースホルダー

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

## 値

| 値 | 必須 | 説明 |
|---|---|---|
| `source_type` | はい | `entity` または `block` |
| `entity_selector` | エンティティの場合 | クライアント側セレクター、UUID、または完全一致のエンティティ名 |
| `block_pos` | ブロックの場合 | `100 64 -200` のような、3つの絶対整数座標 |
| `nbt_path` | はい | `Health`、`Pos[0]`、`Inventory[0].id` などの NBT パス |
| `scale` | いいえ | 数値の `value` 結果に掛け算を行う; デフォルトは `1.0` |
| `return_type` | いいえ | `value`、`string`、`snbt`、`json`; デフォルトは `value` |

クライアント側のブロック位置では `~` や `^` 座標は使用できません。

## クライアントのエンティティセレクター

| セレクター | 初期対象 | デフォルトの順序 |
|---|---|---|
| `@s` | ローカルプレイヤー | 自分自身 |
| `@p` | プレイヤー | 最寄り |
| `@a` | プレイヤー | クライアントの反復順 |
| `@r` | プレイヤー | ランダム |
| `@e` | クライアントから見えるすべてのエンティティ | クライアントの反復順 |

`@e` は `sort=nearest` を追加しない限り最寄りのエンティティを選択しません。UUID を直接指定した検索や、完全一致のエンティティ名による検索もサポートされています。

サポートされるセレクターオプション:

| オプション | 説明 |
|---|---|
| `type` | エンティティ ID; 除外するには `!` を前置します |
| `name` | 完全一致の表示名; 除外するには `!` を前置します |
| `tag` | エンティティタグ; 除外するには `!` を前置します |
| `limit` | 正の結果数上限 |
| `sort` | `nearest`、`furthest`、`random`、`arbitrary` |
| `distance` | `..10` や `5..20` のようなバニラの距離範囲 |
| `x`, `y`, `z` | 検索の起点; 絶対値と `~` オフセットに対応 |
| `dx`, `dy`, `dz` | 起点からの検索ボックスサイズ |

ローカルの `^` 座標やその他のバニラセレクターオプションは、クライアントプレースホルダーではサポートされていません。

例:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@e[type=minecraft:zombie,sort=nearest,limit=1,distance=..20]","nbt_path":"Health"}}
```

## 戻り値の種類

| 種類 | 結果 |
|---|---|
| `value` | 数値タグは数値として整形され、`scale` が適用されます; 文字列タグはそのテキストを返します; その他のタグは SNBT 風のテキストを返します |
| `string` | タグの文字列値を返します。タグに文字列値がない場合は空文字列を返します |
| `snbt` | タグの SNBT 表現を返します |
| `json` | compound タグのみ: NBT の整形出力を含むシリアライズ済みの Minecraft テキストコンポーネントを返します |

クライアント側の `json` モードは、NBT を直接 JSON に変換するものではありません。

## 例

プレイヤーの空腹度:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel"}}
```

ホットバーの先頭アイテムの ID:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Inventory[{Slot:0b}].id","return_type":"string"}}
```

ブロックエンティティのアイテム数:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"block","block_pos":"100 64 -200","nbt_path":"Items[0].count"}}
```

# サーバー側プレースホルダー

`nbt_data_get_server` はサーバーの `/data get` の動作に従い、以下をサポートします:

- 完全なサーバー側エンティティセレクター。
- 絶対座標、相対座標 (`~`)、ローカル座標 (`^`) を使ったブロックターゲット。
- `source_type:"storage"` によるコマンドストレージ。

```text
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health","return_type":"value"}}
```

このプレースホルダーは、サーバー応答が届くまで空の値を返します。過剰なリクエストを避けるため、応答は短時間キャッシュされます。

# NBT パスの見つけ方

NBT パスを指定せずに対応するコマンドを使うと、利用可能なデータを確認できます:

```text
/data get entity @s
/data get block 100 64 -200
```

クライアント側の結果は、クライアントに同期されているデータに限定されます。無効な対象またはパスは空文字列を返し、詳細は `logs/latest.log` に書き込まれます。
