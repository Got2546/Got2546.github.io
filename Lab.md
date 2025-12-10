**[⬅ ย้อนกลับ](https://got2546.github.io/)**

![This is an alt text.](/img/Last%20Score%20Report.jpg )

# --- กำหนดค่า Microsoft Defender ---

>## ⭐ สรุปแล็บ
- ในการทำแล็บนี้ เป้าหมายคือ เรียนรู้การตั้งค่าระบบป้องกันมัลแวร์ใน Windows Security (Windows Defender) ซึ่งเป็นทักษะพื้นฐานที่คนทำงานด้าน Cybersecurity ต้องรู้ โดยเฉพาะเรื่องการ ตั้งค่า Exclusion, ดูเวอร์ชัน Threat Definition, อัปเดตความปลอดภัย, และ สแกนมัลแวร์ ที่เป็นงานประจำของฝ่าย IT Security จากบทเรียน CompTIA Security Pro ได้อธิบายไว้ว่า การป้องกันมัลแวร์ต้องอาศัยหลายอย่าง เช่นการอัปเดตแพตช์, ป้องกันไวรัส, firewall และการฝึกผู้ใช้ให้รู้เท่าทันภัยคุกคาม

## ✅ สิ่งที่ทําในแล็บนี้
- 1) เข้าไปยังเมนู Virus & threat protection
เริ่มจากเข้า Settings → Update & Security → Windows Security → Virus & threat protection
ขั้นตอนนี้ทำให้เราเข้าถึงศูนย์ควบคุมการป้องกันไวรัส ซึ่งตามแนว CompTIA ถือเป็นด่านแรกของการป้องกันมัลแวร์ (ข้อ Anti-malware ใน Malware Prevention)

- 2) เพิ่ม File Exclusion สำหรับไฟล์ cat.jpg
เข้าเมนู Manage settings → Exclusions → Add an exclusion → File
เลือกไฟล์ที่กำหนด: D:\Graphics\cat.jpg
เหตุผลที่ต้องรู้วิธีเพิ่ม Exclusion เพราะในการทำงานบางครั้งโปรแกรมต่าง ๆ อาจถูกรบกวนจาก Antivirus ดังนั้น IT จึงต้องรู้วิธี “ยกเว้นไฟล์ที่ปลอดภัย”

- 3)  เพิ่ม Process Exclusion สำหรับ welcome.scr
เลือก Add an exclusion → Process แล้วพิมพ์:
welcome.scr ไฟล์ .scr คือ Screensaver ซึ่งในโลกความเป็นจริงมีเคสที่แอบฝังมัลแวร์ได้บ่อย 
ดังนั้น แล็บนี้ตั้งใจให้เรา เรียนรู้วิธีจัดการกระบวนการที่ไวต่อความเสี่ยง