---
name: arts-paper-writer
description: เขียนบทความวิจัย, วิทยานิพนธ์, exegesis, และงานเขียนวิชาการสำหรับงานวิจัยทางศิลปะ ครอบคลุมทุกขั้นตอนตั้งแต่ outline จนถึง full draft รองรับโครงสร้างเฉพาะของ arts research (traditional academic, exegesis สำหรับ practice-based, exhibition catalog essay, museum text). Use when the user asks to "เขียนบทความวิจัย", "เขียนเปเปอร์", "ร่างวิทยานิพนธ์", "draft a paper", "write an exegesis", "write a research article", "เขียน abstract", "เขียน introduction", "academic writing for arts", or needs help structuring/writing any part of an arts research manuscript. MUST trigger this skill whenever a user mentions writing any academic content for arts research, even short pieces like abstracts.
license: MIT
metadata:
  author: CAMT Research Support Unit
  version: 1.0.0
  parent_skill: arts-research-pipeline
---

# Arts Paper Writer

ช่วยเขียนงานวิจัยทางศิลปะ ออกแบบให้รองรับลักษณะเฉพาะของงานวิจัยเชิงสร้างสรรค์ที่ traditional academic writing ไม่ได้ครอบคลุม

## Trigger Keywords

ภาษาไทย: เขียนบทความ, เขียนเปเปอร์, ร่างวิทยานิพนธ์, เขียน abstract, เขียน introduction, เขียน discussion, เขียน conclusion, เขียน exegesis, เขียนบทความวิชาการ

English: write paper, draft article, write thesis, write exegesis, academic writing, manuscript writing, write abstract

## Modes

| Mode | Output |
|------|--------|
| `full` (default) | ร่าง full paper ทุกส่วน |
| `outline-only` | outline + section abstracts |
| `section` | เขียนเฉพาะ section ที่ระบุ |
| `abstract-only` | เขียน abstract สั้น/ยาว |
| `exegesis` | เขียน exegesis สำหรับ practice-based |
| `revision` | revise ตาม reviewer comments |
| `format-convert` | แปลงรูปแบบ (e.g., LaTeX, journal template) |
| `lit-review` | เขียน literature review section อย่างเดียว |

## ก่อนเริ่ม: ถามข้อมูลที่จำเป็น

ถ้าผู้ใช้ยังไม่ระบุ ให้ถามให้ครบ:
1. ประเภทบทความ (research article, review, conference paper, vocational thesis, dissertation chapter, exegesis)?
2. วารสาร/สถานที่ตีพิมพ์เป้าหมาย → ดู guidelines ว่าต้องการ format อะไร
3. ความยาวที่ต้องการ (คำหรือหน้า)
4. ภาษา (Thai, English, bilingual)?
5. รูปแบบการอ้างอิง (APA 7, Chicago, MLA, journal-specific)?
6. ข้อมูลที่มีอยู่แล้ว (literature, data, creative work, drafts)?

## โครงสร้างมาตรฐาน 4 รูปแบบ

### A. Traditional Academic Article (สำหรับงานเชิงทฤษฎี/ประวัติศาสตร์/วิเคราะห์)

```
1. Title (ชื่อเรื่อง) — 12-15 คำ informative + specific
2. Abstract (200-300 คำ)
   - บริบท/ปัญหา (1-2 ประโยค)
   - RQ (1 ประโยค)
   - วิธีการ (1-2 ประโยค)
   - ผลการศึกษาหลัก (2-3 ประโยค)
   - implications (1 ประโยค)
3. Keywords (5-7 คำ)
4. Introduction (10-15% ของความยาวรวม)
   - Hook ที่น่าสนใจ
   - บริบทปัญหา
   - Gap ในวรรณกรรม
   - RQ + objectives
   - Significance
   - Roadmap ของบทความ
5. Literature Review / Theoretical Framework (15-20%)
   - จัดกลุ่มตามประเด็น ไม่ใช่ตาม author
   - แสดง critical engagement ไม่ใช่แค่สรุป
   - ลงท้ายด้วย gap ที่งานเราจะปิด
6. Methodology (10-15%)
   - ระบุ method และเหตุผลการเลือก
   - Data/material/objects of study
   - Analysis framework
   - Ethics (ถ้าเกี่ยวข้อง)
7. Analysis / Findings (30-35%)
   - แสดงหลักฐาน + การตีความ
   - ใช้ image/figure/score แทรกที่จำเป็น
   - แต่ละ argument มี evidence ชัดเจน
8. Discussion (15-20%)
   - เชื่อมกลับ literature
   - Implications (theoretical, methodological, practical)
   - ข้อจำกัด (limitations)
9. Conclusion (5%)
   - สรุปสั้น
   - Future research
10. References
11. Appendices (ถ้ามี)
```

