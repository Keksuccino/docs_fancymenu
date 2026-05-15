---
title: ตัวยึดข้อมูล NBT
description: วิธีใช้งานตัวยึดข้อมูล NBT
---


# การดึงข้อมูล NBT

ตัวยึดเหล่านี้มีให้ใช้งานใน FancyMenu v3.8.0+.

ตัวยึด **Client NBT Data Get** และ **Server NBT Data Get** ช่วยให้คุณดึงข้อมูล NBT (Named Binary Tag) จากเอนทิตีและบล็อกใน Minecraft ได้ คล้ายกับคำสั่ง `/data get` ซึ่งมีประโยชน์มากสำหรับการสร้างเลย์เอาต์แบบไดนามิกที่ตอบสนองต่อสถานะเกม ค่าสถานะผู้เล่น หรือสภาพแวดล้อมในโลกเกม

> ตัวยึดนี้ทรงพลังเป็นพิเศษสำหรับการเล่นแบบใช้ม็อด เพราะสามารถเข้าถึงข้อมูล NBT แบบกำหนดเองที่ม็อดเพิ่มให้กับเอนทิตีและผู้เล่นได้ ไม่ว่าคุณจะเล่นม็อดสายเวทมนตร์ที่เพิ่มระบบมานา ม็อด RPG ที่มีค่าสถานะแบบกำหนดเอง หรือม็อดเทคโนโลยีที่มีค่าพลังงาน คุณก็สามารถแสดงค่าพวกนี้ใน UI ของคุณได้
{.is-info}

## ภาพรวม

ตัวยึดเหล่านี้จะดึงค่าที่เฉพาะเจาะจงจากโครงสร้างข้อมูล NBT โดยใช้ NBT path คุณสามารถดึงพลังชีวิตของผู้เล่น ความหิว ไอเท็มในคลัง ข้อมูลสถานะของบล็อก คุณสมบัติแบบม็อด เช่น มานาหรือพลังงาน และอื่น ๆ ได้อีกมากมาย

ตัวยึดฝั่งไคลเอนต์มีข้อดีสำคัญคือทำงานได้โดยฝั่งไคลเอนต์ล้วน ๆ ดังนั้นคุณไม่จำเป็นต้องติดตั้ง FancyMenu บนเซิร์ฟเวอร์ แต่ในขณะเดียวกันก็มีข้อจำกัดมากกว่า เพราะไม่ใช่ทุกอย่างที่เกี่ยวกับข้อมูล NBT จะมองเห็นได้สำหรับไคลเอนต์ทั้งหมดตลอดเวลา

ตัวยึดฝั่งเซิร์ฟเวอร์ต้องติดตั้ง FancyMenu บนเซิร์ฟเวอร์ แต่จะรองรับได้ **เต็มรูปแบบ** กับแทบ **ทุกอย่าง** ที่ถูกเก็บเป็น NBT

หน้านี้จะเน้นที่เวอร์ชันฝั่งไคลเอนต์ (`nbt_data_get`) แต่ทุกอย่างทำงานคล้ายกันมากสำหรับเวอร์ชันฝั่งเซิร์ฟเวอร์ (`nbt_data_get_server`) เช่นกัน

## ไวยากรณ์ของตัวยึด

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

## ค่าที่จำเป็น

| ค่า | คำอธิบาย | ตัวเลือก |
|-------|-------------|---------|
| `source_type` | ประเภทของแหล่งข้อมูล | `entity` หรือ `block` |
| `nbt_path` | NBT path ที่จะใช้ค้นหา | เช่น `Health`, `foodLevel`, `Pos[0]`, `Inventory[0].id` |

## ค่าตามเงื่อนไข

ขึ้นอยู่กับ `source_type` คุณจะต้องใช้หนึ่งในรายการต่อไปนี้:

| ค่า | ต้องใช้เมื่อ | คำอธิบาย | รูปแบบ |
|-------|--------------|-------------|--------|
| `entity_selector` | source_type เป็น `entity` | เลือกเอนทิตีที่จะค้นหา | `@s` (ตัวเอง), `@p` (ผู้เล่นที่ใกล้ที่สุด), `@e` (เอนทิตีที่ใกล้ที่สุด), UUID หรือชื่อเอนทิตี |
| `block_pos` | source_type เป็น `block` | พิกัดของบล็อก | `x y z` (เช่น `100 64 -200`) |

