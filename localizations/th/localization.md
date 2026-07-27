---
title: การทำให้เลย์เอาต์รองรับหลายภาษา
description: แปลข้อความและเนื้อหาอื่น ๆ ของเลย์เอาต์ให้รองรับหลายภาษา
---

# การทำให้เลย์เอาต์รองรับหลายภาษา

ใช้ [**ช่องว่างสำหรับ Localize Text**](./placeholders#localize-text-local) สำหรับข้อความที่ต้องการแปล:

```text
{"placeholder":"local","values":{"key":"modpack.menu.play"}}
```

FancyMenu จะตรวจสอบข้อมูลภาษาที่ใช้งานอยู่ของ Minecraft ก่อน หากไม่พบคีย์ดังกล่าว จะไปตรวจสอบไฟล์การแปลแบบกำหนดเองของ FancyMenu ถ้าไม่มีแหล่งใดมีคีย์นั้น ระบบจะแสดงคีย์นั้นเอง

# ไฟล์การแปลแบบกำหนดเองของ FancyMenu

วางไฟล์ไว้ที่:

```text
<game-directory>/config/fancymenu/custom_locals/
```

สร้างโฟลเดอร์ย่อยสำหรับไฟล์การแปลของคุณ:

```text
custom_locals/
└── my_pack/
    └── text.json
```

ให้วางไฟล์การแปลไว้ภายในอย่างน้อยหนึ่งโฟลเดอร์ย่อยของ `custom_locals`; ไฟล์ที่วางไว้โดยตรงในรากของ `custom_locals` จะไม่ถูกโหลด รองรับโฟลเดอร์ย่อยซ้อนกันหลายชั้น

รูปแบบ UTF-8 ที่รองรับ:

| นามสกุล | รูปแบบ |
|---|---|
| `.json` | ออบเจ็กต์ JSON; ออบเจ็กต์ซ้อนกันจะกลายเป็นคีย์ที่คั่นด้วยจุด |
| `.lang` | บรรทัด `key=value` |
| `.properties` | ไวยากรณ์ Java properties |

ตัวอย่าง JSON:

```json
{
  "modpack": {
    "menu": {
      "play": "Play"
    }
  }
}
```

สิ่งนี้จะกำหนด `modpack.menu.play`.

FancyMenu จะรวมไฟล์ที่รองรับจากโฟลเดอร์ย่อยเหล่านี้เป็นพจนานุกรมการแปลแบบกำหนดเองชุดเดียว ให้ใช้แต่ละคีย์ในเพียงไฟล์เดียวเท่านั้น ไฟล์การแปลแบบกำหนดเองจะไม่สลับตามภาษาที่ Minecraft เลือกใช้; หากคุณต้องการให้สลับภาษาอัตโนมัติ ให้ใช้วิธี resource pack ด้านล่าง

ให้รีสตาร์ตไคลเอนต์หลังจากแก้ไขไฟล์การแปลแบบกำหนดเอง

# ข้อความเฉพาะภาษา

หากต้องการสลับอัตโนมัติตามภาษาที่ Minecraft เลือก ให้จัดเตรียมไฟล์ภาษาปกติของ Minecraft ผ่าน [resource pack](./resources#minecraft-resources-resource-packs):

```text
assets/<namespace>/lang/en_us.json
assets/<namespace>/lang/de_de.json
```

ใช้คีย์เดียวกันในแต่ละไฟล์ภาษา เปิดใช้งาน resource pack แล้วอ่านค่าด้วย [**ช่องว่างสำหรับ Localize Text**](./placeholders#localize-text-local)

# การแปลภาพและองค์ประกอบ

ใช้ [**เงื่อนไข Is Game Language**](./conditions#is-game-language-fancymenu_loading_requirement_is_language) เพื่อแสดงองค์ประกอบหรือเลย์เอาต์ที่แตกต่างกันสำหรับรหัสภาษาแต่ละแบบ เช่น `en_us` และ `de_de`
