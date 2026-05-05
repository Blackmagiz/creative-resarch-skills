# CAMT Arts Research Skills

**ชุด Agent Skills สำหรับงานวิจัยเชิงสร้างสรรค์ทางศิลปะ**
**วิทยาลัยศิลปะ สื่อ และเทคโนโลยี มหาวิทยาลัยเชียงใหม่**
**(College of Arts, Media and Technology, Chiang Mai University)**

ชุด skill นี้ช่วยให้ Claude สนับสนุนงานวิจัยทางศิลปะของบุคลากร CAMT ได้อย่างมีประสิทธิภาพและรวดเร็ว ครอบคลุมทุกขั้นตอนตั้งแต่การวางแผน การทบทวนวรรณกรรม การวิจัยปฏิบัติ การเขียน การตรวจทาน ไปจนถึงการจัดรูปแบบสำหรับตีพิมพ์

---

## ภาพรวม (Overview)

ชุด skill นี้ออกแบบเฉพาะสำหรับงานวิจัยใน 14 สาขาที่ CAMT รับผิดชอบ:

- ทัศนศิลป์ (Visual Arts)
- ออกแบบ (Design)
- ดนตรี (Music)
- การแสดง (Performance)
- ประยุกต์ศิลป์ (Applied Arts)
- ปรัชญาศิลป์ (Philosophy of Art)
- สุนทรียศาสตร์ (Aesthetics)
- ประวัติศาสตร์ศิลป์ (Art History)
- โบราณคดี (Archaeology)
- สื่อศิลปะ (Media Arts)
- การออกแบบสื่อ (Media Design)
- เรขศิลป์ (Graphic Arts)
- ศิลปะการถ่ายภาพ (Photography)
- ศิลปศึกษา (Art Education) รวมถึงทัศนศิลป์ศึกษา ศิลปะการแสดงศึกษา/นาฏศิลป์ศึกษา ดนตรีศึกษา

