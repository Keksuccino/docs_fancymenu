---
title: เส้นทาง JSON
description: วิธีใช้ Jayway JsonPath ในตัวยึดตำแหน่ง JSON Parser
excludeFromAiPlaintext: true
sourceBlobSha: 2aa2965bffefdb17d944b31190f40ec33198c1e4
---
# เส้นทาง JSON ใน FancyMenu

ตัวยึดตำแหน่ง **JSON Parser** ของ FancyMenu ใช้ [Jayway JsonPath](https://github.com/json-path/JsonPath) เพื่อดึงเนื้อหาจากไฟล์ JSON
หน้านี้อธิบายเส้นทาง JSON โดยละเอียด

ข้อความในหน้านี้คัดลอกมาจาก README ในคลัง GitHub ของ Jayway JsonPath

> [!NOTE]
> ในข้อความนี้ คำว่า "นิพจน์ JsonPath" หมายถึงเส้นทาง JSON

# JsonPath

นิพจน์ JsonPath จะอ้างอิงโครงสร้าง JSON ในลักษณะเดียวกับที่ใช้นิพจน์ XPath ร่วมกับเอกสาร XML โดย "ออบเจ็กต์สมาชิกระดับราก" ใน JsonPath จะอ้างอิงด้วย `$` เสมอ ไม่ว่าจะเป็นออบเจ็กต์หรืออาร์เรย์

นิพจน์ JsonPath สามารถใช้รูปแบบจุด

`$.store.book[0].title`

หรือรูปแบบวงเล็บ

`$['store']['book'][0]['title']`

## ตัวดำเนินการ

| ตัวดำเนินการ                  | คำอธิบาย                                                        |
| :------------------------ | :----------------------------------------------------------------- |
| `$`                       | องค์ประกอบรากที่ต้องการค้นหา ใช้เริ่มนิพจน์เส้นทางทั้งหมด       |
| `@`                       | โหนดปัจจุบันที่กำลังประมวลผลโดยเพรดิเคตตัวกรอง            |
| `*`                       | อักขระแทนค่า ใช้ได้ทุกตำแหน่งที่ต้องระบุชื่อหรือตัวเลข       |
| `..`                      | การสแกนแบบลึก ใช้ได้ทุกตำแหน่งที่ต้องระบุชื่อ                  |
| `.<name>`                 | ลูกในรูปแบบจุด                                                  |
| `['<name>' (, '<name>')]` | ลูกหรือลูกหลายรายการในรูปแบบวงเล็บ                                  |
| `[<number> (, <number>)]` | ดัชนีหรือดัชนีหลายรายการของอาร์เรย์                                             |
| `[start:end]`             | ตัวดำเนินการแบ่งส่วนอาร์เรย์                                               |
| `[?(<expression>)]`       | นิพจน์ตัวกรอง นิพจน์ต้องประเมินผลเป็นค่าบูลีน    |


## ฟังก์ชัน

สามารถเรียกใช้ฟังก์ชันที่ส่วนท้ายของเส้นทางได้ โดยอินพุตของฟังก์ชันคือผลลัพธ์ของนิพจน์เส้นทาง
ประเภทผลลัพธ์ของฟังก์ชันจะขึ้นอยู่กับตัวฟังก์ชันเอง

| ฟังก์ชัน                  | คำอธิบาย                                                         | ประเภทผลลัพธ์ |
| :------------------------ | :------------------------------------------------------------------ |:----------- |
| min()                     | ส่งคืนค่าต่ำสุดของอาร์เรย์ตัวเลข                       | Double      |
| max()                     | ส่งคืนค่าสูงสุดของอาร์เรย์ตัวเลข                       | Double      |
| avg()                     | ส่งคืนค่าเฉลี่ยของอาร์เรย์ตัวเลข                   | Double      | 
| stddev()                  | ส่งคืนค่าส่วนเบี่ยงเบนมาตรฐานของอาร์เรย์ตัวเลข        | Double      | 
| length()                  | ส่งคืนความยาวของอาร์เรย์                                     | Integer     |
| sum()                     | ส่งคืนผลรวมของอาร์เรย์ตัวเลข                       | Double      |
| keys()                    | ส่งคืนคีย์คุณสมบัติ (เป็นทางเลือกแทนเครื่องหมายทิลด์ `~` ที่ส่วนท้าย)  | `Set<E>`    |
| concat(X)                 | ส่งคืนผลลัพธ์ของเส้นทางที่ต่อเข้ากับรายการใหม่  | เหมือนอินพุต  |
| append(X)                 | เพิ่มรายการลงในอาร์เรย์ผลลัพธ์ของเส้นทาง JSON                           | เหมือนอินพุต  |

## ตัวดำเนินการตัวกรอง

ตัวกรองคือนิพจน์ตรรกะที่ใช้กรองอาร์เรย์ ตัวกรองทั่วไปอาจเป็น `[?(@.age > 18)]` โดย `@` หมายถึงรายการปัจจุบันที่กำลังประมวลผล คุณสามารถสร้างตัวกรองที่ซับซ้อนขึ้นได้ด้วยตัวดำเนินการตรรกะ `&&` และ `||` ค่าข้อความต้องอยู่ภายในเครื่องหมายอัญประกาศเดี่ยวหรือคู่ (`[?(@.color == 'blue')]` หรือ `[?(@.color == "blue")]`)   

| ตัวดำเนินการ                 | คำอธิบาย                                                           |
| :----------------------- | :-------------------------------------------------------------------- |
| ==                       | ด้านซ้ายเท่ากับด้านขวา (โปรดทราบว่า 1 ไม่เท่ากับ '1')              |
| !=                       | ด้านซ้ายไม่เท่ากับด้านขวา                                            |
| <                        | ด้านซ้ายน้อยกว่าด้านขวา                                               |
| <=                       | ด้านซ้ายน้อยกว่าหรือเท่ากับด้านขวา                                        |
| >                        | ด้านซ้ายมากกว่าด้านขวา                                            |
| >=                       | ด้านซ้ายมากกว่าหรือเท่ากับด้านขวา                                |
| =~                       | ด้านซ้ายตรงกับนิพจน์ทั่วไป  [?(@.name =~ /foo.*?/i)]             |
| in                       | ด้านซ้ายมีอยู่ในด้านขวา [?(@.size in ['S', 'M'])]                        |
| nin                      | ด้านซ้ายไม่มีอยู่ในด้านขวา                                         |
| subsetof                 | ด้านซ้ายเป็นสับเซตของด้านขวา [?(@.sizes subsetof ['S', 'M', 'L'])]       |
| anyof                    | ด้านซ้ายมีส่วนตัดกับด้านขวา [?(@.sizes anyof ['M', 'L'])]     |
| noneof                   | ด้านซ้ายไม่มีส่วนตัดกับด้านขวา [?(@.sizes noneof ['M', 'L'])]    |
| size                     | ขนาดของด้านซ้าย (อาร์เรย์หรือสตริง) ต้องตรงกับด้านขวา                     |
| empty                    | ด้านซ้าย (อาร์เรย์หรือสตริง) ต้องว่างเปล่า                                |


## ตัวอย่างเส้นทาง

กำหนดให้ JSON เป็นดังนี้

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
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[*].author" target="_blank">$.store.book[*].author</a>| ผู้เขียนหนังสือทั้งหมด     |
| <a href="http://jsonpath.herokuapp.com/?path=$..author" target="_blank">$..author</a>                   | ผู้เขียนทั้งหมด                         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.*" target="_blank">$.store.*</a>                  | สิ่งของทั้งหมด ทั้งหนังสือและจักรยาน  |
| <a href="http://jsonpath.herokuapp.com/?path=$.store..price" target="_blank">$.store..price</a>             | ราคาของทุกสิ่ง         |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[2]</a>                 | หนังสือเล่มที่สาม                      |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[-2]</a>                 | หนังสือเล่มรองสุดท้าย            |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[0,1]" target="_blank">$..book[0,1]</a>               | หนังสือสองเล่มแรก               |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[:2]" target="_blank">$..book[:2]</a>                | หนังสือทั้งหมดตั้งแต่ดัชนี 0 (รวมดัชนีนี้) จนถึงดัชนี 2 (ไม่รวมดัชนีนี้) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[1:2]" target="_blank">$..book[1:2]</a>                | หนังสือทั้งหมดตั้งแต่ดัชนี 1 (รวมดัชนีนี้) จนถึงดัชนี 2 (ไม่รวมดัชนีนี้) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[-2:]" target="_blank">$..book[-2:]</a>                | หนังสือสองเล่มสุดท้าย                   |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2:]" target="_blank">$..book[2:]</a>                | หนังสือเล่มที่สองนับจากท้าย          |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.isbn)]" target="_blank">$..book[?(@.isbn)]</a>          | หนังสือทั้งหมดที่มีหมายเลข ISBN         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[?(@.price < 10)]" target="_blank">$.store.book[?(@.price < 10)]</a> | หนังสือทั้งหมดในร้านที่ราคาต่ำกว่า 10  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.price <= $['expensive'])]" target="_blank">$..book[?(@.price <= $['expensive'])]</a> | หนังสือทั้งหมดในร้านที่ไม่ "แพง"  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.author =~ /.*REES/i)]" target="_blank">$..book[?(@.author =~ /.*REES/i)]</a> | หนังสือทั้งหมดที่ตรงกับนิพจน์ทั่วไป (ไม่สนใจตัวพิมพ์เล็ก-ใหญ่)  |
| <a href="http://jsonpath.herokuapp.com/?path=$..*" target="_blank">$..*</a>                        | แสดงทุกสิ่ง   
| <a href="http://jsonpath.herokuapp.com/?path=$..book.length()" target="_blank">$..book.length()</a>                 | จำนวนหนังสือ                      |