## ค่าตัวเลือกเสริม

| ค่า | คำอธิบาย | ค่าเริ่มต้น | ตัวเลือก |
|-------|-------------|---------|---------|
| `scale` | ตัวคูณสเกลสำหรับค่าตัวเลข | `1.0` | ตัวเลขทศนิยมใด ๆ |
| `return_type` | วิธีจัดรูปแบบข้อมูลที่ส่งกลับ | `value` | `value` (ตัวเลข/ขนาด), `string` (ข้อความ), `snbt` (NBT ที่จัดรูปแบบแล้ว), `json` (รูปแบบ JSON) |

## อธิบายประเภทผลลัพธ์

- **`value`** - ส่งกลับค่าตัวเลขหรือขนาด (ค่าเริ่มต้น)
  - สำหรับตัวเลข: ส่งกลับตัวเลข (ปรับสเกลได้)
  - สำหรับสตริง: ส่งกลับความยาวของสตริง
  - สำหรับรายการ/อาร์เรย์: ส่งกลับจำนวนไอเท็ม
  - สำหรับคอมพาวด์: ส่งกลับจำนวนแท็ก

- **`string`** - ส่งกลับค่าสตริงจริงของข้อมูล NBT

- **`snbt`** - ส่งกลับข้อมูลในรูปแบบ SNBT (Stringified NBT)

- **`json`** - ส่งกลับข้อมูลในรูปแบบ JSON (ใช้ได้เฉพาะ compound tags)

## ตัวอย่าง

### ดึงพลังชีวิตของผู้เล่น
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

### ดึงระดับความหิวของผู้เล่น
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel"}}
```

### ดึงพิกัดแกน X ของผู้เล่น
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Pos[0]"}}
```

### ดึงไอเท็มในช่องฮอตบาร์ช่องแรก
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Inventory[{Slot:0b}].id","return_type":"string"}}
```

### ดึงข้อมูลบล็อกที่ตำแหน่งเฉพาะ
```json
{"placeholder":"nbt_data_get","values":{"source_type":"block","block_pos":"100 64 -200","nbt_path":"Items[0].Count"}}
```

### ดึงเปอร์เซ็นต์พลังชีวิตแบบสเกลแล้ว (Health * 5)
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health","scale":"5"}}
```

## วิธีค้นหา NBT Path ที่มีอยู่

### วิธีที่ 1: ใช้คำสั่ง `/data get` (แนะนำ)

วิธีที่ง่ายที่สุดในการค้นหา NBT path ที่ใช้ได้คือใช้คำสั่ง `/data get` ในเกมโดยไม่ระบุ path:

1. **สำหรับเอนทิตี:** `/data get entity @p`
2. **สำหรับบล็อก:** `/data get block <x> <y> <z>`

คำสั่งนี้จะแสดงข้อมูล NBT ทั้งหมดที่มีสำหรับเป้าหมายนั้น ช่วยให้คุณเห็น path ที่ใช้ได้อย่างชัดเจน

#### ทำความเข้าใจกับผลลัพธ์

เมื่อคุณรัน `/data get entity @p` คุณจะเห็นผลลัพธ์คล้ายกับนี้:

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

วิธีดึง path ที่ถูกต้องจากผลลัพธ์นี้:

1. **ค่าธรรมดา** - ใช้ชื่อคีย์โดยตรง:
   - `Health: 20.0f` → Path: `Health`
   - ตัวอย่าง: `{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}`

2. **ค่าที่ซ้อนกัน** - ใช้สัญกรณ์จุดเพื่อเข้าถึงข้อมูลที่ซ้อนอยู่:
   - `abilities: {walkSpeed: 0.1f}` → Path: `abilities.walkSpeed`
   - ตัวอย่าง: `{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"abilities.walkSpeed"}}`

