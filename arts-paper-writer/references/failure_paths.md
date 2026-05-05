---
name: failure_paths
purpose: 8 failure scenarios ใน arts-paper-writer + recovery strategies
parent_skill: arts-paper-writer
version: 2.0.0
---

# Failure Paths — Arts Paper Writer

## Overview

failure paths คือสถานการณ์ที่กระบวนการเขียนสะดุดหรือล้มเหลว แต่ละ path มี trigger condition และ recovery strategy

---

## Failure Path Table

| # | ชื่อ | Trigger | ผลกระทบ | Recovery |
|---|-----|---------|---------|---------|
| F1 | RQ Undefined | เริ่มเขียน full mode โดยไม่มี RQ ชัดเจน | บทความไม่มีทิศทาง | หยุด → ส่งไป arts-deep-research Socratic mode |
| F2 | Empty Literature | Literature review บาง (<10 sources, ขาด Thai) | Lit review อ่อนแอ, gap claim ไม่น่าเชื่อ | หยุด → ส่งไป arts-deep-research full mode |
| F3 | Theory-Practice Mismatch | ทฤษฎีที่เลือกไม่เหมาะกับ method หรือ data | Analysis ขาดความสอดคล้อง | theory-focus review → เลือก theory ใหม่ |
| F4 | Structure Mismatch | เลือก Structure A สำหรับ practice-based research | ผลงานสร้างสรรค์ไม่ถูก document ครบ | switch to Structure B (Exegesis) |
| F5 | Revision Leak | แก้ comment แล้วทำให้ section อื่นขัดแย้ง | Manuscript inconsistent | รัน anti_leakage_protocol → แก้ downstream |
| F6 | Bilingual Mismatch | Thai abstract ≠ English abstract | ไม่ผ่าน TCI requirements | bilingual_abstract_agent → re-align |
| F7 | Citation Format Chaos | References ผสม format หลาย style | ไม่ผ่าน journal submission | format-convert mode → standardize |
| F8 | Writing Quality FAIL | WQC score ≤20 หรือ single dimension score = 3 | ไม่พร้อม submit | แก้ตาม WQC report → re-check |

---

## Detailed Recovery Protocols

### F1: RQ Undefined

**Detection**: intake_planner_agent ถาม RQ แต่ผู้ใช้ให้คำตอบที่กว้างมาก เช่น "ผมจะศึกษาเรื่องศิลปะไทย"

**Recovery**:
```
1. หยุดกระบวนการเขียนทันที
2. แจ้งผู้ใช้: "RQ ยังไม่ชัดเพียงพอที่จะเริ่มเขียน ขอแนะนำให้ใช้ 
   arts-deep-research → Socratic mode ก่อน"
3. ถ้าผู้ใช้ต้องการเขียนต่อแม้ RQ ยังไม่ชัด:
   - สร้าง Paper Plan Card ด้วย placeholder RQ
   - Mark ว่า "RQ: PLACEHOLDER — MUST CONFIRM BEFORE ANALYSIS SECTION"
   - เขียนได้ถึงแค่ Introduction และ Lit Review
   - หยุดที่ Methodology จนกว่า RQ จะ confirmed
```

---

### F2: Empty Literature

**Detection**: ผู้ใช้ไม่มี literature review หรือมีน้อยกว่า 10 sources; ไม่มี Thai-language sources สำหรับงาน Thai context

**Recovery**:
```
1. แจ้งผู้ใช้ว่า literature ยังบาง
2. ระบุว่าขาดประเภทไหน (international / Thai / primary sources)
3. แนะนำ arts-deep-research → full mode
4. ถ้าผู้ใช้ต้องการเขียน Lit Review ด้วยสิ่งที่มี:
   - เขียนด้วย sources ที่มี
   - Mark section ด้วย: "⚠️ Literature ยังไม่ครบ — ต้องเพิ่มก่อน submit"
   - ระบุ gaps ที่ชัดเจน
```

---

### F3: Theory-Practice Mismatch

**Detection**: writing_quality_agent Pattern C (Decorative Theory) score ≥ 2 หรือ methodology section ระบุ method แต่ analysis section ไม่ได้ใช้ method นั้น

**Recovery**:
```
1. ระบุ theories ที่ "decorative" (mention แต่ไม่ใช้)
2. ตัดสินใจ: ใช้ทฤษฎีนั้นจริงๆ หรือตัดออก
   Option A: ใช้จริง → เขียน analysis sections ใหม่โดยใช้ theory framework
   Option B: ตัดออก → ลบ theory จาก Lit Review / Framework
3. ถ้าไม่แน่ใจว่าทฤษฎีไหนเหมาะ → arts-paper-reviewer → theory-focus mode
```

---

### F4: Structure Mismatch

**Detection**: ผู้ใช้เลือก traditional paper structure แต่งาน involve creative work ที่เป็น core research method

**Recovery**:
```
1. แจ้งผู้ใช้ว่า Structure A ไม่เหมาะกับ practice-based work
2. แนะนำ switch to Structure B (Exegesis)
3. Map sections ที่เขียนไปแล้วไปยัง Exegesis structure:
   Introduction → Introduction (เพิ่ม why practice-based)
   Lit Review → Contextual Review (ปรับ focus)
   Methodology → Methodology of Practice (เพิ่ม reflexivity)
   Analysis → The Work + Critical Reflection (expand มาก)
4. ส่ง exegesis_agent ทำต่อ
```

---

### F5: Revision Leak

**Detection**: anti_leakage_protocol พบ downstream sections ที่ไม่ consistent หลัง revision

**Recovery**:
```
1. รัน Dependency Map จาก anti_leakage_protocol.md
2. List ทุก section ที่ต้องแก้
3. แก้ทีละ section ตาม dependency order (upstream → downstream)
4. รัน anti_leakage_protocol อีกครั้งหลังแก้ทุก section
5. รัน writing_quality_agent → Pattern G check
```

---

### F6: Bilingual Mismatch

**Detection**: bilingual_abstract_agent alignment check พบ ≥1 element ไม่ match

**Recovery**:
```
1. ระบุ element ที่ไม่ match (จาก alignment table)
2. ตัดสินใจว่า version ไหน "correct" (Thai หรือ English)
3. แก้อีก version ให้ตรงกัน
4. รัน alignment check ใหม่
5. ห้าม add information ใหม่ระหว่าง fix — แก้ให้ match เท่านั้น
```

---

### F7: Citation Format Chaos

**Detection**: writing_quality_agent Dimension 4 (Citation Quality) พบ format mixed

**Recovery**:
```
1. ระบุ target citation style (จาก journal requirements)
2. ใช้ format-convert mode
3. ตรวจทุก in-text citation: (Author, Year) vs (Author Year) vs footnote
4. ตรวจ References list: APA 7 vs Chicago 17 vs TCI
5. ตรวจ consistency ของ DOI/URL format
```

---

### F8: Writing Quality FAIL

**Detection**: WQC total score ≤20 หรือ single dimension score = 3

**Recovery**:
```
1. เรียง issues ตาม severity (score 3 ก่อน)
2. สำหรับแต่ละ issue:
   - ระบุ location (section, paragraph)
   - section_writer_agent เขียน replacement passage
   - ตรวจ anti_leakage_protocol (ถ้า revision)
3. รัน writing_quality_agent อีกครั้ง
4. ทำซ้ำจนกว่า WQC score ≥21 และไม่มี single dimension = 3
```
