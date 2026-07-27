---
title: การกำหนดตำแหน่งและขนาดขั้นสูง
description: วิธีใช้การกำหนดตำแหน่งและขนาดขั้นสูงขององค์ประกอบ
---
# การกำหนดตำแหน่งและขนาดขั้นสูง

การกำหนดตำแหน่งและขนาดขั้นสูงช่วยให้คุณควบคุมพิกัดและขนาดขององค์ประกอบได้โดยตรง

> [!WARNING]
> สำหรับการปรับให้เหมาะกับขนาด GUI ให้ลองใช้ **Auto-Scaling** ระดับเลย์เอาต์ก่อน คลิกขวาพื้นหลังของตัวแก้ไข บังคับขนาด GUI แล้วเปิด **Auto-Scaling** ในเมนูเดียวกัน


# การสลับโหมดการกำหนดตำแหน่ง/ขนาดขั้นสูง

หากต้องการเปิดการกำหนดตำแหน่งหรือขนาดขั้นสูงให้กับองค์ประกอบ ให้ **คลิกขวา** ที่องค์ประกอบนั้นแล้วเลือก **Advanced Positioning** หรือ **Advanced Sizing**
องค์ประกอบจะสลับไปยังโหมดขั้นสูงโดยอัตโนมัติเมื่อคุณตั้งค่าตำแหน่งหรือขนาดแบบขั้นสูง

หากต้องการ **ปิดใช้งาน** และกลับไปใช้การกำหนดตำแหน่ง/ขนาดแบบปกติ ให้ **ล้างค่าการกำหนดตำแหน่ง/ขนาดทั้งหมด**

> [!WARNING]
> ในขณะที่องค์ประกอบอยู่ในโหมด Advanced Sizing/Positioning การปรับขนาดและ/หรือการย้ายองค์ประกอบอาจถูกปิดใช้งานหรือถูกจำกัด

# การคำนวณตำแหน่ง/ขนาด

ค่าตำแหน่งและขนาดขั้นสูงรองรับ [placeholders](./placeholders)

ซึ่งช่วยให้คุณผสาน placeholder [**Calculator**](./placeholders#calculator-calc) เข้ากับ placeholder ของ GUI เช่น [**Screen Width**](./placeholders#screen-width-guiwidth), [**GUI Scale**](./placeholders#gui-scale-guiscale) และ [**Element Width**](./placeholders#element-width-elementwidth) ได้

> [!NOTE]
> คุณสามารถเพิ่ม placeholders ได้โดยคลิกปุ่ม **Placeholders** ที่มุมขวาบนของตัวแก้ไขข้อความ หากคุณไม่เห็นปุ่มนี้ แสดงว่าเนื้อหาที่คุณต้องการแก้ไข **ไม่รองรับ** placeholders

หากต้องการคำนวณบางอย่างด้วย [**Calculator placeholder**](./placeholders#calculator-calc) ให้แทนที่ตัวอย่างนิพจน์ด้วยค่าของคุณเอง placeholders ที่ซ้อนกันสามารถส่งขนาดของหน้าจอหรือองค์ประกอบได้

ตัวอย่างนี้ส่งคืนค่า `2`:

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

ตั้งค่า `decimal` เป็น `false` สำหรับการคำนวณตำแหน่งและขนาดที่เป็นจำนวนเต็มพิกเซล

ตัวอย่างตัวคำนวณต่อไปนี้ใช้ [**Screen Width placeholder**](./placeholders#screen-width-guiwidth) และหารด้วย `2`:

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`

> [!IMPORTANT]
> **Advanced Positioning** จะไม่สนใจจุดยึดขององค์ประกอบ และใช้มุมซ้ายบนของหน้าจอ (`X0 Y0`) เป็นจุดกำเนิดแทน **Stay on Screen** ยังคงมีผลอยู่
