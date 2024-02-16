# JOIN

### LEFT JOIN
LEFT JOIN เป็นการ JOIN TABLE แบบ เอา TABLE ซ้าย หรือ TABLE แรก เป็นหลัก ถ้าซ้ายมี เอาซ้ายออกมาให้หมด
ถ้าขวามี และซ้ายก็มีด้วย ก็จะเอาออกมา
ถ้าขวาดันไม่มี แต่ซ้ายมี พวกฟิลด์ต่าง ๆ ที่อยู่ใน TABLE ขวาจะ NULL

![leftjion](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*8CR8r4MIoq33ScZ6do5fSg.png)

```sql
SELECT tbl1.col1, tbl2.col2...
FROM tbl1
LEFT JOIN tbl2
ON tbl1.field_name = tbl2.field_name;
```

### RIGHT JOIN

RIGHT JOIN เป็นการ JOIN TABLE เหมือน LEFT JOIN ทุกประการแต่… แทนที่จะเอาข้อมูลด้านซ้าย ให้มาเอาด้านขวาแทน…
ถ้าขวามี เอาขวาออกมาให้หมด
ถ้าขวามี และซ้ายก็มีด้วย ก็จะเอาออกมา
ถ้าซ้ายดันไม่มี แต่ขวามี พวกฟิลด์ต่าง ๆ ที่อยู่ใน TABLE ซ้ายจะ NULL

![rightjoin](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*XdnZ2RsSDzgdqgRQ_dlwog.png)

```sql
SELECT tbl1.col1, tbl2.col2...
FROM tbl1
RIGHT JOIN tbl2
ON tbl1.field_name = tbl2.field_name;
```

### INNER JOIN
INNER JOIN การทำ Inner join นั้นเป็นการเอาข้อมูลของทั้งสองตารางมา join กัน แต่ว่า จะเอาเฉพาะที่เงือนไขของทั้งสองตารางมีเหมือนกันเท่านั้น

![inner join](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*dLqTQUk7TnVXGdBqWjeAOQ.png)

```sql
SELECT tbl1.col1, tbl2.col2...
FROM tbl1
INNER JOIN tbl2
ON tbl1.field_name = tbl2.field_name;
```

### FULL OUTER JOIN

FULL OUTER JOIN เป็นการ JOIN แบบไม่สนใจโลก ไม่สนใจว่าจะ ตารางซ้าย ตารางขวาคือเอาหมด ขอแค่มันตรงเงื่อนไขที่ระบุไว้ก็พอ
ซ้ายมีก็แสดง
ขวามีก็แสดง
ซ้ายมีขวาไม่มีก็แสดง ส่วนด้านขวาที่ไม่มีจะออกเป็น null
ขวามีซ้ายไม่มีก็แสดง ส่วนด้านซ้ายที่ไม่มีจะออกเป็น null

![fullouterjoin](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*8dGpguA0nozycblBAhaEpw.png)

```sql
SELECT *
FROM tbl1
FULL OUTER JOIN tbl2
ON tbl1.field_name = tbl2.field_name;
```


[ที่มา](https://iamgique.medium.com/%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%83%E0%B8%8A%E0%B9%89-join-%E0%B9%83%E0%B8%99-sql-%E0%B9%81%E0%B8%9A%E0%B8%9A%E0%B8%AD%E0%B9%8B%E0%B8%AD%E0%B8%87%E0%B8%B5%E0%B9%89%E0%B8%99%E0%B8%B5%E0%B9%88%E0%B9%80%E0%B8%AD%E0%B8%87-479ce75f33b1)