3. **ค่าแบบอาร์เรย์** - ใช้วงเล็บเหลี่ยมพร้อมดัชนี:
   - `Motion: [0.0d, 0.0d, 0.0d]` → Path สำหรับการเคลื่อนที่แกน Y: `Motion[1]`
   - ตัวอย่าง: `{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Motion[1]"}}`

### วิธีที่ 2: ม็อด NBT Autocomplete

หากต้องการค้นหา NBT path ได้ง่ายขึ้น ลองติดตั้งม็อด **NBT Autocomplete**:
- รองรับ Fabric และ Forge (Minecraft 1.21.x)
- แสดงคำแนะนำแบบ autocomplete ในเกมขณะพิมพ์คำสั่ง
- แสดงชื่อแท็กและชนิดข้อมูลที่มีอยู่
- [Modrinth](https://modrinth.com/mod/nbt-autocomplete) | [CurseForge](https://www.curseforge.com/minecraft/mc-mods/nbt-autocomplete)

## NBT Path ที่พบบ่อย

### เอนทิตีผู้เล่น
- `Health` - พลังชีวิตปัจจุบัน (float)
- `foodLevel` - ระดับความหิว (int, 0-20)
- `foodSaturationLevel` - ระดับความอิ่ม (float)
- `XpLevel` - ระดับประสบการณ์ (int)
- `XpP` - ความคืบหน้าประสบการณ์ (float, 0.0-1.0)
- `Pos[0]`, `Pos[1]`, `Pos[2]` - พิกัด X, Y, Z
- `Inventory` - อาร์เรย์คลังของผู้เล่น
- `SelectedItemSlot` - ช่องฮอตบาร์ที่เลือกอยู่ (int, 0-8)

### NBT ของบล็อกที่พบบ่อย
- `Items` - เนื้อหาภายในคอนเทนเนอร์ (หีบ เตาเผา ฯลฯ)
- `CustomName` - ชื่อแบบกำหนดเองของบล็อก
- `Lock` - สตริงล็อกสำหรับคอนเทนเนอร์

### ตัวอย่าง NBT จากม็อดที่พบบ่อย
- **ม็อดเวทมนตร์**: มักเก็บมานาเป็น `playerMana`, `mana.current` หรือคล้ายกัน
- **ม็อดเทค**: ค่าพลังงาน เช่น `energy`, `forgeEnergy`, หรือ `energyStorage.energy`
- **ม็อด RPG**: ค่าสถานะแบบกำหนดเอง เช่น `customStats.strength`, `rpgAttributes.level`

หากต้องการหา NBT path ของม็อด ให้ใช้ `/data get entity @p` ขณะที่ม็อดกำลังทำงานอยู่ และดูแท็กแบบกำหนดเองที่ม็อดเพิ่มเข้ามา

## ข้อจำกัด

- **เข้าถึง storage ฝั่งไคลเอนต์ไม่ได้** - แหล่งข้อมูล storage ไม่รองรับฝั่งไคลเอนต์ (รองรับเฉพาะฝั่งเซิร์ฟเวอร์)
- **ประสิทธิภาพ** - การเข้าถึงข้อมูล NBT บ่อย ๆ อาจส่งผลต่อประสิทธิภาพ
- จะส่งกลับสตริงว่างหาก path ไม่ถูกต้องหรือไม่สามารถเข้าถึงข้อมูลได้

## เคล็ดลับ

1. ทดสอบ NBT path ในเกมก่อนเสมอโดยใช้ `/data get`
2. ใช้พารามิเตอร์ `scale` เพื่อแปลงค่าเป็นเปอร์เซ็นต์หรือรูปแบบที่มีประโยชน์อื่น ๆ
3. จำไว้ว่าข้อมูล NBT บางส่วนอาจไม่ถูกซิงก์ไปยังไคลเอนต์
4. ตัวเลือกเอนทิตีจำกัดเฉพาะเอนทิตีที่อยู่ภายในระยะการเรนเดอร์
5. สำหรับคอนเทนต์ที่มาจากม็อด ให้ตรวจสอบเอกสารของม็อดหรือใช้ `/data get` เพื่อค้นหา NBT path แบบกำหนดเอง
