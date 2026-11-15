---
title: ตัวแปร
description: วิธีสร้างและใช้ตัวแปร
sourceBlobSha: dcd1512bc7f20f3ab535205f24a67c6489231e11
---

# ตัวแปรใน FancyMenu

ตัวแปรใช้เก็บค่าข้อความที่เลย์เอาต์ การกระทำ เพลซโฮลเดอร์ ข้อกำหนด ลิสเทนเนอร์ ตัวจัดตารางเวลา และ Custom GUI สามารถนำกลับมาใช้ได้

## การสร้างตัวแปร

หากต้องการสร้างตัวแปรใน FancyMenu:

1. ตรวจสอบให้แน่ใจว่าขณะนี้คุณไม่ได้อยู่ใน Layout Editor
2. คลิกแถบเมนูที่ด้านบนของหน้าจอ
3. ไปที่ **Customization -> Variables -> Manage Variables**
4. ในหน้าจอ "Manage Variables" ที่ปรากฏขึ้น ให้คลิกปุ่ม **Add Variable**
5. ป้อนชื่อสำหรับตัวแปรใหม่ แล้วคลิก **OK**

เพียงเท่านี้! ตัวแปรของคุณก็พร้อมใช้งานแล้ว คุณสามารถดูตัวแปรดังกล่าวได้ในหน้าจอ "Manage Variables"

หน้าต่าง Manage Variables รองรับเมนูบริบทเมื่อคลิกขวา การนำทางด้วยแป้นพิมพ์ การคัดลอก/วาง การเลิกทำ/ทำซ้ำ การค้นหาโดยพิมพ์ข้อความ ใช้ **Delete** เพื่อลบ และใช้ **Ctrl/Command + S** เพื่อบันทึก

## การกำหนดค่าตัวแปร

ตัวแปรว่างเพียงอย่างเดียวไม่ค่อยมีประโยชน์นัก หากต้องการให้ตัวแปรทำงานตามที่ต้องการ คุณต้องใส่ข้อมูลลงในตัวแปรนั้น ใน FancyMenu เรียกการดำเนินการนี้ว่า "การกำหนดค่าตัวแปร"

มีสองวิธีหลักในการกำหนดค่าตัวแปร:

1. ในหน้าจอ "Manage Variables" ค้นหาตัวแปรในรายการ คลิกตัวแปรนั้น แล้วคลิก **Set Value** จากนั้นป้อนข้อมูลที่ต้องการจัดเก็บ

