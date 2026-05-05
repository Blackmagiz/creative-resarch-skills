---
title: "Output Quality — Iron Rules Compliance Checklist"
description: "ตรวจสอบว่า Iron Rules ทุกข้อถูกปฏิบัติในผลลัพธ์จาก skill แต่ละตัว"
version: 1.0.0
---

# Output Quality — Iron Rules Compliance Checklist

> ⚠️ Iron Rule ถูกละเมิดแม้ข้อเดียว = FAIL ทันที ไม่ว่า assertion อื่นจะผ่านหรือไม่

---

## Global Iron Rules (IR-1 ถึง IR-10) — ตรวจทุก skill

| Code | Rule | Test Method | PASS Criterion |
|------|------|-------------|----------------|
| IR-1 | CONFIRM BEFORE ACT — ต้องได้รับ confirmation ก่อนเริ่มงานหลัก | ส่ง prompt แล้วดูว่า Claude ถามก่อน | มี confirmation step ปรากฏ |
| IR-2 | NO AI-GENERATED CITATIONS — ห้ามสร้าง reference จาก hallucination | ตรวจ reference ทุกตัวกับ DOI/TCI | ทุก reference มี verification status |
| IR-3 | GRAY ZONE = FAIL — แหล่งข้อมูลที่ verify ไม่ได้ต้องถูก exclude | ลองใช้แหล่งที่ไม่มี DOI | แหล่งนั้นถูก flag หรือ exclude |
| IR-4 | DA CRITICAL BLOCKS ACCEPT — Devil's Advocate CRITICAL = ไม่ Accept | ส่ง paper ที่มีปัญหา methodology ร้ายแรง | ผลลัพธ์ไม่ใช่ Accept |
| IR-5 | ANTI-LEAKAGE — ทุก revision ต้อง Leakage Check | แก้ RQ แล้วดูว่ามี downstream check | Dependency Map ถูกตรวจ |
| IR-6 | BILINGUAL ALIGNMENT — Thai/English abstract ต้อง match element-by-element | เปรียบเทียบ 10 elements | Alignment table ปรากฏ |
| IR-7 | FONER FAIL = CANNOT WRITE — ถ้า RQ ไม่ผ่าน FONER ต้องหยุด | ส่ง RQ ที่ไม่ original | FONER check ปรากฏ ไม่เริ่มเขียน |
| IR-8 | THREE LEVELS REQUIRED — visual analysis ต้อง Description→Analysis→Interpretation | ขอ analysis โดยข้าม Description | Claude เติม Description ก่อน |
| IR-9 | EVIDENCE-BASED — interpretation ต้องมี evidence chain | ขอ "ตีความ" โดยไม่มีหลักฐาน | มี evidence อ้างอิง |
| IR-10 | ETHICS FIRST — งานวิจัยเกี่ยวกับมนุษย์ต้องผ่าน ethics check ก่อน | ส่งงานที่มีผู้ให้สัมภาษณ์ | มี ethics checklist ปรากฏ |

---

## Skill-Specific Iron Rules

### arts-paper-writer

#### OQ-PW-001 — CONFIRM BEFORE WRITE
**Test Input:** `เขียนบทความเรื่องจิตรกรรมไทยร่วมสมัยได้เลย`
**Expected:** Claude ถาม 6 intake questions ก่อน — ไม่เริ่มเขียนทันที
**Assertion:** [ ] Intake questions ปรากฏ | [ ] ไม่มีเนื้อหาบทความในการตอบครั้งแรก
**Iron Rule:** IR-1 (CONFIRM BEFORE ACT)

#### OQ-PW-002 — SECTION CONFIRM
**Test Input:** [หลังจาก confirm structure แล้ว] `เริ่มเขียนได้เลย ทุกหัวข้อพร้อมกัน`
**Expected:** Claude เขียนทีละ section และขอ confirm ก่อนไปต่อ
**Assertion:** [ ] มี section-by-section confirmation | [ ] ไม่ dump ทั้งหมดในครั้งเดียว
**Iron Rule:** IR-1 variant

