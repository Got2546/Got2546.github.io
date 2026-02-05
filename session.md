**[⬅ ย้อนกลับ](https://got2546.github.io/)**

# --- ___ปัญหาที่ตรวจพบจาก RIPS___ ---
![This is an alt text.](/img/img2/50.jpg)

=== 

# โปรแกรมที่ใช้และวิธีดาวน์โหลดและติดตั้ง
# [Download VirtualBox](/VirtualBox.md)<br>
# [WinSCP 6.5 Download](/WinSCP.md)

=== 

# Help - Session Fixation แล้วกดดาวน์โหลดไฟล์ติดตั้ง (Setup.exe)


#### แนวคิดของช่องโหว่

| source | sink | vulnerability |
| :---- | :----: | ----: |
| 1$_POST + | setcookie() | = Session Fixation |

---

# คำอธิบายช่องโหว่ (Vulnerability Description)
Session Fixation เป็นช่องโหว่ที่ผู้โจมตีสามารถบังคับให้ผู้ใช้งานใช้ Session ID ที่ผู้โจมตีกำหนดไว้ล่วงหน้า ได้ เมื่อผู้ใช้งานทำการเข้าสู่ระบบเรียบร้อยแล้ว ผู้โจมตีจะสามารถใช้ Session ID เดียวกันนั้น เพื่อเข้าถึงบัญชีของผู้ใช้งานและสวมรอยเป็นผู้ใช้งานได้ทันที

---

###### กล่าวโดยสรุปคือ

> ระบบยอมรับ Session ID จากผู้ใช้โดยตรง ทำให้ผู้ไม่หวังดีสามารถควบคุม Session ของผู้อื่นได้

---

# ตัวอย่างโค้ดที่มีช่องโหว่ (Vulnerable Example Code)

```php
setcookie("PHPSESSID", $_GET["sessid"]);
```

> โค้ดตัวอย่างนี้แสดงให้เห็นว่า
ระบบนำค่า Session ID ที่รับมาจากผู้ใช้ผ่าน URL ไปตั้งค่าเป็น Session ของระบบโดยตรง ซึ่งเป็นพฤติกรรมที่ไม่ปลอดภัย

---

# ตัวอย่างการโจมตี (Proof of Concept)

```bash
/index.php?sessid=1f3870be274f6c49b3e31a0c6728957f
```

> ผู้โจมตีสามารถส่ง Session ID ผ่าน URL ให้ผู้ใช้งาน หากระบบนำค่า Session ID นี้ไปใช้งานจริง ผู้โจมตีก็สามารถใช้ Session เดียวกันเข้ามาในระบบได้ภายหลัง

---

# แนวทางการแก้ไข (Patch)
## ไม่ควรนำ Session Token หรือ Session ID ที่ผู้ใช้ส่งเข้ามาไปใช้งานโดยตรง
ระบบควรเป็นผู้สร้างและจัดการ Session ID เองทั้งหมด เพื่อป้องกันไม่ให้ผู้โจมตีสามารถกำหนด Session ID ให้ผู้ใช้งานได้

```bash
1. No code.
```

---

# ฟังก์ชันที่ช่วยเพิ่มความปลอดภัย (Related Securing Functions)

> ไม่มีฟังก์ชันเฉพาะที่ระบุไว้
แต่ควรใช้การจัดการ Session ของฝั่ง Server อย่างเหมาะสม เช่น การสร้าง Session ID ใหม่จากระบบเท่านั้น

>>># None.

=====

# ปัญหาที่ RIPS เจอ
### File: /var/www/html/bWAPP/commandi.php
![This is an alt text.](/img/img2/51.jpg)

---

# เปิด WinSCP
![This is an alt text.](/img/img2/55.jpg)

# แล้วมองดูช่องขวาว่าหาชื่อว่า selections.php
![This is an alt text.](/img/img2/56.jpg)

# จากนั้นทำการลากไฟล์ทีต้องการจากหน้าต่างทางด้านขวา (เครื่องเรา)ไปวางไว้ใน หน้าต่างทางด้านซ้าย (เครื่อง Server)
![This is an alt text.](/img/img2/57.jpg)

# จากนั้นคลิกขวาที่ไฟล์ชื่อว่าselections.php และกด Open
![This is an alt text.](/img/img2/58.jpg)

# จากนั้นจะขึ้นหน้าโค้ดมาให้แก้
![This is an alt text.](/img/img2/59.jpg)

---

# ดูโค้ดก่อนแก้ (Before) ❌

```php
Userinput reaches sensitive sink. For more information, press the help icon on the left side.
78: setcookie setcookie("security_level", $security_level_cookie, time() + 60 * 60 * 24 * 365, "/", "", false, false);  // selections.php
63: $security_level_cookie = "0";  // selections.phpswitch($security_level_cookie),
58: $security_level_cookie = "2";  // selections.phpswitch($security_level_cookie), case "2" : ,
53: $security_level_cookie = "1";  // selections.phpswitch($security_level_cookie), case "1" : ,
48: $security_level_cookie = "0";  // selections.phpswitch($security_level_cookie), case "0" : ,
41: $security_level_cookie = $_POST['security_level'];  // selections.php
requires:
38: if(isset($_POST['form_security_level']) && isset($_POST['security_level']))
75: if($evil_bee == 1) else 
```

# ก่อนแก้ไข
## รับค่ามาปุ๊บ ยัดใส่ Cookie ปั๊บ อันตรายมาก!
![This is an alt text.](/img/img2/53.jpg)

# หลังแก้ไข
## รับค่ามาปุ๊บ ยัดใส่ Cookie ปั๊บ อันตรายมาก!
![This is an alt text.](/img/img2/54.jpg)

---
## เมื่อแก้โคตรเสร็จแล้วบันทึกและลากไฟล์จากด้านซ้ายไปด้านขวาและกด Yes
![This is an alt text.](/img/img2/60.jpg)

---

## เช็คผ่าน RIPS อีกครั้งว่าปัญหานั้นเป็น 0 แล้ว
![This is an alt text.](/img/img2/61.jpg)


## ทดสอบการทำงานหลังแก้ไข
เมื่อทำการแก้ไขโค้ดเสร็จสิ้นแล้ว ขั้นตอนสำคัญถัดมาคือการทดสอบระบบซ้ำ (Re-testing) เพื่อยืนยันว่าฟังก์ชันต่างๆ ยังคงทำงานได้ถูกต้อง และการปิดช่องโหว่นี้ไม่ได้ส่งผลกระทบให้ส่วนอื่นของระบบเสียหายครับ
![This is an alt text.](/img/img2/62.jpg)

### การทดสอบที่ทำ:
Server: 110.164.252.222 Address: 110.164.252.222#53 Non-authoritative answer: Name: www.ivecr5.ac.th Address: 122.155.166.155

---

#  ทำไมวิธีนี้ถึงปลอดภัย?
1. ตัดวงจรข้อมูล (Data Flow Break): ข้อมูลดิบจากภายนอก ไม่สามารถไหลไปถึงจุดบันทึก (Sensitive Sink) ได้โดยตรงอีกต่อไป
2. กฎเหล็ก (Whitelisting): เรากำหนดไว้เลยว่าใน Cookie จะมีได้แค่เลข 0, 1, 2 เท่านั้น แฮกเกอร์จะพยายามยัดเยียดโค้ดอันตราย หรือค่าแปลกปลอมลงไปไม่ได้เลย
3. การซ่อนข้อมูล (HttpOnly): การปรับค่า setcookie ตัวสุดท้ายเป็น true เปรียบเสมือนการใส่กุญแจล็อค Cookie ไว้ ให้เฉพาะ Server เท่านั้นที่อ่านได้ โปรแกรมแฮกทางหน้าเว็บ (JavaScript) จะมองไม่เห็น

---
## สรุป
จากเดิมที่ "ใครส่งอะไรมาก็รับหมด" เราเปลี่ยนระบบใหม่เป็น "เรากำหนดเอง (Whitelist) + เปลี่ยนรหัสผ่านใหม่ทุกครั้ง (Regenerate) + ซ่อนกุญแจไว้ (HttpOnly)" ทำให้แฮกเกอร์เจาะไม่เข้า และเครื่องมือสแกนหาเรื่องด่าไม่ได้อีกต่อไปครับ!