### B. Exegesis Format (สำหรับ Practice-based Research)

```
1. Title
2. Abstract
3. Introduction
   - Research question + creative work overview
   - Why practice-based approach?
4. Contextual Review (แทน traditional lit review)
   - Artists/practitioners ที่ทำงานในเส้นทางคล้ายกัน
   - Theoretical/conceptual influences
   - Place this work in conversation
5. Methodology of Practice
   - Method ของการสร้างสรรค์ + เหตุผล
   - Process journal / documentation strategy
   - Reflexivity statement
6. The Work (Documentation)
   - บรรยายผลงาน — material, process, outcome
   - Visual/audio/video documentation พร้อม caption ละเอียด
   - Iteration และการพัฒนา
7. Critical Reflection
   - สิ่งที่ค้นพบจากการปฏิบัติ
   - Challenges และการแก้ปัญหา
   - Self-reflexivity — bias ของศิลปิน-นักวิจัยเอง
8. Contribution to Knowledge
   - งานนี้เพิ่มอะไรใหม่ — knowledge in practice, knowledge from practice
9. Conclusion + Future Direction
10. References
11. Documentation Appendix (high-res, video links)
```

### C. Exhibition Catalog Essay / Museum Text

```
1. Opening hook (story, image, question)
2. Artist introduction + practice context
3. Conceptual themes ของนิทรรศการ/ผลงาน
4. Key works analysis (3-5 ชิ้นเด่น)
5. Place in art history / contemporary discourse
6. Critical assessment
7. References (สั้น) / Further Reading
```

### D. Conference Paper (Short, 4000-6000 words)

ปรับโครงสร้าง A ให้สั้นลง — Lit review รวมกับ Intro, Discussion สั้น

## เทคนิคการเขียนสำหรับแต่ละ Section

### Abstract

**สูตร 5 ประโยค** (สำหรับ 200-300 คำ):
1. **บริบทกว้าง** — ทำไมหัวข้อนี้สำคัญ
2. **ช่องว่าง** — สิ่งที่ยังไม่รู้
3. **คำถามวิจัย/วัตถุประสงค์** — สิ่งที่งานนี้ทำ
4. **วิธีและผล** — ทำอย่างไร, พบอะไร
5. **Implication** — ทำไมสำคัญ

❌ **อย่าทำ**: เปิดด้วย "บทความนี้เป็นการศึกษาเรื่อง..."
✅ **ทำ**: เปิดด้วยปัญหา/ปรากฏการณ์ที่น่าสนใจ

### Introduction

**โครงสร้าง funnel** (กว้าง → แคบ):
- เปิดด้วยปรากฏการณ์/ปัญหาที่จับใจ
- ชี้ความสำคัญ (so what?)
- เกริ่นวรรณกรรมพอให้เห็น gap (ไม่ใช่ full lit review)
- ระบุ RQ และ objectives
- Roadmap

**Tip สำหรับงานศิลปะ**: ใช้ vivid imagery หรือ specific work เป็น anchor — เช่น เริ่มด้วยภาพ painting, scene จาก performance, หรือ design object เพื่อจับสายตา

### Literature Review

หลีกเลี่ยง "annotated bibliography style" (Author A พบว่า..., Author B พบว่า...)
เน้น **synthesis** — จัดกลุ่มตาม theme/argument/period:

```
✅ "งานวิจัยเกี่ยวกับการใช้สีในจิตรกรรมล้านนาแบ่งได้เป็น 3 แนวทาง 
ทางที่หนึ่งเน้น...(Author A, Author B); ทางที่สองเน้น...(Author C); 
และทางที่สามเน้น...(Author D, E) แม้ทั้งสามทางจะ..., แต่ยังไม่มีงาน
ใดที่ศึกษา..."
```

### Methodology

ต้องตอบ 4 คำถาม:
1. ทำอะไร (what)
2. ทำอย่างไร (how)
3. ทำไมเลือกวิธีนี้ (why this method, not others)
4. ข้อจำกัดของวิธี (limitations)

สำหรับ practice-based: ระบุ "researcher positionality" — ผู้วิจัยอยู่ตรงไหนกับวัตถุที่ศึกษา

### Analysis / Findings

**กฎ 3 ระดับ**:
1. **Description** — บรรยายสิ่งที่เห็น/ได้ยิน (objective)
2. **Analysis** — แยกแยะองค์ประกอบ ความสัมพันธ์
3. **Interpretation** — ความหมาย, นัยยะ (subjective แต่มีหลักฐาน)

อย่าข้าม description ไปสู่ interpretation เลย — reader จะตามไม่ทัน

### Discussion

