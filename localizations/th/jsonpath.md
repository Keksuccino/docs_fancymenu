---
title: เส้นทาง JSON
description: วิธีใช้ Jayway JsonPath ใน placeholder ตัวแยกวิเคราะห์ JSON
---

# เส้นทาง JSON ใน FancyMenu

placeholder **JSON Parser** ของ FancyMenu ใช้ [Jayway JsonPath](https://github.com/json-path/JsonPath) เพื่อดึงข้อมูลจากไฟล์ JSON
หน้านี้อธิบายเส้นทาง JSON อย่างละเอียด

ข้อความในหน้านี้เป็นสำเนาจาก README ของที่เก็บ GitHub ของ Jayway JsonPath

> ในข้อความนี้ คำว่า "JsonPath expression" หมายถึงเส้นทาง JSON
{.is-info}

# JsonPath

นิพจน์ JsonPath จะอ้างอิงโครงสร้าง JSON เสมอในลักษณะเดียวกับที่นิพจน์ XPath ใช้ร่วมกับเอกสาร XML โดย "root member object" ใน JsonPath จะถูกอ้างอิงด้วย `$` เสมอ ไม่ว่าจะเป็นอ็อบเจ็กต์หรืออาร์เรย์ก็ตาม

นิพจน์ JsonPath สามารถใช้แบบจุด (dot–notation) ได้

`$.store.book[0].title`

หรือแบบวงเล็บเหลี่ยม (bracket–notation)

`$['store']['book'][0]['title']`

## ตัวดำเนินการ

| ตัวดำเนินการ             | คำอธิบาย                                                        |
| :------------------------ | :--------------------------------------------------------------- |
| `$`                       | องค์ประกอบรากที่ใช้สำหรับ query จุดนี้เริ่มต้นนิพจน์เส้นทางทั้งหมด |
| `@`                       | โหนดปัจจุบันที่กำลังประมวลผลโดย predicate ของตัวกรอง          |
| `*`                       | ไวลด์การ์ด ใช้ได้ทุกที่ที่ต้องการชื่อหรือตัวเลข                 |
| `..`                      | การสแกนแบบลึก ใช้ได้ทุกที่ที่ต้องการชื่อ                       |
| `.<name>`                 | ลูกแบบใช้สัญลักษณ์จุด                                          |
| `['<name>' (, '<name>')]` | ลูกหรือหลายลูกแบบใช้วงเล็บเหลี่ยม                              |
| `[<number> (, <number>)]` | ดัชนีอาร์เรย์หรือหลายดัชนี                                      |
| `[start:end]`             | ตัวดำเนินการตัดช่วงอาร์เรย์                                    |
| `[?(<expression>)]`       | นิพจน์ตัวกรอง นิพจน์ต้องประเมินค่าได้เป็นบูลีน                  |


## ฟังก์ชัน

สามารถเรียกใช้ฟังก์ชันได้ที่ท้ายสุดของเส้นทาง - อินพุตของฟังก์ชันคือเอาต์พุตของนิพจน์เส้นทาง
เอาต์พุตของฟังก์ชันจะถูกกำหนดโดยตัวฟังก์ชันเอง

| ฟังก์ชัน                  | คำอธิบาย                                                         | ประเภทเอาต์พุต |
| :------------------------ | :---------------------------------------------------------------- |:----------- |
| min()                     | ให้ค่าต่ำสุดของอาร์เรย์ตัวเลข                                     | Double      |
| max()                     | ให้ค่าสูงสุดของอาร์เรย์ตัวเลข                                     | Double      |
| avg()                     | ให้ค่าเฉลี่ยของอาร์เรย์ตัวเลข                                     | Double      | 
| stddev()                  | ให้ค่าส่วนเบี่ยงเบนมาตรฐานของอาร์เรย์ตัวเลข                        | Double      | 
| length()                  | ให้ความยาวของอาร์เรย์                                             | Integer     |
| sum()                     | ให้ผลรวมของอาร์เรย์ตัวเลข                                         | Double      |
| keys()                    | ให้คีย์ของพร็อพเพอร์ตี (ทางเลือกแทน terminal tilde `~`)          | `Set<E>`    |
| concat(X)                 | ให้ผลลัพธ์ของเส้นทางที่ต่อกันพร้อมรายการใหม่                      | เหมือนอินพุต |
| append(X)                 | เพิ่มรายการลงในอาร์เรย์ผลลัพธ์ของ json path                       | เหมือนอินพุต |

## ตัวกรองโอเปอเรเตอร์

ตัวกรองคือนิพจน์เชิงตรรกะที่ใช้กรองอาร์เรย์ ตัวกรองที่พบบ่อยคือ `[?(@.age > 18)]` โดยที่ `@` แทนรายการปัจจุบันที่กำลังประมวลผล สามารถสร้างตัวกรองที่ซับซ้อนขึ้นได้ด้วยตัวดำเนินการเชิงตรรกะ `&&` และ `||` สตริงลิเทอรัลต้องอยู่ในเครื่องหมายอัญประกาศเดี่ยวหรือคู่ (`[?(@.color == 'blue')]` หรือ `[?(@.color == "blue")]`)   

| ตัวดำเนินการ            | คำอธิบาย                                                           |
| :----------------------- | :------------------------------------------------------------------ |
| ==                       | ฝั่งซ้ายเท่ากับฝั่งขวา (โปรดทราบว่า 1 ไม่เท่ากับ '1')              |
| !=                       | ฝั่งซ้ายไม่เท่ากับฝั่งขวา                                          |
| <                        | ฝั่งซ้ายน้อยกว่าฝั่งขวา                                             |
| <=                       | ฝั่งซ้ายน้อยกว่าหรือเท่ากับฝั่งขวา                                 |
| >                        | ฝั่งซ้ายมากกว่าฝั่งขวา                                              |
| >=                       | ฝั่งซ้ายมากกว่าหรือเท่ากับฝั่งขวา                                  |
| =~                       | ฝั่งซ้ายตรงกับ regular expression  [?(@.name =~ /foo.*?/i)]         |
| in                       | ฝั่งซ้ายมีอยู่ในฝั่งขวา [?(@.size in ['S', 'M'])]                  |
| nin                      | ฝั่งซ้ายไม่มีอยู่ในฝั่งขวา                                          |
| subsetof                 | ฝั่งซ้ายเป็น subset ของฝั่งขวา [?(@.sizes subsetof ['S', 'M', 'L'])] |
| anyof                    | ฝั่งซ้ายมีส่วนตัดกันกับฝั่งขวา [?(@.sizes anyof ['M', 'L'])]      |
| noneof                   | ฝั่งซ้ายไม่มีส่วนตัดกันกับฝั่งขวา [?(@.sizes noneof ['M', 'L'])]   |
| size                     | ขนาดของฝั่งซ้าย (อาร์เรย์หรือสตริง) ต้องตรงกับฝั่งขวา            |
| empty                    | ฝั่งซ้าย (อาร์เรย์หรือสตริง) ควรว่างเปล่า                          |


## ตัวอย่างเส้นทาง

กำหนดให้มี json ดังนี้

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
| <a href="http://jsonpath.herokuapp.com/?path=$.store..price" target="_blank">$.store..price</a>             | ราคาของทุกสิ่ง         |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[2]</a>                 | หนังสือลำดับที่สาม                      |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[-2]</a>                 | หนังสือลำดับรองสุดท้าย            |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[0,1]" target="_blank">$..book[0,1]</a>               | หนังสือสองเล่มแรก               |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[:2]" target="_blank">$..book[:2]</a>                | หนังสือทั้งหมดตั้งแต่ดัชนี 0 (รวม) จนถึงดัชนี 2 (ไม่รวม) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[1:2]" target="_blank">$..book[1:2]</a>                | หนังสือทั้งหมดตั้งแต่ดัชนี 1 (รวม) จนถึงดัชนี 2 (ไม่รวม) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[-2:]" target="_blank">$..book[-2:]</a>                | หนังสือสองเล่มสุดท้าย                   |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2:]" target="_blank">$..book[2:]</a>                | หนังสือลำดับที่สองนับจากท้าย          |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.isbn)]" target="_blank">$..book[?(@.isbn)]</a>          | หนังสือทั้งหมดที่มีหมายเลข ISBN         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[?(@.price < 10)]" target="_blank">$.store.book[?(@.price < 10)]</a> | หนังสือทั้งหมดในร้านที่ราคาต่ำกว่า 10  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.price <= $['expensive'])]" target="_blank">$..book[?(@.price <= $['expensive'])]</a> | หนังสือทั้งหมดในร้านที่ไม่ใช่ "expensive"  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.author =~ /.*REES/i)]" target="_blank">$..book[?(@.author =~ /.*REES/i)]</a> | หนังสือทั้งหมดที่ตรงกับ regex (ไม่สนใจตัวพิมพ์เล็ก/ใหญ่)  |
| <a href="http://jsonpath.herokuapp.com/?path=$..*" target="_blank">$..*</a>                        | แสดงทุกสิ่ง   
| <a href="http://jsonpath.herokuapp.com/?path=$..book.length()" target="_blank">$..book.length()</a>                 | จำนวนหนังสือ                      |
