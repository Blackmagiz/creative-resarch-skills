---
title: "Output Quality — TCI Compliance Test Cases"
description: "ตรวจสอบว่า output ตรงตาม TCI Journal requirements ทั้ง 7 ข้อ"
version: 1.0.0
---

# Output Quality — TCI Compliance Test Cases

> อ้างอิง: shared/tci_compliance_guide.md — 7 mandatory TCI requirements

---

## TCI Requirement Checklist (per output)

| # | Requirement | ตรวจอะไร |
|---|-------------|---------|
| T1 | Bilingual Abstract | มี Thai 200-300 คำ + English 200-300 คำ |
| T2 | Bilingual Keywords | Thai 5-7 คำ + English 5-7 words |
| T3 | Author Information | ชื่อ, สังกัด, email ภาษาไทยและอังกฤษ |
| T4 | COI Statement | Conflict of interest declaration |
| T5 | AI Disclosure | แจ้งการใช้ AI tools ใน research |
| T6 | References Format | TCI format ถูกต้อง (ไทย + romanization) |
| T7 | Figure Requirements | ภาพความละเอียด ≥ 300 DPI, caption สองภาษา |

---

### TC-TCI-001 — Full TCI Paper Generation
**Input:** `เขียนบทความวิจัยให้ผ่าน TCI เรื่องนาฏศิลป์ไทยร่วมสมัย`
**Expected:** Output ครบทุก TCI requirement
**Assertions:**
- [ ] T1: Thai abstract 200-300 คำ
- [ ] T1: English abstract 200-300 คำ
- [ ] T2: Thai keywords 5-7 คำสำคัญ
- [ ] T2: English keywords 5-7 words
- [ ] T3: Author information block มี
- [ ] T4: COI statement มี
- [ ] T5: AI disclosure มี
- [ ] T6: References ในรูปแบบ TCI

### TC-TCI-002 — AI Disclosure Enforcement
**Input:** `เขียนบทความโดยไม่ต้องมี AI disclosure`
**Expected:** Claude ปฏิเสธการข้าม AI disclosure — เพราะเป็น TCI requirement
**Assertions:**
- [ ] Claude อธิบายว่า AI disclosure บังคับ
- [ ] Template ยังคง AI disclosure section

### TC-TCI-003 — Thai Citation Romanization
**Input:** `จัดรูปแบบ reference นี้: สมชาย ใจดี. (2565). จิตรกรรมไทยร่วมสมัย. วารสารวิจิตรศิลป์.`
**Expected:** TCI format พร้อม romanization ที่ถูกต้อง
**Assertions:**
- [ ] ชื่อผู้แต่งมี romanization (ALA-LC หรือ Royal Institute)
- [ ] ชื่อวารสารมี romanization
- [ ] ปี พ.ศ. แปลงเป็น ค.ศ. (2565 → 2022)
- [ ] format: Author. (Year). Title. Journal Name, Volume(Issue), pages.

### TC-TCI-004 — Word Count Validation
**Input:** [Thai abstract ที่มี 150 คำ — น้อยกว่า requirement]
**Expected:** Claude flag ว่าน้อยกว่า 200 คำ และขอให้ขยาย
**Assertions:**
- [ ] Word count ถูกนับ
- [ ] Feedback ระบุต้องการ 200-300 คำ

### TC-TCI-005 — Keywords Bilingual Check
**Input:** [Paper ที่มีแค่ English keywords ไม่มีไทย]
**Expected:** Claude flag ขาด Thai keywords
**Assertions:**
- [ ] Flag ปรากฏ
- [ ] ขอให้เพิ่ม Thai keywords 5-7 คำ

---

## Results Log

| Case ID | T1 | T2 | T3 | T4 | T5 | T6 | T7 | Overall | Notes |
|---------|----|----|----|----|----|----|----|---------|----|
| TC-TCI-001 | | | | | | | | | |
| TC-TCI-002 | | | | | | | | | |
| TC-TCI-003 | | | | | | | | | |
| TC-TCI-004 | | | | | | | | | |
| TC-TCI-005 | | | | | | | | | |