**โครงสร้าง**:
- สรุปผลการศึกษาหลัก (1 ย่อหน้า)
- เชื่อมกลับวรรณกรรม — งานเรา confirm/extend/contradict งานก่อนหน้าอย่างไร
- Theoretical implication
- Methodological implication
- Practical implication
- Limitations (ซื่อสัตย์ — ไม่เกลือ)
- Future research

### Conclusion

**3 ประโยค minimum**:
1. ตอบ RQ ตรงๆ
2. นัยยะหลัก
3. Future research / call to action

ห้ามแนะนำสิ่งใหม่ใน conclusion ที่ไม่ได้กล่าวถึงในเนื้อหา

## เทคนิคการเขียนเฉพาะภาษา

### ภาษาไทยทางวิชาการ

**ปัญหาที่พบบ่อย**:
- ประโยคยาวเกินไป — ตัดเป็นประโยคย่อย
- ใช้ "เป็นที่" "การที่" บ่อยเกินไป
- ทับศัพท์โดยไม่จำเป็น (เช่น "ดิสคอร์ส" → ใช้ "วาทกรรม")
- คำว่า "นั้น" "นี้" "ดังกล่าว" เกินจำเป็น

**Tip**: คำศัพท์เฉพาะที่ยังไม่มีคำแปลไทย → ใส่ไทยตามด้วย (ภาษาอังกฤษ) ในการใช้ครั้งแรก

### ภาษาอังกฤษทางวิชาการ

- ใช้ active voice เป็นหลัก ยกเว้นเมื่อ subject ไม่สำคัญ/ต้องการเน้น object
- หลีกเลี่ยง vague pronouns (this, that, these โดยไม่ระบุชัด)
- ใช้ signposting language (however, therefore, in contrast, building on)
- Precise verbs: argues, demonstrates, suggests, contends — แทน "talks about"

### Bilingual Writing

ถ้าเขียน 2 ภาษา:
- เขียนต้นฉบับภาษาเดียวก่อน ค่อยแปล (อย่าเขียนสองภาษาพร้อมกัน)
- ตรวจ technical terms ให้ตรงกันในทั้งสองภาษา
- บางคำที่แปลแล้วผิดความ → ใส่คำเดิมในวงเล็บ

## Anti-patterns ที่เจอบ่อยในงานเขียนศิลปะ

🚫 **"Art talk" without rigor** — ใช้คำหรูแต่ไม่มี argument (เช่น "ความงามที่หลั่งไหลซ่านไปทั่วผืนผ้าใบ")
✅ ใช้ภาษาที่ specific และ analyzable

🚫 **Overclaim ผ่าน hyperbole** — "งานนี้เปลี่ยนวงการศิลปะไทย" (ถ้าไม่มีหลักฐาน)
✅ ระบุ scale ของ contribution ให้พอดี

🚫 **Theory dropping** — ใส่ชื่อ Foucault, Derrida, Deleuze เพื่อดูฉลาด แต่ไม่ได้ใช้จริง
✅ ใช้ทฤษฎีเฉพาะที่จำเป็นและเชื่อมกับ argument

🚫 **Description-only** — บรรยายผลงานไปเรื่อยๆ โดยไม่วิเคราะห์
✅ ทุก description ต้องนำไปสู่ analysis/interpretation

🚫 **Cultural essentialism** — "ศิลปะไทย/ตะวันออกมีลักษณะ X" แบบเหมารวม
✅ ระบุเฉพาะ context, period, school

## AI Disclosure Statement

วารสารหลายแห่งบังคับ ตัวอย่าง template:

```
## AI Use Disclosure

This manuscript was prepared with assistance from [AI tool name and version]
for [specific tasks: e.g., literature search assistance, grammar checking,
formatting]. All research design, analysis, interpretation, and final 
writing decisions were made by the author(s). All references and quotations
have been independently verified against original sources. AI was not 
listed as an author.
```

## Workflow

```
1. รับบรีฟจากผู้ใช้ (หัวข้อ, ประเภท, target venue, materials)
2. เลือกโครงสร้าง (A/B/C/D)
3. สร้าง outline พร้อม section abstracts (200-300 คำ/section)
4. นำเสนอ outline ให้ผู้ใช้ confirm
5. เขียนทีละ section — confirm ก่อนไป section ถัดไป
6. เชื่อม transitions ระหว่าง section
7. Final pass: abstract refinement + title polish
8. ส่งต่อให้ arts-paper-reviewer skill (Stage 5 ของ pipeline)
```

## References

ดูเอกสารเพิ่มเติมใน `references/`:
- `paper_templates.md` — templates พร้อมใช้
- `journal_styles.md` — style guides ของวารสารยอดนิยม (TCI, Q1)
- `thai_academic_writing.md` — คู่มือเขียนภาษาไทยทางวิชาการ
- `exegesis_guide.md` — คู่มือเขียน exegesis
