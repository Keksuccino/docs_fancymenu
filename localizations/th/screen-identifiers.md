---
title: ตัวระบุหน้าจอ
description: เกี่ยวกับตัวระบุหน้าจอและวิธีค้นหาตัวระบุของหน้าจอ
---
# ตัวระบุหน้าจอ

FancyMenu ใช้ตัวระบุหน้าจอสำหรับเลย์เอาต์ วิดเจ็ตแบบ Vanilla [การทำงานของหน้าจอ](./action-scripts#open-screen-or-custom-gui-opengui) และ [การแทนที่ Custom GUI](./custom-guis#overriding-an-existing-screen) โดยตัวระบุจะคำนึงถึงตัวพิมพ์เล็ก-ใหญ่ ดังนั้นให้คัดลอกให้ตรงจาก debug overlay

โดยปกติหน้าจอที่มาพร้อมกับเกมจะใช้ตัวระบุสากลแบบสั้น เช่น `title_screen` ส่วนหน้าจอของม็อดอื่นอาจใช้ชื่อคลาส Java ของมัน Custom GUI จะใช้ตัวระบุที่ป้อนในตัวจัดการของมัน นี่คือตัวระบุหน้าจอของ FancyMenu ไม่ใช่ตำแหน่งทรัพยากรของ Minecraft

# การค้นหาตัวระบุของหน้าจอ

คุณสามารถดูตัวระบุของเมนูที่กำลังใช้งานอยู่ได้โดยใช้ **debug overlay**
มันจะแสดงตัวระบุของหน้าจอปัจจุบัน และให้คุณคัดลอกไปยังคลิปบอร์ดได้โดยคลิกซ้ายที่มัน

>[!TIP]
>คุณสามารถเปิดใช้งาน **debug overlay** ได้โดยกด **CTRL + ALT + D** ขณะที่คุณ **ไม่ได้** อยู่ในตัวแก้ไขเลย์เอาต์

<br>

<img width="553" alt="Screenshot_3" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/1800351e-f042-4826-8eed-7725b78bc84d">

<br>

<img width="579" alt="Screenshot_4" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/9e0d1e61-7f2d-4817-9be1-b63ee61978dd">

# การเปิดหน้าจอ

[**การทำงาน Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui) สามารถเปิดได้เฉพาะหน้าจอที่ FancyMenu สามารถสร้างได้ในสถานะเกมปัจจุบันเท่านั้น หน้าจอบางประเภทต้องมีโลกที่โหลดแล้ว การเชื่อมต่อ ผู้เล่น หรือหน้าจอแม่ต้นฉบับ

หาก FancyMenu ไม่สามารถสร้างจากตัวระบุได้ จะแสดงข้อผิดพลาด ให้ใช้ [**Mimic Vanilla/Mod Button**](./action-scripts#mimic-vanillamod-button-mimicbutton) กับวิดเจ็ตที่ปกติใช้เปิดหน้าจอนั้น
