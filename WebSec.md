**[⬅ ย้อนกลับ](https://got2546.github.io/)**

# --- กำหนดค่า Microsoft Defender ---

# ขั้นตอนที่ 1 ดาวน์โหลดไฟล์ติดตั้ง
> ไปที่เว็บไซต์อย่างเป็นทางการ: virtualbox.org
![This is an alt text.](/img/img2/0.1.jpg)

> คลิกที่เมนู Downloads
![This is an alt text.](/img/img2/0.2.jpg)

> ภายใต้หัวข้อ "VirtualBox 7.x.x platform packages" ให้คลิกที่ Windows hosts
![This is an alt text.](/img/img2/1.jpg)

> (แนะนำ) ให้ดาวน์โหลด "VirtualBox 7.x.x Oracle VM VirtualBox Extension Pack" มาเก็บไว้ด้วยครับ (ต้องใช้คู่กันเพื่อให้รองรับ USB 3.0 และฟีเจอร์อื่นๆ)
![This is an alt text.](/img/img2/2.jpg)

# ขั้นตอนที่ 2: เริ่มการติดตั้ง (Installation)

> ดับเบิ้ลคลิก ไฟล์ .exe ที่ดาวน์โหลดมา (เช่น VirtualBox-7.2.6-xxxxx-Win.exe)
![This is an alt text.](/img/img2/4.jpg)

> หน้าต่าง Setup จะเด้งขึ้นมา ให้กด Next >
![This is an alt text.](/img/img2/5.jpg)

> Custom Setup: หน้าจอนี้จะให้เลือกตำแหน่งติดตั้งและฟีเจอร์ ปกติไม่ต้องปรับอะไรครับ ให้ใช้ค่า Default ได้เลย แล้วกด Next >
![This is an alt text.](/img/img2/7.jpg)

> Warning: Network Interfaces:
>> 	ข้อควรระวัง: หน้าจอนี้จะมีตัวหนังสือสีแดงเตือนว่า "Installing the Oracle VM VirtualBox Networking feature will reset your network connection..."
>> ไม่ต้องตกใจครับ นี่เป็นเรื่องปกติ โปรแกรมจะทำการรีเซ็ตการ์ดแลนของคุณชั่วคราว (เน็ตจะตัดไปประมาณ 2-3 วินาทีแล้วกลับมา)
>> ให้กด Yes เพื่อไปต่อ
![This is an alt text.](/img/img2/8.jpg)

> Missing Dependencies (ถ้ามี): หากมีหน้าต่างถามหา Python Core / win32api ถ้าคุณไม่ได้เป็นนักพัฒนาที่ต้องเขียนสคริปต์ควบคุม VirtualBox ให้กด Yes (Proceed with installation) ได้เลยครับ
![This is an alt text.](/img/img2/9.jpg)

> หน้าต่าง Custom Setup ในหัวข้อ Select one or more startup options ้ามันกดอยู่แล้วไปกดปุ่ม Next ได้เลยถ้ายังไม่ได้เลือกอะไรเลือกทั้งหมดเลย
![This is an alt text.](/img/img2/10.jpg)

> กดปุ่ม Install และรอสักครู่
![This is an alt text.](/img/img2/11.jpg)

> เมื่อเสร็จแล้ว ให้กด Finish (ถ้าติ๊กถูกไว้ โปรแกรมจะเปิดขึ้นมาเอง)
![This is an alt text.](/img/img2/13.jpg)

# ขั้นตอนที่ 3: เริ่มการนำเข้า (Import)

> เมื่อตั้งค่าทุกอย่างเรียบร้อยแล้ว ให้กดปุ่ม เลือก Import Appliance... (หรือกดคีย์ลัด Ctrl + I)
![This is an alt text.](/img/img2/15.jpg)

> ในช่อง Source: ตรวจสอบให้แน่ใจว่าเลือกเป็น "Local File System"
![This is an alt text.](/img/img2/16.jpg)

> คลิกที่ ไอคอนโฟลเดอร์ (ด้านขวาของช่อง File)
![This is an alt text.](/img/img2/17.1.jpg)

> หน้าต่างเลือกไฟล์จะเด้งขึ้นมา ให้ไปที่โฟลเดอร์ที่คุณดาวน์โหลดไฟล์ไว้
![This is an alt text.](/img/img2/17.2.jpg)

> ดับเบิ้ลคลิก ที่ไฟล์ .ova หรือ .ovf ที่ต้องการ (หรือคลิก 1 ครั้งแล้วกด Open)
![This is an alt text.](/img/img2/17.3.jpg)

> เมื่อตั้งค่าเสร็จแล้ว ให้กดปุ่ม Finish (หรือ Import)
![This is an alt text.](/img/img2/18.jpg)

> รอหลอดโหลดสีเขียววิ่งจนเต็ม (ความเร็วขึ้นอยู่กับขนาดไฟล์และความเร็วฮาร์ดดิสก์ของคุณ)
![This is an alt text.](/img/img2/19.jpg)

> เสร็จแล้ว
![This is an alt text.](/img/img2/20.jpg)