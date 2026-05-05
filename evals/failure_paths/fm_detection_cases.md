---
title: "Failure Paths — FM Detection Test Cases"
description: "ตรวจสอบว่า Failure Modes FM-A ถึง FM-G ถูก detect และรายงานอย่างถูกต้อง"
version: 1.0.0
---

# Failure Paths — FM Detection Test Cases

> อ้างอิง: shared/cross_agent_quality_definitions.md — FM-A ถึง FM-G

---

## Failure Mode Reference

| Code | Name | คำอธิบาย |
|------|------|---------|
| FM-A | Decorative Theory | ใช้ทฤษฎีเพื่อ "ประดับ" ไม่ได้วิเคราะห์จริง |
| FM-B | Catalog Description | บรรยายผลงานอย่างเดียว ไม่วิเคราะห์เชิงวิจัย |
| FM-C | Thai Cultural Essentialism | อ้าง "ความเป็นไทย" เป็น universal ไม่อิงทฤษฎี |
| FM-D | Western Frame Imposition | ใช้ framework ตะวันตกกับบริบทไทย/เอเชียโดยไม่ปรับ |
| FM-E | Unverified References | อ้างอิงที่ verify ไม่ได้ หรือ hallucinated |
| FM-F | Practice-Research Confusion | ไม่แยก creative practice กับ research methodology |
| FM-G | Missing Cultural Sensitivity | ขาดความตระหนักทางวัฒนธรรมในการวิเคราะห์ |

---

### FP-FM-A-001 — Decorative Theory Detection
**Input (excerpt):**
```
การวิจัยนี้ใช้ทฤษฎีหลังสมัยใหม่ (postmodernism) เป็นกรอบการวิจัย
ผลงานชุด "แสงสว่าง" ใช้สีและพื้นผิวที่หลากหลาย แสดงออกถึงความรู้สึก
ของศิลปิน ซึ่งสะท้อนความเป็นไทย
[ทฤษฎีถูกกล่าวถึงในประโยคแรกแล้วหายไป — ไม่ปรากฏในการวิเคราะห์]
```
**Expected:** FM-A detected — ทฤษฎีถูกกล่าวถึงแต่ไม่ได้ใช้วิเคราะห์
**Assertions:**
- [ ] FM-A flag ปรากฏ
- [ ] Recovery protocol เสนอ: ให้ระบุว่า concept ใดของทฤษฎีที่ใช้วิเคราะห์อะไร
- [ ] Score ใน WQC: Anti-Pattern A ≥ 2

### FP-FM-B-001 — Catalog Description Detection
**Input (excerpt):**
```
ผลงาน "ท้องฟ้า" เป็นภาพวาดสีน้ำมันขนาด 120x180 ซม. ใช้สีฟ้าและขาว
มีแสงสว่างจากมุมขวาบน พื้นผิวหนาบางสลับกัน ตัวภาพแสดงให้เห็น
ก้อนเมฆในยามเช้า ศิลปินใช้พู่กันขนาดใหญ่
```
**Expected:** FM-B detected — บรรยายอย่างเดียวไม่วิเคราะห์
**Assertions:**
- [ ] FM-B flag ปรากฏ
- [ ] Recovery: ขอให้เพิ่มการวิเคราะห์ว่าเทคนิคนี้ "สื่อความหมาย" หรือ "สร้างผล" อะไร
- [ ] Score: Anti-Pattern B ≥ 2

### FP-FM-C-001 — Thai Cultural Essentialism Detection
**Input (excerpt):**
```
ดนตรีไทยมีความอ่อนโยนและความละเมียดละไมโดยธรรมชาติ
ซึ่งแตกต่างจากดนตรีตะวันตกที่รุนแรงและตรงไปตรงมา
คุณสมบัตินี้สะท้อนจิตวิญญาณของคนไทยที่มีมาแต่โบราณ
```
**Expected:** FM-C detected — อ้าง "ความเป็นไทย" โดยไม่มีฐานทฤษฎีหรือหลักฐาน
**Assertions:**
- [ ] FM-C flag ปรากฏ
- [ ] Recovery: ขอให้อ้างอิงนักวิชาการที่ศึกษาเรื่องนี้จริง
- [ ] ชี้ว่า essentialism อาจเป็น ethnocentric

### FP-FM-D-001 — Western Frame Imposition Detection
**Input (excerpt):**
```
วิเคราะห์นาฏศิลป์รำโนราโดยใช้ Laban Movement Analysis (LMA)
ซึ่งพัฒนาโดย Rudolf Laban สำหรับ European concert dance
โดยไม่มีการปรับหรืออภิปรายข้อจำกัดของ framework นี้
```
**Expected:** FM-D detected — LMA ใช้กับ Thai performance โดยไม่ adapt
**Assertions:**
- [ ] FM-D flag ปรากฏ
- [ ] Recovery: เสนอ Thai/ASEAN framework เพิ่มเติม (เช่น นาฏยศาสตร์ไทย)
- [ ] แนะนำให้ discuss ข้อจำกัดของ Western framework

### FP-FM-E-001 — Unverified Reference Detection
**Input (excerpt):**
```
References:
Smith, J. (2019). Thai Contemporary Art Movements. Journal of Asian Arts, 15(2), 45-62.
[DOI: 10.1234/jaa.2019.15.2.45 — ไม่มีจริง]
```
**Expected:** FM-E detected — DOI ไม่มีจริง
**Assertions:**
- [ ] FM-E flag หรือ "verification failed" ปรากฏ
- [ ] Reference ถูก mark เป็น unverified
- [ ] ไม่รวมใน final bibliography โดยไม่ verify

### FP-FM-F-001 — Practice-Research Confusion Detection
**Input (excerpt):**
```
Methodology: ฉันสร้างภาพวาด 10 ชิ้นเป็น methodology ของการวิจัย
กระบวนการสร้างสรรค์คือการทดลองใช้สีต่างๆ และดูว่าผลออกมาอย่างไร
```
**Expected:** FM-F detected — ไม่ชัดว่า creative work เป็น data/method/output
**Assertions:**
- [ ] FM-F flag ปรากฏ
- [ ] Recovery: ถามว่าผลงานคือ data, method, หรือ research output
- [ ] เสนอ practice-based framework ที่เหมาะสม

### FP-FM-G-001 — Cultural Sensitivity Detection
**Input (excerpt):**
```
การแสดงโขนซึ่งแต่เดิมสงวนไว้สำหรับราชสำนัก
ปัจจุบันถูกทำให้เป็น entertainment ทั่วไป
เหมือนกับที่ตะวันตกทำกับ opera
```
**Expected:** FM-G detected — เปรียบโขนกับ opera โดยไม่ตระหนักถึงความต่าง
**Assertions:**
- [ ] FM-G flag ปรากฏ
- [ ] Recovery: ขอให้ discuss ความหมายทางวัฒนธรรมและ context ของโขน

---

## Results Log

| Case ID | FM Code | Detected? | Recovery Offered? | Score Impact | Notes |
|---------|---------|-----------|-------------------|--------------|-------|
| FP-FM-A-001 | FM-A | | | | |
| FP-FM-B-001 | FM-B | | | | |
| FP-FM-C-001 | FM-C | | | | |
| FP-FM-D-001 | FM-D | | | | |
| FP-FM-E-001 | FM-E | | | | |
| FP-FM-F-001 | FM-F | | | | |
| FP-FM-G-001 | FM-G | | | | |
