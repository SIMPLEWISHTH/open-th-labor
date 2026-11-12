# HANDOFF: open-th-labor → Claude Desktop

เอกสารนี้ให้ Claude Desktop อ่านแล้วทำสองอย่าง: (1) ลงโปรเจกต์ลงเครื่อง (2) สร้าง Project ใน Claude ให้ทำงานต่อได้ทันที

- **Repo:** https://github.com/SIMPLEWISHTH/open-th-labor
- **Branch หลัก:** `main` (branch นี้ `claude/vigilant-franklin-mjv1ev` มีเอกสาร handoff เพิ่มเข้ามา)
- **เว็บที่ deploy แล้ว (ถ้าเปิด Pages):** https://simplewishth.github.io/open-th-labor/
- **เจ้าของ:** SIMPLEWISHTH / @Digital WRS

---

## 1. โปรเจกต์นี้คืออะไร

งานวิจัยตลาดแรงงานไทยเทียบโลก ปี 2026 หัวข้อ "ช่องว่างระหว่างคนกับงาน" ประกอบด้วย

- รายงานหลัก + คำตอบคำถามวิจัย 4 ข้อ
- บันทึกวิจัยโจทย์ย่อย 8 ข้อ (ทำครบแล้ว) แต่ละข้อเป็นหน้าเว็บ interactive
- รายงานประวัติศาสตร์ตลาดแรงงาน + ไทม์ไลน์ภาพ 11 ยุค

**ภาษา:** เนื้อหาทั้งหมดเป็นภาษาไทย

## 2. โครงสร้างไฟล์

ไม่มี build step, ไม่มี package.json, ไม่มี dependency ทุกหน้าเป็น HTML ไฟล์เดียว (CSS/JS/ข้อมูล inline)

| ไฟล์ | เนื้อหา |
| --- | --- |
| `README.md` | ภาพรวม + คำตอบ 4 ข้อ + กราฟ Mermaid + ตารางสรุปโจทย์ย่อย |
| `report-2026.md` | รายงานฉบับเต็มพร้อมลิงก์แหล่งข้อมูล (ต้นทางของตัวเลขทั้งหมด) |
| `history-labor-evolution.md` | ประวัติศาสตร์ตลาดแรงงาน จากยุคล่าสัตว์ถึงยุค AI |
| `index.html` | เว็บหลัก 12 กราฟ, tooltip, ตารางข้อมูลใต้กราฟ, dark mode, สารบัญลอยขวาบน |
| `journey.html` | ไทม์ไลน์ 11 ยุคเต็มจอ ฉากกระดาษตัดที่ morph ระหว่างยุค |
| `q1-underutilization.html` | ภูเขาน้ำแข็ง 0.95%: ดัชนีใช้แรงงานไม่เต็มศักยภาพรายจังหวัด |
| `q2-skills-verification.html` | ชั้นยืนยันทักษะ + ตัวคำนวณขยายผล |
| `q3-ai-entry-level.html` | AI กับงานระดับเริ่มต้น (ธีมนกคีรีบูน) |
| `q4-spatial-matching.html` | จับคู่งานเชิงพื้นที่ เหนือ/อีสาน + แผนที่ 77 จังหวัด |
| `q5-platform-riders.html` | ทางเลือกคุ้มครองไรเดอร์ + แบบจำลองปรับค่าได้ |
| `q6-learning-accounts.html` | บัญชีเรียนรู้แรงงานนอกระบบ + ตัวคำนวณงบ |
| `q7-occupation-standards.html` | มาตรฐาน ISCO-08/ESCO/O*NET + ผลทดลองเชื่อมรหัส |
| `q8-skills-partnership.html` | Skills partnership กับเพื่อนบ้าน + ตัวคำนวณจุดคุ้มทุน |
| `.nojekyll` | ให้ GitHub Pages เสิร์ฟไฟล์ตรง ๆ |

ข้อสังเกตทางเทคนิค: ทุกหน้าโหลด Google Fonts จากเน็ต (Anuphan, Sarabun, Kanit ฯลฯ) ถ้า offline จะ fallback เป็นฟอนต์ระบบ เนื้อหายังใช้ได้

## 3. ลงเครื่อง

ต้องมี `git` เท่านั้น (ไม่ต้องมี Node/Python เพื่อดูเว็บ)

```bash
git clone https://github.com/SIMPLEWISHTH/open-th-labor.git
```

```bash
cd open-th-labor
git checkout claude/vigilant-franklin-mjv1ev   # เฉพาะถ้าต้องการไฟล์ HANDOFF.md นี้; ไม่งั้นอยู่ main ได้
```

เปิดดูเว็บ (เลือกอย่างใดอย่างหนึ่ง)

```bash
# แบบ 1: เปิดไฟล์ตรง ๆ
open index.html          # macOS
# start index.html       # Windows
# xdg-open index.html    # Linux
```

```bash
# แบบ 2: ผ่าน local server (ใกล้เคียง GitHub Pages ที่สุด ถ้ามี Python)
python3 -m http.server 8000
# แล้วเปิด http://localhost:8000/
```

ตรวจว่าลงสำเร็จ: เปิด `index.html` แล้วเห็นหัวเรื่อง "ตลาดแรงงานไทย 2026" พร้อมกราฟ, ลองสลับ dark mode, และเปิด `q1-underutilization.html` ถึง `q8-skills-partnership.html` ทั้ง 8 หน้าได้โดยไม่มี error ใน console

## 4. สร้าง Project ใน Claude Desktop

### ชื่อ Project
`open-th-labor: ตลาดแรงงานไทย 2026`

### Project instructions (คัดลอกไปวางได้เลย)

