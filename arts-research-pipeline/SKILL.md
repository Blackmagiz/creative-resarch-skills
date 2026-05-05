---
name: arts-research-pipeline
description: ตัวจัดการ pipeline งานวิจัยเชิงสร้างสรรค์ทางศิลปะแบบครบวงจร 8 ขั้นตอน สำหรับนักวิจัยวิทยาลัยศิลปะ สื่อ และเทคโนโลยี (CAMT) ม.เชียงใหม่. Use when the user wants to start a complete arts research project from scratch, needs end-to-end orchestration of an arts research workflow, asks about "งานวิจัยศิลปะ", "วิจัยสร้างสรรค์", "creative research", "arts research pipeline", "วิจัยทัศนศิลป์/ดนตรี/นาฏศิลป์/ออกแบบ", or wants to coordinate multiple research stages (planning → literature review → methodology → creation/analysis → writing → review → revision → finalization). MUST trigger this skill whenever a user mentions starting an arts/creative research project, even if they don't specify the word "pipeline."
license: MIT
metadata:
  author: CAMT Research Support Unit
  version: 1.0.0
  institution: College of Arts, Media and Technology, Chiang Mai University
  language: Thai/English
---

# Arts Research Pipeline (CAMT Edition)

ตัวจัดการ workflow งานวิจัยเชิงสร้างสรรค์ทางศิลปะแบบครบวงจร ออกแบบเฉพาะสำหรับสายงานของวิทยาลัยศิลปะ สื่อ และเทคโนโลยี ม.เชียงใหม่ ครอบคลุมสาขา: ทัศนศิลป์, ออกแบบ, ดนตรี, การแสดง, ประยุกต์ศิลป์, ปรัชญาศิลป์, สุนทรียศาสตร์, ประวัติศาสตร์ศิลป์, โบราณคดี, สื่อศิลปะ, การออกแบบสื่อ, เรขศิลป์, ศิลปะการถ่ายภาพ, ศิลปศึกษา

## หลักคิดพื้นฐาน (Core Philosophy)

งานวิจัยทางศิลปะแตกต่างจากงานวิจัยสาย STEM ในประเด็นสำคัญ 5 ข้อ ที่ pipeline นี้ออกแบบมารองรับ

1. **Multiple ways of knowing** — ความรู้ทางศิลปะมาจากการปฏิบัติ (practice), การวิเคราะห์ (analysis), การตีความ (interpretation), และการไตร่ตรอง (reflection) ไม่ใช่แค่การพิสูจน์เชิงประจักษ์
2. **Practice as research** — งานสร้างสรรค์ (creative output) เป็นส่วนหนึ่งของผลลัพธ์ทางวิชาการได้ ไม่ใช่แค่ข้อมูลประกอบ
3. **Hermeneutic rigor** — ความเข้มงวดอยู่ที่การตีความที่มีหลักฐานและ self-reflexivity ไม่ใช่แค่ replicability
4. **Cultural situatedness** — งานต้องตระหนักบริบททางวัฒนธรรม โดยเฉพาะอย่างยิ่งบริบทไทย/ล้านนา/อาเซียน ไม่ใช่ใช้กรอบตะวันตกครอบทุกอย่าง
5. **Ethics of representation** — มีจริยธรรมในการนำเสนอภาพ บุคคล วัฒนธรรม และมรดกทางวัฒนธรรม

## Trigger Keywords

ภาษาไทย: งานวิจัยศิลปะ, วิจัยสร้างสรรค์, วิจัยเชิงสร้างสรรค์, วิจัยทางศิลปะ, pipeline งานวิจัย, จัดการงานวิจัย, เริ่มทำวิจัยศิลปะ, วิจัยทัศนศิลป์, วิจัยดนตรี, วิจัยนาฏศิลป์, วิจัยออกแบบ

English: arts research, creative research, artistic research, practice-based research, research pipeline, end-to-end research workflow

## Modes (โหมดการใช้งาน)

ผู้ใช้บอกโหมดได้ตอนเริ่มงาน ถ้าไม่ระบุ ใช้ `full` เป็นค่าตั้งต้น และถามผู้ใช้สั้นๆ ก่อนเริ่ม

