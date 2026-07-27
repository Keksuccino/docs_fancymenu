---
title: การสื่อสารกับเซิร์ฟเวอร์ระยะไกล
description: >-
  ส่งและรับข้อมูลข้อความแบบกำหนดเองระหว่างไคลเอนต์ FancyMenu
  และเซิร์ฟเวอร์ภายนอก
---

# การสื่อสารกับเซิร์ฟเวอร์ระยะไกล

ระบบ "การสื่อสารกับเซิร์ฟเวอร์ระยะไกล" ช่วยให้ไคลเอนต์ FancyMenu สามารถสื่อสารกับเซิร์ฟเวอร์ภายนอกผ่านการเชื่อมต่อ WebSocket ได้

ข้อมูลทั้งหมดเป็นแบบข้อความ:

- รองรับข้อความธรรมดา
- รองรับ JSON (ในรูปแบบข้อความปกติ)

URL ของแต่ละเซิร์ฟเวอร์จะได้รับ **request ID** ที่แคชไว้หนึ่งค่าในระหว่างรันไทม์
FancyMenu ใช้ ID นี้เพื่อติดตามการเชื่อมต่อและเปิดเผยในตัวแปรของ listener

# เริ่มต้นอย่างรวดเร็ว

1. เพิ่ม [**Connect To Remote Server**](#connect-to-remote-server) เมื่อควรเปิดการเชื่อมต่อให้เร็วขึ้น
2. เพิ่ม [**Send Data To Remote Server**](#send-data-to-remote-server) โดยใช้ URL เดียวกัน
3. เพิ่ม [**On Remote Server Data Received**](#on-remote-server-data-received) เพื่อโต้ตอบกับการตอบกลับ
4. ใช้ [**On Remote Server Connected**](#on-remote-server-connected) และ [**On Remote Server Connection Closed**](#on-remote-server-connection-closed) สำหรับตรรกะเกี่ยวกับสถานะการเชื่อมต่อ
5. ปิดการเชื่อมต่อด้วย [**Close Remote Server Connection**](#close-remote-server-connection) หรือ [**Close All Remote Server Connections**](#close-all-remote-server-connections)

# การดำเนินการ

## Connect To Remote Server

เปิดการเชื่อมต่อกับเซิร์ฟเวอร์ระยะไกล หรือใช้การเชื่อมต่อเดิมที่มีอยู่ซ้ำ โดยไม่ส่งข้อมูล payload

อินพุต:

- Remote Server URL

## Send Data To Remote Server

เชื่อมต่อ (หรือใช้การเชื่อมต่อที่มีอยู่เดิมซ้ำ) และส่งข้อมูลข้อความ

อินพุต:

1. Remote Server URL
2. Data

## Close Remote Server Connection

ปิดการเชื่อมต่อหนึ่งรายการตาม request ID

อินพุต:

- Connection Request ID

## Close All Remote Server Connections

ปิดการเชื่อมต่อกับเซิร์ฟเวอร์ระยะไกลที่กำลังใช้งานอยู่ทั้งหมด

# ตัวฟังเหตุการณ์

## On Remote Server Connected

ทำงานหลังจากการเชื่อมต่อกับเซิร์ฟเวอร์ระยะไกลเปิดสำเร็จ

ตัวแปร:

- `$$request_id`
- `$$remote_server_url`

## On Remote Server Data Received

ทำงานเมื่อได้รับข้อมูลจากเซิร์ฟเวอร์ระยะไกลที่เชื่อมต่ออยู่

ตัวแปร:

- `$$request_id`
- `$$remote_server_url`
- `$$data`

## On Remote Server Connection Closed

ทำงานเมื่อการเชื่อมต่อกับเซิร์ฟเวอร์ระยะไกลถูกปิด

ตัวแปร:

- `$$request_id`
- `$$remote_server_url`
- `$$intentionally_closed`
- `$$crashed`
- `$$unknown_close_reason`

# พฤติกรรมของการเชื่อมต่อ

- การเชื่อมต่อเป็นแบบ **เริ่มต้นโดยไคลเอนต์**
- FancyMenu จะรักษาการเชื่อมต่อให้ทำงานอยู่เบื้องหลัง
- หากการเชื่อมต่อล่มหรือหมดเวลา FancyMenu จะลองใหม่ทุก 10 วินาที
- เมื่อการเชื่อมต่อที่ล่มกลับมาใช้งานได้ FancyMenu จะบันทึกข้อความการกู้คืน
- ข้อความขาออกที่ยังไม่ส่งจะถูกจัดคิวไว้ โดยมี **อายุสูงสุด 30 วินาที**
- ข้อความในคิวที่เก่ากว่า 30 วินาทีจะถูกทิ้ง

# โหมด URL

- `wss://` จะถูกใช้ตามที่เขียนไว้ และเป็นตัวเลือกที่แนะนำ
- `ws://` จะถูกใช้ตามที่เขียนไว้ และไม่มีการเข้ารหัส
- `https://` จะถูกแปลงเป็น `wss://`
- `http://` จะถูกแปลงเป็น `ws://`
- โฮสต์ที่ระบุเพียงชื่อจะถูกเติมนำหน้าด้วย `wss://`
- สกีม URL อื่น ๆ ที่ระบุชัดเจนจะถูกปฏิเสธ

ควรใช้ URL `wss://` ที่ระบุชัดเจน ตัวอย่าง URL ภายในเครื่อง:

- `ws://127.0.0.1:8765`

ใช้ URL ที่คงที่เพียงหนึ่งรายการต่อหนึ่งบริการ จัดการสถานะ listener ที่ปิด/ล่ม และปิดการเชื่อมต่อเมื่อไม่จำเป็นแล้ว