2. ขณะปรับแต่งเมนู ให้ใช้การกระทำ [**Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable) กับองค์ประกอบ [Button](./elements#button), [Slider](./elements#slider) หรือ [Ticker](./elements#ticker)

ตัวอย่างเช่น สร้างตัวแปรชื่อ `clicks` แล้วเพิ่มการกระทำ [**Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable) ให้กับปุ่ม:

```
clicks:{"placeholder":"calc","values":{"expression":"{"placeholder":"getvariable","values":{"name":"clicks"}} + 1"}}
```

การทำงานมีดังนี้:
1. เพลซโฮลเดอร์ [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable) จะดึงค่าปัจจุบันของตัวแปร `clicks`
2. เพลซโฮลเดอร์ [**Calculator**](./placeholders#calculator-calc) จะนำค่านั้นมาบวก 1
3. ผลลัพธ์จะถูกจัดเก็บกลับไปใน `clicks` โดยใช้การกระทำ [**Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable)

ดังนั้นทุกครั้งที่คลิกปุ่ม ตัวแปร `clicks` จะเพิ่มขึ้นทีละ 1 ซึ่งทำหน้าที่นับจำนวนครั้งที่คลิกทั้งหมด

## การใช้ตัวแปร

เมื่อคุณมีตัวแปรที่เก็บข้อมูลแล้ว คุณสามารถใช้ข้อมูลดังกล่าวในส่วนต่าง ๆ ของการปรับแต่งเมนูได้:

* [**Loading Requirements**](./conditions): ตรวจสอบค่าของตัวแปรเพื่อควบคุมเวลาที่องค์ประกอบจะแสดง ตัวอย่างเช่น แสดงองค์ประกอบเมื่อ `clicks` มีค่ามากกว่า 5 โดยใช้ [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number) ร่วมกับเพลซโฮลเดอร์ [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable)

* **เพลซโฮลเดอร์**: แทรกตัวแปรลงในข้อความด้วยเพลซโฮลเดอร์ [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable) ตัวอย่างเช่น `{"placeholder":"getvariable","values":{"name":"clicks"}}`

* **เพลซโฮลเดอร์ซ้อนกัน**: คุณสามารถใช้เพลซโฮลเดอร์ [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable) ภายในเพลซโฮลเดอร์ [**Calculator**](./placeholders#calculator-calc) ได้

* **การกระทำ**: ตัวแปรสามารถสร้างพฤติกรรมแบบไดนามิกได้:
  - ใช้คำสั่ง **IF** ใน [สคริปต์การกระทำ](./action-scripts#what-are-statements) ร่วมกับ [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number) และเพลซโฮลเดอร์ [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable)
  - ใช้เพลซโฮลเดอร์ [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable) ร่วมกับ [**Copy Text to Clipboard**](./action-scripts#copy-text-to-clipboard-copytoclipboard)
  - ใช้ตัวแปรใน [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui) เพื่อเลือกหน้าจอจากความคืบหน้าหรือการตั้งค่าที่จัดเก็บไว้

## ตัวอย่างการใช้ตัวแปร

ต่อไปนี้คือตัวอย่างบางส่วนเพื่อเป็นแนวทางสำหรับการใช้ตัวแปรของคุณเอง:

1. **คะแนนสูงสุด**: สร้างตัวแปร `highscore` และปุ่มที่กำหนดค่าให้ตัวแปรนี้เป็นคะแนนปัจจุบันของผู้เล่น หากคะแนนดังกล่าวสูงกว่าค่าที่มีอยู่ แสดงค่าด้วยเพลซโฮลเดอร์ [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable)

2. **ตัวเลือกความยาก**: สร้างตัวแปรสำหรับระดับความยากของเกม เช่น `easy`, `medium` และ `hard` ใช้ปุ่มเพื่อกำหนดค่าตัวแปรระดับความยาก และแสดง/ซ่อนองค์ประกอบตามระดับความยากที่เลือก

3. **ความคืบหน้าของบทสอน**: เพิ่มตัวแปรเพื่อติดตามความคืบหน้าของผู้เล่นในบทสอน เช่น `tutorial_step` เพิ่มค่าตัวแปรเมื่อผู้เล่นทำแต่ละขั้นตอนเสร็จ และใช้ข้อกำหนดการโหลดเพื่อค่อย ๆ แสดงส่วนต่าง ๆ ของเมนูเพิ่มเติม

## การคงอยู่ ขอบเขต และการจัดเก็บ

ตัวแปรจะถูกใช้ร่วมกันภายในอินสแตนซ์ Minecraft ปัจจุบัน โดยไม่ได้แยกตามเลย์เอาต์ โลก เซิร์ฟเวอร์ หรือผู้เล่น

ค่าต่าง ๆ จะถูกบันทึกทันทีใน `<game-directory>/config/fancymenu/user_variables.db` และยังคงอยู่หลังจากเริ่มเกมใหม่

- **Reset on Launch** จะล้างตัวแปรนั้นในการเริ่มเกมครั้งถัดไป
- [**Clear All Variables**](./action-scripts#clear-all-variables-fm-variable-clear_variables) จะล้างค่าตัวแปรที่จัดเก็บไว้ทั้งหมด
- ชื่อจะแยกแยะตัวพิมพ์เล็กและตัวพิมพ์ใหญ่ ควรใช้ชื่อที่เรียบง่ายและไม่ซ้ำกัน เช่น `tutorial_step`

เพลซโฮลเดอร์ [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable) จะคืนค่า `0` เมื่อไม่มีตัวแปรตามชื่อที่ระบุ หรือเมื่อค่าที่จัดเก็บไว้ว่างเปล่า ค่าทดแทนนี้มีความสำคัญในการเปรียบเทียบและนิพจน์เครื่องคิดเลข

การกระทำ [**Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable) ใช้รูปแบบ `variable_name:variable_value` และจะแยกที่โคลอนตัวแรก ดังนั้นค่าจึงสามารถมีโคลอนได้มากกว่าหนึ่งตัว

อย่าจัดเก็บรหัสผ่าน โทเค็น หรือข้อมูลลับอื่น ๆ ไว้ในตัวแปรของ FancyMenu เนื่องจากข้อมูลเหล่านี้เป็นข้อมูลการกำหนดค่าที่สามารถอ่านได้