| Mode | เมื่อไหร่ใช้ | Output หลัก |
|------|-------------|-------------|
| `full` | เริ่มงานวิจัยใหม่ตั้งแต่ต้น | เอกสารวิจัยฉบับสมบูรณ์ |
| `quick` | งานเร่งด่วน, abstract, conference paper | บทความสั้น/บทคัดย่อ |
| `practice-based` | งานวิจัยที่มีผลงานสร้างสรรค์เป็นแกน | exegesis + creative work documentation |
| `historical` | งานประวัติศาสตร์ศิลป์/โบราณคดี | บทความเชิงประวัติศาสตร์/บริบท |
| `theoretical` | ปรัชญาศิลป์, สุนทรียศาสตร์, art criticism | บทความเชิงทฤษฎี |
| `ethnographic` | ดนตรีชาติพันธุ์, performance studies, ศิลปะชุมชน | งานชาติพันธุ์วรรณนา |
| `educational` | ศิลปศึกษา, นวัตกรรมการสอน | งานวิจัยการศึกษา + เครื่องมือ |
| `proposal-only` | เขียนข้อเสนอโครงการ | proposal (ใช้ research-proposal skill เสริม) |

## Pipeline 8 ขั้นตอน

```
Stage 1: PLAN          → ปัญหาวิจัย, RQ, Methodology Blueprint
Stage 2: RESEARCH      → ทบทวนวรรณกรรม + บริบท
Stage 2.5: INTEGRITY   → ตรวจ AI hallucination + verify sources
Stage 3: METHOD/CREATE → ปฏิบัติ/วิเคราะห์/เก็บข้อมูล
Stage 4: WRITE         → ร่างบทความ
Stage 4.5: INTEGRITY   → ตรวจสอบ claim verification
Stage 5: REVIEW        → peer review จำลอง
Stage 6: REVISE        → ปรับปรุงตามคำวิจารณ์
Stage 7: VERIFY        → ตรวจสอบครั้งสุดท้าย
Stage 8: FINALIZE      → จัดรูปแบบเพื่อตีพิมพ์
```

### Stage 1: PLAN (วางแผน)

**Objective**: กำหนดปัญหาวิจัย, คำถามวิจัย, และ methodology blueprint

**สิ่งที่ต้องส่งมอบ (deliverables)**:
- Research question (RQ) ที่ชัดเจน 1-3 ข้อ
- ขอบเขตงาน (scope statement)
- Methodology blueprint — ระบุว่าจะใช้วิธีใด (formal analysis, ethnography, practice-based, hermeneutic, semiotic, archival, oral history, etc.)
- Theoretical framework เบื้องต้น
- Ethics consideration (ถ้าทำงานกับมนุษย์/ชุมชน/มรดกวัฒนธรรม → ต้องมี)

**Quality gate**: RQ ต้องตอบสามคำถามนี้ได้ — (1) ใหม่ในแง่ไหน (originality)? (2) สำคัญต่อใคร (significance)? (3) ทำได้จริงด้วยวิธีอะไร (feasibility)?

**Skills ที่อาจใช้ร่วม**: `aesthetics-philosophy` ถ้าเป็นงานทฤษฎี, `practice-based-research` ถ้าเป็น artistic research

### Stage 2: RESEARCH (ทบทวนวรรณกรรมและบริบท)

**Objective**: ทบทวนวรรณกรรม, แหล่งข้อมูลปฐมภูมิ, และบริบททางวัฒนธรรม

**Action**: เรียก `arts-deep-research` skill

**สิ่งที่ต้องส่งมอบ**:
- Literature matrix (ตารางสรุป 15-50 references ตามขอบเขต)
- Identified research gap
- Primary sources inventory (artworks, performances, archives, interviews)
- บริบททางวัฒนธรรม (cultural context) — โดยเฉพาะบริบทไทย/ล้านนา ถ้าเกี่ยวข้อง

**Quality gate**: ต้องมีอย่างน้อย — (1) แหล่งวิชาการต่างประเทศที่ peer-reviewed, (2) แหล่งภาษาไทย/TCI ถ้ามี, (3) primary sources ที่จับต้องได้

### Stage 2.5: INTEGRITY GATE 1 (ตรวจสอบความถูกต้อง)

**Critical**: AI มีแนวโน้ม hallucinate references และข้อมูลทางประวัติศาสตร์ ขั้นตอนนี้บังคับ ห้ามข้าม

**Checklist 7 ข้อ**:
1. ✅ ทุก reference ตรวจสอบได้จริง (ไม่ใช่ AI สร้างขึ้น) — ตรวจกับ Google Scholar, JSTOR, TCI
2. ✅ ผู้เขียน, ปี, ชื่อบทความ ตรงกับต้นฉบับ
3. ✅ คำพูดอ้างอิง (quotes) ตรงกับต้นฉบับเป๊ะ ไม่ paraphrase ปลอมเป็น quote
4. ✅ ข้อมูลศิลปิน/ผลงาน — ปี, สถานที่, สื่อ, ขนาด ตรงกับแหล่งที่เชื่อถือได้
5. ✅ ข้อมูลทางประวัติศาสตร์ — ตรวจกับแหล่งทุติยภูมิที่เป็น authoritative
6. ✅ การแปล (ถ้ามี) — ระบุผู้แปลและตรวจสอบความถูกต้อง
7. ✅ ภาพ/figure — มีลิขสิทธิ์ใช้งานได้, มี caption ครบถ้วน