**อ้างอิงและพัฒนาต่อจาก**: [Imbad0202/academic-research-skills](https://github.com/Imbad0202/academic-research-skills) ปรับให้เข้ากับลักษณะเฉพาะของงานวิจัยทางศิลปะ

---

## Skills ทั้งหมด 10 ตัว (10 Skills)

### Core Pipeline (4 skills) — ขั้นตอนหลักของการทำวิจัย

| # | Skill | หน้าที่ |
|---|-------|---------|
| 1 | **arts-research-pipeline** | ตัวจัดการ workflow 8 ขั้นตอน — orchestrator หลัก |
| 2 | **arts-deep-research** | ทบทวนวรรณกรรมเชิงลึก + สืบค้นแหล่งข้อมูลศิลปะ |
| 3 | **arts-paper-writer** | เขียนบทความ/วิทยานิพนธ์/exegesis |
| 4 | **arts-paper-reviewer** | จำลอง peer review (ทีม 5 คน + Devil's Advocate) |

### Specialized Methods (5 skills) — วิธีวิจัยเฉพาะทาง

| # | Skill | หน้าที่ |
|---|-------|---------|
| 5 | **practice-based-research** | งานวิจัยที่มีผลงานสร้างสรรค์เป็นแกน |
| 6 | **visual-analysis** | วิเคราะห์งานทัศนศิลป์/ภาพถ่าย/ออกแบบ |
| 7 | **performance-arts-research** | วิจัยดนตรี/การแสดง/นาฏศิลป์ |
| 8 | **art-history-archaeology** | วิจัยประวัติศาสตร์ศิลป์/โบราณคดี |
| 9 | **aesthetics-philosophy** | สุนทรียศาสตร์/ปรัชญาศิลป์ |

### Utility (1 skill) — เครื่องมือสนับสนุน

| # | Skill | หน้าที่ |
|---|-------|---------|
| 10 | **arts-citation-formatter** | จัดรูปแบบ citation (APA/Chicago/MLA/TCI) |

---

## สิ่งที่ทำให้ skill suite นี้แตกต่างจาก generic research skills

### 1. ออกแบบสำหรับงานศิลปะโดยเฉพาะ

- **Practice-based research** เป็น first-class — ไม่ใช่กรอบเสริม
- รองรับ creative output (ภาพ เสียง การแสดง) เป็น primary research contribution
- มี exegesis writing guide
- รองรับ formal analysis, iconographic, semiotic, contextual analysis ครบ

### 2. ตระหนักบริบทไทย/ล้านนา/อาเซียน

- เตือนการ impose Western frameworks ตรงๆ บนงานศิลปะไทย
- รวมระบบเฉพาะของไทย (ดนตรีไทย, นาฏศิลป์ไทย, จิตรกรรมล้านนา)
- รองรับ TCI standard และวารสารไทย
- รองรับการอ้างอิงเอกสารโบราณ (ใบลาน, สมุดข่อย, จารึก)

### 3. AI Hallucination Protection

- มี Integrity Gate 2 จุดใน pipeline
- เน้นการ verify references ทุกตัว (AI สร้าง references ปลอมเก่ง)
- มี checklist ก่อนส่งไป stage ถัดไป

### 4. Cultural & Ethical Sensitivity

- ครอบคลุม ethics ของการวิจัยกับชุมชน, มรดกวัฒนธรรม, looted artifacts
- รองรับการขอ permissions, IRB, copyright
- เตือน cultural essentialism, exoticization

### 5. Bilingual Support

- ทุก skill มี trigger keywords ทั้งไทยและอังกฤษ
- รองรับการเขียนงานทั้งสองภาษา
- คู่มือ Thai academic writing แยกออก

---

## วิธีติดตั้ง (Installation)

### Option A: Claude.ai (Pro/Max/Team/Enterprise)

1. **ดาวน์โหลด** ไฟล์ `camt-arts-research-skills.zip`
2. **แตกไฟล์** จะได้ folder ของแต่ละ skill (10 folders)
3. **สำหรับแต่ละ skill** ที่ต้องการใช้:
   - บีบ folder นั้นเป็น `.zip` แยก (เช่น `arts-research-pipeline.zip`)
   - ไปที่ Claude.ai → **Settings** → **Capabilities** → **Skills** → **Upload skill**
   - อัปโหลดไฟล์ zip
   - เปิดใช้งาน skill (toggle on)
4. **ทดสอบ** โดยพิมพ์คำสั่งเช่น "ช่วยทำวิจัยศิลปะให้หน่อย" — Claude จะเรียก `arts-research-pipeline` อัตโนมัติ

> **หมายเหตุ**: Claude.ai รับ skill ทีละไฟล์ — ต้อง zip แยกแต่ละ skill หรือใช้ skill-creator ในการ batch upload

### Option B: Claude Code (Filesystem-based)

```bash
# Clone หรือ download repo
cd /tmp
# (วาง folder camt-arts-research-skills/ ที่นี่)

# Personal level (ใช้ทุก project)
mkdir -p ~/.claude/skills
cp -r camt-arts-research-skills/* ~/.claude/skills/

# หรือ Project level (เฉพาะ project นี้)
mkdir -p .claude/skills
cp -r camt-arts-research-skills/* .claude/skills/
```

ตรวจสอบการติดตั้ง:
```bash
ls ~/.claude/skills/
# ควรเห็น 10 folders
```

ทดสอบใน Claude Code:
```
> ช่วย review เปเปอร์ที่ผมเพิ่งเขียนเสร็จหน่อย
# Claude จะเรียก arts-paper-reviewer skill
```

### Option C: API (สำหรับ developers)

ใช้ `/v1/skills` endpoint อัปโหลด skill — ดู [Claude Skills API guide](https://platform.claude.com/docs/en/build-with-claude/skills-guide)

---

## ตัวอย่างการใช้งาน (Usage Examples)

### ตัวอย่างที่ 1: เริ่มงานวิจัยใหม่

```
คุณ: "อยากทำวิจัยเรื่องการประยุกต์ลายล้านนาในการออกแบบ
     บรรจุภัณฑ์ร่วมสมัย จะเริ่มยังไงดี?"

Claude: [เรียก arts-research-pipeline skill อัตโนมัติ]
        ถามคำถาม pre-pipeline 6 ข้อ → กำหนด mode → 
        เริ่ม Stage 1 (PLAN) → ช่วยกำหนด RQ และ methodology
```

### ตัวอย่างที่ 2: ทบทวนวรรณกรรม

```
คุณ: "หาเปเปอร์เกี่ยวกับ rasa theory ในงาน 
     contemporary Thai dance ให้หน่อย"

Claude: [เรียก arts-deep-research skill]
        แนะนำฐานข้อมูล (RILM, Asian Theatre Journal, TCI) →
        สร้าง search queries → สรุปเป็น literature matrix →
        ระบุ research gap
```

### ตัวอย่างที่ 3: วิเคราะห์ภาพ

```
คุณ: "ช่วยวิเคราะห์จิตรกรรมฝาผนังวัดบวรนิเวศ 
     ห้องด้านทิศใต้ ตามกรอบ Panofsky"

Claude: [เรียก visual-analysis skill — mode: iconographic]
        วิเคราะห์ 3 ระดับ → Pre-iconographic, 
        Iconographic, Iconological → ระบุ limitations 
        ของ Panofsky framework กับงานไทย
```

### ตัวอย่างที่ 4: เขียน Exegesis

```
คุณ: "ผมเป็นศิลปินทำงาน sound installation ที่ใช้
     เสียงพิธีกรรมล้านนา จะเขียน exegesis ส่วนแรกยังไง?"

Claude: [เรียก practice-based-research + arts-paper-writer]
        แนะนำโครงสร้าง exegesis → ช่วยเขียน 
        Contextual Review + Methodology of Practice
```

### ตัวอย่างที่ 5: ตรวจสอบ References

```
คุณ: "ตรวจ reference list ของผมหน่อย ว่ามีอะไรเป็น 
     AI hallucination หรือเปล่า?"

Claude: [เรียก arts-citation-formatter — mode: verify]
        ตรวจแต่ละ entry → ระบุที่อาจไม่มีจริง → 
        แนะนำให้ค้น Google Scholar/JSTOR ก่อนใช้
```

---

## Workflow ที่แนะนำ (Recommended Workflow)

```
1. PLAN
   ↓ [arts-research-pipeline orchestrates]
   
2. RESEARCH (Literature Review)
   ↓ [arts-deep-research]
   
3. INTEGRITY GATE 1
   ↓ [verify all sources]
   
4. METHOD/CREATE
   ↓ [เลือก specialized skill ตามประเภทงาน:]
     • practice-based-research     → งาน creative
     • visual-analysis             → วิเคราะห์ภาพ
     • performance-arts-research   → ดนตรี/การแสดง
     • art-history-archaeology     → งานประวัติศาสตร์
     • aesthetics-philosophy       → งานทฤษฎี
   
5. WRITE
   ↓ [arts-paper-writer]
   
6. INTEGRITY GATE 2
   
7. REVIEW
   ↓ [arts-paper-reviewer]
   
8. REVISE → VERIFY → FINALIZE
   ↓ [arts-citation-formatter — final formatting]
   
9. SUBMIT
```

---

## คำเตือนและข้อจำกัด (Limitations & Cautions)

### ⚠️ AI ไม่ใช่นักวิจัย — เป็นผู้ช่วย

> "AI is your copilot, not the pilot." (Imbad0202)

skill suite นี้ช่วย:
- ✅ จัดโครงสร้างความคิด
- ✅ ค้นหาวรรณกรรม
- ✅ ตรวจการเขียน
- ✅ จัดรูปแบบ
- ✅ ตรวจ logic ของ argument

skill suite นี้**ไม่**ทดแทน:
- ❌ การกำหนดคำถามวิจัยที่มีคุณค่า
- ❌ การลงพื้นที่/อ่านงานต้นฉบับ
- ❌ การตีความที่อาศัยประสบการณ์
- ❌ การตัดสินทางจริยธรรม
- ❌ การพิจารณาบริบทวัฒนธรรมที่ลึกซึ้ง

### ⚠️ ตรวจสอบทุกอย่างที่ AI สร้าง

โดยเฉพาะ:
- **References** — AI hallucinate ชื่อ/ปี/วารสารปลอมได้บ่อยมาก
- **ข้อมูลศิลปิน/ผลงาน** — ตรวจ ปี/สถานที่/สื่อ/ขนาด ทุกครั้ง
- **Quotes** — เปรียบกับต้นฉบับเสมอ ไม่ใช่ paraphrase
- **DOI** — ลองเปิด doi.org/[doi] ดูว่าใช้ได้จริง

### ⚠️ บริบทวัฒนธรรม

skill suite นี้ออกแบบโดยตระหนักบริบทไทย/ล้านนา แต่:
- ไม่สามารถทดแทน knowledge holder ในชุมชน
- ต้องการการ consult กับ stakeholders ในงานชาติพันธุ์
- AI mediation ไม่ใช่ direct dialogue

---

## Roadmap & Future Development

แผนการพัฒนาในอนาคต:
- [ ] เพิ่ม `arts-grant-writer` skill — สำหรับเขียนข้อเสนอขอทุน
- [ ] เพิ่ม `arts-presentation-builder` skill — สำหรับ conference/exhibition
- [ ] เพิ่ม `dataset-for-arts-research` skill — สำหรับงาน digital humanities
- [ ] เพิ่ม `oral-history-skill` — สำหรับงาน oral tradition
- [ ] รองรับการแปลข้ามภาษาไทย-อังกฤษอัตโนมัติ
- [ ] ขยาย references library ใน `references/` ของแต่ละ skill

---

## Contributing

ยินดีรับ feedback และการพัฒนาจากบุคลากร CAMT:
- รายงาน issues
- เสนอ feature ใหม่
- ส่ง pull request
- ติดต่อ: [Research Support Unit, CAMT]

---

## License

MIT License — ใช้ได้ฟรี ไม่จำกัด ทั้งภายในและภายนอกมหาวิทยาลัย แต่กรุณา attribute

---

## Acknowledgments

- **ต้นแบบ**: Imbad0202/academic-research-skills (Cheng-I Wu)
- **มาตรฐาน**: Anthropic Agent Skills (open standard)
- **บริบท**: ผลงานวิชาการของอาจารย์-นักวิจัย CAMT, มหาวิทยาลัยเชียงใหม่
- **อ้างอิงเพิ่มเติม**: ดูใน reference list ของแต่ละ skill

---

## เอกสารเพิ่มเติม

แต่ละ skill มีเอกสารใน `references/` directory ของตัวเอง — ใช้สำหรับเก็บ:
- รายละเอียด databases
- Templates เพิ่มเติม
- Examples
- Specialized references

โครงสร้าง:
```
camt-arts-research-skills/
├── README.md                          # ไฟล์นี้
├── arts-research-pipeline/
│   ├── SKILL.md
│   └── references/
├── arts-deep-research/
│   ├── SKILL.md
│   └── references/
├── arts-paper-writer/
├── arts-paper-reviewer/
├── practice-based-research/
├── visual-analysis/
├── performance-arts-research/
├── art-history-archaeology/
├── aesthetics-philosophy/
└── arts-citation-formatter/
```

---

**สำหรับคำถามเพิ่มเติม กรุณาติดต่อหน่วยส่งเสริมงานวิจัย วิทยาลัยศิลปะ สื่อ และเทคโนโลยี มหาวิทยาลัยเชียงใหม่**

Version 1.0.0 | May 2026