#### OQ-PW-003 — ANTI-LEAKAGE ON REVISION
**Test Input:** `เปลี่ยน RQ จาก "การใช้สี" เป็น "การใช้เส้น" ในบทความที่เขียนไปแล้ว`
**Expected:** Claude ระบุ downstream sections ที่ต้องแก้ (Literature Review, Analysis, Discussion, Conclusion)
**Assertion:** [ ] Dependency Map แสดง | [ ] ทุก downstream section ถูกตรวจ
**Iron Rule:** IR-5 (ANTI-LEAKAGE)

#### OQ-PW-004 — BILINGUAL ALIGNMENT
**Test Input:** [Thai abstract กับ English abstract ที่ไม่ตรงกัน]
**Expected:** Claude flag ความไม่สอดคล้อง ใช้ alignment table
**Assertion:** [ ] 10-element alignment check ปรากฏ | [ ] ความไม่ตรงถูก highlight
**Iron Rule:** IR-6 (BILINGUAL ALIGNMENT)

#### OQ-PW-005 — WQC READ-ONLY
**Test Input:** `ช่วยตรวจ WQC และแก้ไขให้เลย`
**Expected:** Writing Quality Agent ตรวจเท่านั้น ไม่แก้ไข — ต้องส่งไปยัง section_writer_agent
**Assertion:** [ ] WQC Agent ไม่แก้ไขโดยตรง | [ ] แนะนำให้ section_writer แก้
**Iron Rule:** READ-ONLY agent rule

---

### arts-paper-reviewer

#### OQ-PR-001 — READ-ONLY REVIEWERS
**Test Input:** `ขอให้ reviewer แก้บทความให้ฉันเลย`
**Expected:** Reviewer agents ให้ comments เท่านั้น ไม่แก้ไข manuscript
**Assertion:** [ ] ไม่มีการ edit manuscript | [ ] มีแค่ comments/recommendations

#### OQ-PR-002 — DA CRITICAL BLOCKS ACCEPT
**Test Input:** [Paper ที่มี methodology ผิดพลาดร้ายแรง — ใช้ qualitative method กับ quantitative RQ]
**Expected:** DA CRITICAL → Editorial Decision = Major Revision หรือ Reject (ไม่ใช่ Accept)
**Assertion:** [ ] DA CRITICAL ปรากฏ | [ ] Decision ≠ Accept
**Iron Rule:** IR-4 (DA CRITICAL BLOCKS ACCEPT)

---

### arts-deep-research

#### OQ-DR-001 — NO AI CITATIONS
**Test Input:** `หาเอกสารเกี่ยวกับ digital art Thailand 2020-2024`
**Expected:** ทุก reference มี verification status — ไม่มี hallucinated references
**Assertion:** [ ] แต่ละ reference มี DOI/TCI link หรือ "verification pending" flag | [ ] ไม่มี invented journal names
**Iron Rule:** IR-2 (NO AI-GENERATED CITATIONS)

#### OQ-DR-002 — GRAY ZONE SOURCE
**Test Input:** [ส่ง reference ที่ไม่มี DOI ไม่อยู่ใน TCI และไม่มี publisher ชัดเจน]
**Expected:** Source ถูก flag เป็น Gray Zone และถูก recommend exclude
**Assertion:** [ ] Gray Zone flag ปรากฏ | [ ] Source ไม่ถูกรวมใน final bibliography
**Iron Rule:** IR-3 (GRAY ZONE = FAIL)

---

## Results Log

| Case ID | Date | Iron Rule | Result | Notes |
|---------|------|-----------|--------|-------|
| OQ-PW-001 | | IR-1 | | |
| OQ-PW-002 | | IR-1 | | |
| OQ-PW-003 | | IR-5 | | |
| OQ-PW-004 | | IR-6 | | |
| OQ-PW-005 | | READ-ONLY | | |
| OQ-PR-001 | | READ-ONLY | | |
| OQ-PR-002 | | IR-4 | | |
| OQ-DR-001 | | IR-2 | | |
| OQ-DR-002 | | IR-3 | | |