ถ้าผ่านไม่ครบ ห้ามไป Stage 3

### Stage 3: METHOD/CREATE (วิธีวิจัย/การสร้างสรรค์)

**Objective**: ดำเนินการตามวิธีวิจัย — ปฏิบัติ, วิเคราะห์, หรือเก็บข้อมูลภาคสนาม

**ทางเลือกตามประเภทงาน**:

**A) Practice-based** → ใช้ `practice-based-research` skill
- บันทึก creative process (process journal, sketches, recordings)
- Critical reflection ขณะปฏิบัติ
- Documentation ของผลงาน

**B) Visual analysis** → ใช้ `visual-analysis` skill
- Formal analysis (line, color, composition, medium)
- Iconography (Panofsky's three levels)
- Semiotic analysis
- Comparative analysis

**C) Performance/Music research** → ใช้ `performance-arts-research` skill
- Performance analysis
- Music analysis (Schenkerian, Schenker, set theory, semiotic)
- Notation analysis (ดนตรีไทย/นาฏศิลป์ไทย รวม notation system เฉพาะ)
- Ethnomusicological methods

**D) Historical/Archaeological** → ใช้ `art-history-archaeology` skill
- Archival research
- Provenance research
- Material/stylistic analysis
- Dating techniques

**E) Theoretical/Philosophical** → ใช้ `aesthetics-philosophy` skill
- Philosophical argumentation
- Conceptual analysis
- Critical theory application

**F) Educational research** → ใช้กรอบ design-based research, action research, หรือ phenomenological research ร่วมกับการวิเคราะห์ผู้เรียน

**Quality gate**: ข้อมูล/ผลงานที่ได้มาตรวจสอบได้, มี documentation ครบ, จริยธรรมการวิจัยผ่าน (ถ้าเกี่ยวข้องกับมนุษย์ — IRB)

### Stage 4: WRITE (เขียน)

**Objective**: ร่างบทความ/วิทยานิพนธ์

**Action**: เรียก `arts-paper-writer` skill

**โครงสร้างมาตรฐานสำหรับงานศิลปะวิจัย** (ปรับตามประเภท):

```
Traditional Academic:
1. Abstract (200-300 คำ)
2. Introduction (ปัญหา + RQ + scope + significance)
3. Literature Review / Conceptual Framework
4. Methodology
5. Analysis / Findings / Creative Work Documentation
6. Discussion (เชื่อมกลับ literature)
7. Conclusion + Future Research
8. References
9. Appendices (ภาพผลงาน, transcript, scores ฯลฯ)

Practice-based (Exegesis Format):
1. Abstract
2. Introduction (research question + creative work overview)
3. Contextual Review (artists, theories ที่เกี่ยวข้อง)
4. Methodology of Practice
5. The Work (creative output documentation)
6. Critical Reflection
7. Contribution to Knowledge
8. Conclusion
9. References
10. Documentation Appendix (high-res images, video links, scores)
```

**Quality gate**:
- ทุก claim มี evidence support
- ทุก quote มี citation ตรงตำแหน่ง
- โครงสร้างย่อหน้ามี topic sentence ชัดเจน
- ภาษาไม่กำกวม

### Stage 4.5: INTEGRITY GATE 2

ตรวจสอบ post-write:
1. ทุก citation ในเนื้อหา → มีอยู่ใน reference list
2. ทุก reference ใน list → ถูกอ้างในเนื้อหา
3. ไม่มี claim ที่เป็น "common knowledge" แบบเหมา (เช่น "นักวิชาการส่วนใหญ่เห็นด้วยว่า...") โดยไม่มี citation
4. รูปภาพมีลิขสิทธิ์/permission ครบ
5. ภาษาไม่ลำเอียง (cultural/gender bias)

### Stage 5: REVIEW (ทบทวนเสมือนวารสาร)

**Action**: เรียก `arts-paper-reviewer` skill

