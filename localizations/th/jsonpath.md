---
title: เส้นทาง JSON
description: วิธีใช้ Jayway JsonPath ในตัวแทนที่ JSON Parser
---

# JSON Paths ใน FancyMenu

ตัวแทนที่ **JSON Parser** ของ FancyMenu ใช้ [Jayway JsonPath](https://github.com/json-path/JsonPath) เพื่อดึงเนื้อหาจากไฟล์ JSON
หน้านี้อธิบาย JSON paths อย่างละเอียด

ข้อความในหน้านี้เป็นสำเนามาจาก README ในที่เก็บ GitHub ของ Jayway JsonPath

> [!NOTE]
> ในข้อความนี้ คำว่า "JsonPath expression" หมายถึง JSON path

# JsonPath

นิพจน์ JsonPath จะอ้างอิงโครงสร้าง JSON เสมอ ในลักษณะเดียวกับที่นิพจน์ XPath ใช้ร่วมกับเอกสาร XML
"อ็อบเจ็กต์สมาชิกหลัก (root member object)" ใน JsonPath จะอ้างอิงด้วย `$` เสมอ ไม่ว่าจะเป็นอ็อบเจ็กต์หรืออาร์เรย์ก็ตาม

นิพจน์ JsonPath สามารถใช้รูปแบบ dot–notation ได้

`$.store.book[0].title`

หรือ bracket–notation

`$['store']['book'][0]['title']`

## ตัวดำเนินการ

| ตัวดำเนินการ              | คำอธิบาย                                                       |
| :------------------------ | :-------------------------------------------------------------- |
| `$`                       | องค์ประกอบรากที่ใช้สืบค้น ใช้เริ่มต้นนิพจน์เส้นทางทั้งหมด      |
| `@`                       | โหนดปัจจุบันที่กำลังประมวลผลโดยพรีดิเคตของตัวกรอง             |
| `*`                       | ไวลด์การ์ด ใช้ได้ทุกที่ที่ต้องระบุชื่อหรือตัวเลข                |
| `..`                      | การสแกนแบบลึก ใช้ได้ทุกที่ที่ต้องระบุชื่อ                      |
| `.<name>`                 | ลูกแบบใช้ dot notation                                          |
| `['<name>' (, '<name>')]` | ลูกหรือหลายลูกแบบใช้ bracket notation                          |
| `[<number> (, <number>)]` | ดัชนีอาร์เรย์หนึ่งค่าหรือหลายค่า                                |
| `[start:end]`             | ตัวดำเนินการแบ่งช่วงอาร์เรย์                                   |
| `[?(<expression>)]`       | นิพจน์ตัวกรอง นิพจน์ต้องประเมินผลเป็นค่าบูลีน                 |


## ฟังก์ชัน

สามารถเรียกใช้ฟังก์ชันได้ที่ท้ายสุดของเส้นทาง - อินพุตของฟังก์ชันคือผลลัพธ์ของนิพจน์เส้นทาง
ผลลัพธ์ของฟังก์ชันจะถูกกำหนดโดยตัวฟังก์ชันเอง

| ฟังก์ชัน                  | คำอธิบาย                                                         | ประเภทผลลัพธ์ |
| :------------------------ | :---------------------------------------------------------------- |:----------- |
| min()                     | ให้ค่าต่ำสุดของอาร์เรย์ตัวเลข                                    | Double      |
| max()                     | ให้ค่าสูงสุดของอาร์เรย์ตัวเลข                                    | Double      |
| avg()                     | ให้ค่าเฉลี่ยของอาร์เรย์ตัวเลข                                     | Double      | 
| stddev()                  | ให้ค่าส่วนเบี่ยงเบนมาตรฐานของอาร์เรย์ตัวเลข                       | Double      | 
| length()                  | ให้ความยาวของอาร์เรย์                                            | Integer     |
| sum()                     | ให้ผลรวมของอาร์เรย์ตัวเลข                                         | Double      |
| keys()                    | ให้คีย์ของพร็อพเพอร์ตี (ทางเลือกแทน terminal tilde `~`)          | `Set<E>`    |
| concat(X)                 | ให้ผลลัพธ์ของเส้นทางที่ต่อเข้ากับรายการใหม่                       | เหมือนอินพุต |
| append(X)                 | เพิ่มรายการลงในอาร์เรย์ผลลัพธ์ของ json path                     | เหมือนอินพุต |

## ตัวดำเนินการตัวกรอง

ตัวกรองคือ expression เชิงตรรกะที่ใช้กรองอาร์เรย์ ตัวกรองทั่วไปจะเป็น `[?(@.age > 18)]` โดยที่ `@` แทนรายการปัจจุบันที่กำลังประมวลผล
สามารถสร้างตัวกรองที่ซับซ้อนขึ้นได้ด้วยตัวดำเนินการเชิงตรรกะ `&&` และ `||` สตริงลิเทอรัลต้องอยู่ในเครื่องหมายอัญประกาศเดี่ยวหรือคู่ (`[?(@.color == 'blue')]` หรือ `[?(@.color == "blue")]`)   

| ตัวดำเนินการ             | คำอธิบาย                                                           |
| :----------------------- | :------------------------------------------------------------------ |
| ==                       | ค่าด้านซ้ายเท่ากับค่าด้านขวา (สังเกตว่า 1 ไม่เท่ากับ '1')         |
| !=                       | ค่าด้านซ้ายไม่เท่ากับค่าด้านขวา                                   |
| <                        | ค่าด้านซ้ายน้อยกว่าค่าด้านขวา                                      |
| <=                       | ค่าด้านซ้ายน้อยกว่าหรือเท่ากับค่าด้านขวา                           |
| >                        | ค่าด้านซ้ายมากกว่าค่าด้านขวา                                       |
| >=                       | ค่าด้านซ้ายมากกว่าหรือเท่ากับค่าด้านขวา                           |
| =~                       | ค่าด้านซ้ายตรงกับนิพจน์ปกติ  [?(@.name =~ /foo.*?/i)]             |
| in                       | ค่าด้านซ้ายมีอยู่ในค่าด้านขวา [?(@.size in ['S', 'M'])]           |
| nin                      | ค่าด้านซ้ายไม่มีอยู่ในค่าด้านขวา                                   |
| subsetof                 | ค่าด้านซ้ายเป็นสับเซตของค่าด้านขวา [?(@.sizes subsetof ['S', 'M', 'L'])] |
| anyof                    | ค่าด้านซ้ายมีส่วนตัดกันกับค่าด้านขวา [?(@.sizes anyof ['M', 'L'])]    |
| noneof                   | ค่าด้านซ้ายไม่มีส่วนตัดกันกับค่าด้านขวา [?(@.sizes noneof ['M', 'L'])] |
| size                     | ขนาดของค่าด้านซ้าย (อาร์เรย์หรือสตริง) ควรตรงกับค่าด้านขวา      |
| empty                    | ค่าด้านซ้าย (อาร์เรย์หรือสตริง) ควรว่างเปล่า                      |


## ตัวอย่างเส้นทาง

เมื่อกำหนด JSON นี้

```javascript
{
    "store": {
        "book": [
            {
                "category": "reference",
                "author": "Nigel Rees",
                "title": "Sayings of the Century",
                "price": 8.95
            },
            {
                "category": "fiction",
                "author": "Evelyn Waugh",
                "title": "Sword of Honour",
                "price": 12.99
            },
            {
                "category": "fiction",
                "author": "Herman Melville",
                "title": "Moby Dick",
                "isbn": "0-553-21311-3",
                "price": 8.99
            },
            {
                "category": "fiction",
                "author": "J. R. R. Tolkien",
                "title": "The Lord of the Rings",
                "isbn": "0-395-19395-8",
                "price": 22.99
            }
        ],
        "bicycle": {
            "color": "red",
            "price": 19.95
        }
    },
    "expensive": 10
}
```

| JsonPath (คลิกลิงก์เพื่อทดลอง)| ผลลัพธ์ |
| :------- | :----- |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[*].author" target="_blank">$.store.book[*].author</a>| ผู้เขียนของหนังสือทั้งหมด     |
| <a href="http://jsonpath.herokuapp.com/?path=$..author" target="_blank">$..author</a>                   | ผู้เขียนทั้งหมด                         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.*" target="_blank">$.store.*</a>                  | ทุกอย่าง ทั้งหนังสือและจักรยาน  |
| <a href="http://jsonpath.herokuapp.com/?path=$.store..price" target="_blank">$.store..price</a>             | ราคาของทุกอย่าง         |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[2]</a>                 | หนังสือเล่มที่สาม                      |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[-2]</a>                 | หนังสือเล่มรองสุดท้าย            |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[0,1]" target="_blank">$..book[0,1]</a>               | หนังสือสองเล่มแรก               |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[:2]" target="_blank">$..book[:2]</a>                | หนังสือทั้งหมดตั้งแต่ดัชนี 0 (รวม) จนถึงดัชนี 2 (ไม่รวม) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[1:2]" target="_blank">$..book[1:2]</a>                | หนังสือทั้งหมดตั้งแต่ดัชนี 1 (รวม) จนถึงดัชนี 2 (ไม่รวม) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[-2:]" target="_blank">$..book[-2:]</a>                | สองเล่มสุดท้าย                   |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2:]" target="_blank">$..book[2:]</a>                | หนังสือจากท้ายลำดับที่สอง          |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.isbn)]" target="_blank">$..book[?(@.isbn)]</a>          | หนังสือทั้งหมดที่มีหมายเลข ISBN         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[?(@.price < 10)]" target="_blank">$.store.book[?(@.price < 10)]</a> | หนังสือทั้งหมดในร้านที่ราคาต่ำกว่า 10  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.price <= $['expensive'])]" target="_blank">$..book[?(@.price <= $['expensive'])]</a> | หนังสือทั้งหมดในร้านที่ไม่ "แพง"  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.author =~ /.*REES/i)]" target="_blank">$..book[?(@.author =~ /.*REES/i)]</a> | หนังสือทั้งหมดที่ตรงกับ regex (ไม่สนตัวพิมพ์เล็ก/ใหญ่)  |
| <a href="http://jsonpath.herokuapp.com/?path=$..*" target="_blank">$..*</a>                        | แสดงทุกอย่าง   
| <a href="http://jsonpath.herokuapp.com/?path=$..book.length()" target="_blank">$..book.length()</a>                 | จำนวนหนังสือ                      |
