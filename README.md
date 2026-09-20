# วิธีเผยแพร่เว็บ Chachan STORY บน GitHub Pages

1. สมัคร/ล็อกอิน GitHub แล้วกด **New repository** ตั้งชื่อเช่น `chachan-story` เลือก Public
2. กด **Add file > Upload files** แล้วลากไฟล์ `index.html` **และ** `og-image.png` เข้าไป กด **Commit changes** (ต้องอัปโหลดสองไฟล์นี้คู่กัน ไม่งั้นภาพตอนแชร์ลิงก์จะไม่ขึ้น)
3. ไปที่ **Settings > Pages**
4. ที่ Source เลือก **Deploy from a branch** แล้วเลือก Branch `main` และโฟลเดอร์ `/ (root)` กด **Save**
5. รอ 1-2 นาที เว็บจะขึ้นที่ `https://ชื่อผู้ใช้.github.io/chachan-story/`
6. เปิดเว็บเช็กบนมือถือ แล้วส่งลิงก์ให้ลูกค้าทางไลน์

## แทนที่ข้อความ placeholder

เปิด `index.html` ใน GitHub (ไอคอนดินสอ) แล้วใช้ค้นหา (Ctrl+F) เพื่อแก้:

- `https://private-character-f70.notion.site/Chachan-STORY-TradingView-MCP-Guide-3e183b60fe7e80f385f5d57c8d211670` เปลี่ยนเป็นลิงก์หน้า Notion คู่มือฟรี (มี 3 ที่ ในปุ่ม "อ่านคู่มือฟรี")
- `[WEBSITE_URL]` เปลี่ยนเป็นลิงก์เว็บจริงจากขั้นตอนที่ 5 มี 6 ที่ (og:url, og:image และใน JSON-LD)
  **ต้องลงท้ายด้วยเครื่องหมาย /** เช่น `https://ชื่อผู้ใช้.github.io/chachan-story/` ไม่งั้นลิงก์ภาพ og:image จะเสีย
- `Chachan STORY` และ `[ชื่อบัญชี]` ในหัวข้อผู้เขียน/โซเชียล

ลิงก์ไลน์ https://line.me/R/ti/p/%40pluggy00 ถูกต้องแล้ว ไม่ต้องแก้

## ตรวจก่อนบอกใคร

รันสคริปต์ตรวจในโฟลเดอร์ `tools` (ต้องมี Python และรัน `pip install playwright` กับ `playwright install chromium` ครั้งแรกครั้งเดียว)

```
python tools/qa_site.py website/index.html
```

ต้องขึ้น "สรุป: ผ่านทั้งหมด" ถ้ายังไม่ผ่านแปลว่ายังแทน placeholder ไม่ครบ อย่าเพิ่งโปรโมท

## อยากแก้ภาพตอนแชร์ลิงก์

แก้ข้อความใน `tools/make_og_image.py` แล้วรัน `python tools/make_og_image.py` จะได้ `og-image.png` ใหม่ อัปโหลดทับของเดิม