**ทีม reviewer 5 คน**:
- Editor-in-Chief (EIC) — ตรวจ scope, fit, significance
- R1: Methodology reviewer — ตรวจวิธีวิจัย
- R2: Domain expert — ตรวจเนื้อหาเฉพาะสาขา
- R3: Cross-disciplinary reviewer — ตรวจการเชื่อมโยงข้ามสาขา
- Devil's Advocate — โจมตี argument หลัก

**Output**: Editorial Decision + Revision Roadmap

### Stage 6: REVISE (ปรับปรุง)

ทำตาม revision roadmap จาก Stage 5
- Major revisions ทำก่อน minor
- ตอบทุก reviewer comment ใน "response to reviewers" letter
- ถ้าไม่เห็นด้วยกับ reviewer ต้องชี้แจงด้วยเหตุผลและหลักฐาน

### Stage 7: VERIFY (ตรวจสอบครั้งสุดท้าย)

ทำซ้ำ Integrity Gates 1+2 หลัง revision
+ ตรวจสอบรูปแบบ citation ตามที่วารสารต้องการ (ใช้ `arts-citation-formatter` skill)

### Stage 8: FINALIZE (จัดรูปแบบสุดท้าย)

- จัดรูปแบบตาม journal template (TCI tier 1/2, Scopus, Q1-Q4)
- ตรวจคำผิด (Thai + English)
- จัดทำ AI disclosure statement (สำคัญสำหรับวารสารปัจจุบัน)
- เตรียม submission package: cover letter, manuscript, figures, supplementary, conflict of interest statement

## วารสารเป้าหมายที่นักวิจัย CAMT มักส่ง

**ในประเทศ (TCI)**:
- วารสารวิชาการศิลปะ การออกแบบ และสถาปัตยกรรม
- วารสารศิลปกรรมศาสตร์ จุฬาฯ
- วารสารหน้าจั่ว (สาขาสถาปัตยกรรม/ออกแบบ)
- วารสารวิจัยและพัฒนา มหาวิทยาลัยราชภัฏ (สำหรับงานเชิงประยุกต์)
- วารสารศิลปวัฒนธรรม

**ต่างประเทศ (ตัวอย่าง Q1-Q2)**:
- *Leonardo* (MIT Press) — สื่อศิลปะ, art-science
- *International Journal of Art & Design Education*
- *Design Studies*
- *Journal of Visual Culture*
- *Art History* (Wiley)
- *Music Theory Online*
- *Performance Research*
- *Asian Theatre Journal*
- *Journal of Southeast Asian Studies*

## ข้อควรระวังเฉพาะงานศิลปะ (Anti-patterns)

🚫 อย่าใช้ AI generate ชื่อศิลปิน/ผลงาน/ปีโดยไม่ตรวจสอบ — มี hallucination สูง
🚫 อย่า paraphrase ความคิดของนักทฤษฎีโดยไม่อ่านงานต้นฉบับ — ความหมายเพี้ยนได้
🚫 อย่าใช้กรอบทฤษฎีตะวันตกตัดสินงานศิลปะไทย/อาเซียนโดยไม่พิจารณาบริบท
🚫 อย่านำภาพศิลปะมาใช้โดยไม่เช็คลิขสิทธิ์ — โดยเฉพาะภาพ contemporary
🚫 อย่าเรียก "งานสร้างสรรค์" ว่า "creative work" แค่เพราะมันสวย — ต้องมี research contribution

## เริ่มต้นใช้งาน

ถ้า user เพิ่งเริ่มและยังไม่ชัดเจน ให้ถามคำถามเหล่านี้ก่อนเริ่ม pipeline:

1. หัวข้อวิจัยคืออะไร (อย่างน้อย 1 ประโยค)?
2. สาขา/สาขาย่อยใด (เลือกจาก 14 สาขาที่ระบุข้างต้น)?
3. ประเภทงาน — ทฤษฎี, ปฏิบัติ, ประวัติศาสตร์, ภาคสนาม, ปฏิบัติการ?
4. มีผลงานสร้างสรรค์ประกอบหรือไม่ (ถ้ามี → practice-based mode)?
5. เป้าหมายตีพิมพ์ที่ไหน (TCI, Scopus, conference, วิทยานิพนธ์)?
6. timeline?

## References

- ARS Pipeline (Imbad0202/academic-research-skills) — ต้นแบบโครงสร้าง pipeline
- Borgdorff, H. (2012). *The Conflict of the Faculties: Perspectives on Artistic Research and Academia.*
- Smith, H. & Dean, R. T. (2009). *Practice-led Research, Research-led Practice in the Creative Arts.*
- Sullivan, G. (2010). *Art Practice as Research.*
- ดูเอกสารเพิ่มเติมใน `references/` directory
