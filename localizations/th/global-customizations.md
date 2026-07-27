---
title: การปรับแต่งแบบทั่วทั้งเกม
description: ใช้การปรับแต่ง FancyMenu แบบ глобัลที่มีผลกับทุกหน้าจอ
---

# การปรับแต่งแบบทั่วทั้งเกม

การปรับแต่งแบบทั่วทั้งเกมจะใช้การตั้งค่า UI และการเริ่มต้นร่วมกัน โดยไม่ต้องแก้ไขเลย์เอาต์ของแต่ละหน้าจอแยกกัน และยังใช้งานได้แม้จะปิดการปรับแต่งหน้าจอแบบปกติอยู่ก็ตาม

ตัวอย่างที่พบบ่อย:

- ใช้สไตล์ปุ่มและสไลเดอร์แบบเดียวร่วมกันสำหรับทุกหน้าจอ
- เปลี่ยนพื้นหลังเมนู, พาโนรามา และเพลงเมนูแบบทั่วทั้งเกม
- ใช้พฤติกรรมการเริ่มต้น/หน้าต่างแบบทั่วทั้งเกม (GUI scale, fullscreen, ชื่อ/ไอคอนหน้าต่าง)
- เปลี่ยนพื้นผิวปุ่มแบบวานิลลาทั่วทั้งเกมโดยไม่ต้องใช้ resource pack
- เปลี่ยนเพลงเมนูแบบวานิลลาทั่วทั้งเกมโดยไม่ต้องใช้ resource pack

# หาได้จากที่ไหน

เปิด **menu bar** ของ FancyMenu ขณะ **ไม่ได้อยู่** ในตัวแก้ไขเลย์เอาต์ จากนั้นเลือก **Customization -> Global Customizations**

# สิ่งที่คุณปรับแต่งได้

## พฤติกรรมแบบทั่วทั้งเกมและการเริ่มต้น

- [**Game Intro**](./game-intro) (วิดีโอหรือแอนิเมชันเปิดที่เล่นก่อนหน้า Title screen)
- **Singleplayer Screen World Icons**
- **Multiplayer Screen Server Icons**
- [**Seamless World Loading**](./seamless-world-loading) (ใช้ภาพหน้าจอของโลกที่เพิ่งเล่นล่าสุดเป็นพื้นหลังของหน้าจอโหลด)
- [**Custom Window Icon**](./window-customization#custom-icon)
- [**Custom Window Title**](./window-customization#custom-title)
- **Default GUI Scale**
- **Force Fullscreen on Launch**

## รูปลักษณ์ของปุ่ม

- **Custom Button Textures** (สถานะ Normal/Hover/Inactive, โหมดโปร่งใส, [nine-slice](./nine-slicing-and-tiling) + ขนาดขอบ)
- **Button Labels** (ขีดเส้นใต้เมื่อชี้เมาส์, สีพื้นฐาน/สีเมื่อชี้, สเกล, เงา)

## รูปลักษณ์ของสไลเดอร์

- **Custom Slider Textures**
- **Slider Background Texture** (พื้นผิว, โหมดโปร่งใส, [nine-slice](./nine-slicing-and-tiling) + ขนาดขอบ)
- **Slider Handle Textures** (สถานะ Normal/Hover/Inactive, [nine-slice](./nine-slicing-and-tiling) + ขนาดขอบ)
- **Slider Labels** (ขีดเส้นใต้เมื่อชี้เมาส์, สีพื้นฐาน/สีเมื่อชี้, สเกล, เงา)

## รูปลักษณ์และเสียงของเมนู

- [**Custom Menu Background Texture**](./menu-backgrounds)
- [**Custom Menu Background Panorama**](./panoramas)
- **Play Vanilla Menu Music** (เปิด/ปิดการเล่นเพลงเมนูแบบวานิลลา)
- [**Custom Menu Music Tracks**](./background-music)
- **Custom Button/Slider Click Sound**

# Custom Menu Music Tracks

ใช้ **Custom Menu Music Tracks** เพื่อสร้างรายการเพลงแบบสุ่มสำหรับเมนู

> [!IMPORTANT]
> แทร็กเมนูแบบกำหนดเองส่วนกลางจะเล่นเฉพาะเมื่อไม่มีโลกถูกโหลดอยู่ เช่น ใน Title screen ใช้องค์ประกอบ [**Audio**](./elements#audio) สำหรับเสียงเมนูขณะอยู่ในโลก

แทร็กที่ตั้งค่าไว้จะใช้ช่องเสียง Music และแทนที่เพลงเมนูแบบวานิลลาในเมนูที่รองรับซึ่งไม่ใช่เมนูในโลก

- แทร็กแรกจะเริ่มหลังจากประมาณห้าวินาที
- แทร็กถัด ๆ ไปจะเริ่มหลังจากหน่วงแบบสุ่มประมาณ 1 ถึง 30 วินาที
- เลือกแทร็กแบบสุ่ม
- หากมีหลายแทร็ก แทร็กก่อนหน้าจะไม่ถูกเลือกซ้ำติดต่อกันสองครั้ง

จัดการรายการแทร็กได้จาก **Custom Menu Music Tracks**:

- เปิด **Custom Menu Music Tracks** เพื่อเปิด **Manage Menu Music Tracks**
- ใช้ **Add Track** เพื่อเพิ่มแหล่งเสียง
- ใช้ **Remove Track** เพื่อลบหนึ่งรายการ
- ใช้ **Clear Tracks** เพื่อลบทั้งหมด