```
คุณช่วยงานวิจัยตลาดแรงงานไทยเทียบโลก ปี 2026 หัวข้อ "ช่องว่างระหว่างคนกับงาน"
repo: https://github.com/SIMPLEWISHTH/open-th-labor

กติกา:
1. ตอบและเขียนเนื้อหาเป็นภาษาไทย
2. ตัวเลขทุกตัวต้องมีที่มาใน report-2026.md หรือบันทึกวิจัยโจทย์ย่อย ห้ามแต่งตัวเลขใหม่
   ถ้าจะเพิ่มตัวเลข ต้องระบุแหล่งที่มาและระดับหลักฐาน
3. ตัวเลขที่ยังยืนยันต้นฉบับไม่ได้ ให้ติดป้ายบอกชัดเจน (ดูหัวข้อ "ข้อแก้ไขจากรายงานต้นทาง" ใน README.md)
4. หน้าเว็บทุกหน้าเป็น HTML ไฟล์เดียว ไม่ใช้ build step รองรับ dark mode มี tooltip
   และมีตารางข้อมูลใต้ทุกกราฟ รองรับมือถือ
5. ตัวชี้วัดที่ต้องไม่สับสน: 2.2 ล้านคนคือ "ผู้เสมือนว่างงาน" ของ สศช.
   ผู้ทำงานต่ำระดับที่อยากทำเพิ่มจริง 0.17-0.19 ล้านคน
6. กลุ่มตัวเลขที่ซ้อนกัน (ผู้ว่างงาน/ทำงานต่ำระดับ/นอกระบบ/สัมผัส GenAI) ห้ามนำมารวมกัน
```

### Knowledge files ที่ควรอัปโหลด (ถ้าใช้ Claude Projects)

อัปโหลดเฉพาะ Markdown (รวมราว 170 KB) ส่วน HTML ใหญ่ไฟล์ละ 70-110 KB และเป็น code ให้ใช้ผ่านการ clone แทน

1. `README.md`
2. `report-2026.md`
3. `history-labor-evolution.md`
4. `HANDOFF.md` (ไฟล์นี้)

### ถ้าใช้ Claude Code ใน Desktop
เปิดโฟลเดอร์ `open-th-labor` ที่ clone ไว้เป็น working directory ได้เลย ไม่ต้องตั้งค่าเพิ่ม (แนะนำให้รัน `/init` ครั้งแรกเพื่อสร้าง `CLAUDE.md` จากหัวข้อ 2 และกติกาข้างบน)

## 5. สถานะงาน ณ วันที่ handoff (12 พ.ย. 2026)

- ทำแล้ว: รายงานหลัก, README, เว็บ index, journey, history, บันทึกวิจัยโจทย์ย่อยครบ 8 ข้อ (q1-q8)
- PR #1-#6 merge เข้า `main` หมดแล้ว ไม่มี PR ค้าง
- ยังไม่มี: `CLAUDE.md`, CI, test (ไม่จำเป็นสำหรับ static site)

### เรื่องที่ควรทำต่อ / ระวัง

1. **ตัวเลขที่ยืนยันต้นฉบับไม่ได้:** Rapid Asia เรื่องแรงงานเพื่อนบ้านที่ผ่านการฝึก (<20% → 55%) และนายจ้างรายงานทักษะไม่ตรง (70% → 40%) ดูรายละเอียดใน `q8-skills-partnership.html`
2. **ตัวเลข 6.69 บาท/กม.** มาจากข้อพิพาทของไรเดอร์ Lalamove (ส่งพัสดุ) ไม่ใช่ไรเดอร์ส่งอาหาร
3. **"ระดับหลักฐาน"** ในตารางนวัตกรรม (●●● / ●●○ / ●○○) ผู้จัดทำจัดกลุ่มเอง ไม่ได้มาจากรายงานต้นทาง
4. **README ยังไม่ได้ลิงก์ `HANDOFF.md`** เพิ่มได้ถ้าต้องการ
5. **GitHub Pages:** ต้องตั้งค่า Settings → Pages → Deploy from a branch → `main` / root เอง (ถ้ายังไม่ได้เปิด)

## 6. Workflow การทำงานกับ repo

- ทำงานบน branch แยก (รูปแบบ `claude/<ชื่อ>`) แล้วเปิด PR เข้า `main`
- commit message ภาษาอังกฤษ สั้น ขึ้นต้นด้วยคำกริยา เช่น `Add research notes for sub-questions 7 and 8`
- หน้าใหม่: ทำเป็น HTML ไฟล์เดียว แล้วเพิ่มแถวใน README (ตารางโจทย์ย่อย + ตารางไฟล์ท้าย README)

---

## 7. Prompt สำหรับวางใน Claude Desktop

```
อ่านไฟล์ HANDOFF.md ใน https://github.com/SIMPLEWISHTH/open-th-labor (branch claude/vigilant-franklin-mjv1ev)
แล้วทำตามนี้ตามลำดับ:
1. git clone repo ลงเครื่อง ในโฟลเดอร์ที่ฉันเลือก (ถามฉันก่อนถ้ายังไม่ได้ระบุ)
2. เปิด index.html ตรวจว่าแสดงผลปกติ และไล่เปิด q1-q8 + journey.html ว่าไม่มี error
3. สร้าง Project ชื่อ "open-th-labor: ตลาดแรงงานไทย 2026" ใส่ Project instructions จากหัวข้อ 4
   และอัปโหลด README.md, report-2026.md, history-labor-evolution.md, HANDOFF.md เป็น knowledge
4. สรุปผลให้ฉัน: ลงที่ไหน ตรวจอะไรแล้วบ้าง มีอะไรผิดปกติ
ห้าม push หรือแก้ไฟล์ใน repo จนกว่าฉันจะสั่ง
```
