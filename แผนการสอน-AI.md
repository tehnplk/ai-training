# แผนการสอน AI

ก่อนเริ่มหัวข้อแรก: **จริยธรรมและความปลอดภัย** ไม่ใส่ข้อมูลส่วนบุคคล ตรวจทานทุกครั้ง คนเป็นผู้รับผิดชอบ เคารพลิขสิทธิ์ โปร่งใส และอ่านก่อนกดอนุญาตคำสั่งของ Claude Code

| No | เรื่อง | โปรแกรมที่ต้องลง | Skill |
|----|--------|------------------|-------|
| 1 | หนังสือราชการ | Python, Node.js, LibreOffice | docx |
| 2 | สรุปเนื้อหาจาก PDF, DOCX | Python, Pandoc | pdf, docx |
| 3 | สร้างและวิเคราะห์ไฟล์ Excel | Python, LibreOffice | xlsx |
| 4 | Mini Dashboard (HTML + Chart.js) จากไฟล์ Excel ข้อ 3 | Python, เว็บเบราว์เซอร์ | dataviz |
| 5 | สร้าง PowerPoint | Python, Node.js, LibreOffice | pptx |
| 6 | Motion Graphic | Node.js 22+, Python, FFmpeg, Playwright Chromium | claude-animation, motion-broll, brag, pixel2motion |

หัวข้อ 4 ใช้ไฟล์ Excel ที่สร้างในหัวข้อ 3 เช่น ข้อมูลสมมติ 100 คน (id, fullname, gender, age, bmi) แล้วสั่งให้ Claude สรุปเป็นหน้า HTML ไฟล์เดียว มีตัวเลขสรุป กราฟ Chart.js ปุ่มกรอง และตารางข้อมูล เปิดดูในเบราว์เซอร์ได้ทันที (ต้องต่ออินเทอร์เน็ตเพื่อโหลด Chart.js)

หัวข้อ 6 Motion Graphic มี 4 งานย่อย:

| งานย่อย | โปรแกรมที่ต้องลง | Skill |
|---------|------------------|-------|
| ทีเซอร์ Animation พร้อมเสียง (MP4) | Node.js, FFmpeg | claude-animation |
| B-roll / Overlay ประกอบคลิปสอน | Node.js, Python, FFmpeg | motion-broll |
| Launch Video จาก URL เว็บไซต์ | Node.js 22+, FFmpeg | brag |
| Animate โลโก้ (HTML / GIF / วิดีโอ) | Python, Playwright Chromium | pixel2motion |

อ้างอิงหัวข้อ 6: [บทความ 8 Use Case Motion Graphic ด้วย Claude Code](https://noobitguy.one/claude-motion-graphic/) และ [คลิป YouTube](https://www.youtube.com/watch?v=djQMXTra5E0)

## Checklist ติดตั้งก่อนเรียน

เปิด Terminal (PowerShell หรือ CMD) แล้วรันคำสั่งทีละบรรทัด ติดตั้งเสร็จให้ปิดแล้วเปิด Terminal ใหม่

| โปรแกรม | ใช้ในหัวข้อ | คำสั่งติดตั้ง | ตรวจสอบ |
|---------|-------------|---------------|---------|
| Python 3 | 1, 2, 3, 4, 5, 6 | `winget install Python.Python.3.12` | `python --version` |
| Node.js (LTS) | 1, 5, 6 | `winget install OpenJS.NodeJS.LTS` | `node --version` (ต้อง 22 ขึ้นไป) |
| LibreOffice | 1, 3, 5 | `winget install TheDocumentFoundation.LibreOffice` | `soffice --version` |
| Pandoc | 2 | `winget install JohnMacFarlane.Pandoc` | `pandoc --version` |
| FFmpeg | 6 | `winget install Gyan.FFmpeg` | `ffmpeg -version` |
| Playwright Chromium | 6 | `pip install pillow numpy playwright` แล้ว `python -m playwright install chromium` | `python -m playwright --version` |

## Skill ที่ใช้

| Skill | ใช้ในหัวข้อ | หน้าที่ |
|-------|-------------|---------|
| docx | 1, 2 | สร้าง แก้ไข และอ่านไฟล์ Word (.docx) |
| pdf | 2 | อ่าน ดึงข้อความ/ตาราง จากไฟล์ PDF |
| xlsx | 3, 4 | สร้าง แก้ไข วิเคราะห์ไฟล์ Excel ใส่สูตร จัดรูปแบบ ทำกราฟ |
| dataviz | 4 | หลักการเลือกกราฟ ชุดสีที่คนตาบอดสีแยกได้ tooltip และโหมดมืด สำหรับ dashboard |
| pptx | 5 | สร้าง แก้ไขสไลด์ PowerPoint (.pptx) |
| claude-animation | 6 | วางโครงเรื่อง สร้างภาพลายเส้นวาดมือและเสียง ออกเป็น MP4 |
| motion-broll | 6 | ใส่วิดีโอ + ซับ (SRT) ได้คลิป B-roll ตรงจังหวะคำพูด พร้อมหน้าเทียบก่อน/หลัง |
| brag | 6 | อ่านโปรเจกต์/เว็บไซต์ แล้วสร้าง Launch Video ~20 วินาที พร้อมเพลงและข้อความโพสต์ |
| pixel2motion | 6 | แปลงโลโก้ PNG/JPG เป็น SVG แล้วทำ animation ปรับความเร็วได้ export เป็น GIF/วิดีโอ |

## ติดตั้ง Skill

| Skill | คำสั่ง (พิมพ์ใน Terminal) | หมายเหตุ |
|-------|--------------------------|----------|
| claude-animation | `claude plugin marketplace add buildwithhanif/claude-animation-skill` แล้ว `claude plugin install claude-animation@claude-animation-skill` | ครั้งแรกรัน `npm install` ในโฟลเดอร์ skill |
| motion-broll | `npx skills add Barty-Bart/motion-graphics` แล้วเลือก motion-broll | ครั้งแรก skill ลง Playwright + Chromium ให้เอง |
| brag | `npx skills add https://github.com/latent-spaces/brag --skill brag` | บน Opus 5.5 จะใช้ /brag-slim อัตโนมัติ ไม่ต้องลง Hyperframes |
| pixel2motion | ส่ง URL https://github.com/nolangz/pixel2motion ให้ Claude แล้วพิมพ์ "ฝากลง skill นี้ให้หน่อย" | ไม่มีคำสั่งติดตั้งในเอกสาร repo |

ติดตั้งเสร็จให้ปิดแล้วเปิด Claude Code ใหม่ skill จึงจะขึ้น
