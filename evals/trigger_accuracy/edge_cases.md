---
title: "Trigger Accuracy — Edge Cases"
description: "กรณีกำกวม — prompt อาจ trigger หลาย skill หรือยากจะตัดสิน"
version: 1.0.0
---

# Trigger Accuracy — Edge Cases

> สำหรับ edge cases: ระบุ **Primary Skill** (ควร trigger ก่อน) และ **Secondary Skill** (อาจถูก invoke ต่อ)

---

### TE-001 — Research vs. Citation
**Input:** `หาแหล่งอ้างอิงเกี่ยวกับ Lanna art และจัดรูปแบบให้เป็น APA`
**Primary Skill:** arts-deep-research (หาก่อน)
**Secondary Skill:** arts-citation-formatter (จัดรูปแบบทีหลัง)
**Expected Flow:** deep-research → handoff → citation-formatter
**Assertion:** [ ] Handoff schema "Citation Package" ถูกใช้

### TE-002 — Write vs. Review
**Input:** `ช่วยเขียนบทความและตรวจสอบด้วย`
**Primary Skill:** arts-paper-writer (เขียนก่อน)
**Secondary Skill:** arts-paper-reviewer (ตรวจหลัง)
**Expected Flow:** paper-writer → Review Package → paper-reviewer
**Assertion:** [ ] Handoff schema "Review Package" ถูกใช้

### TE-003 — Practice-based vs. Visual Analysis
**Input:** `ฉันสร้างภาพวาดเป็นส่วนหนึ่งของวิจัย และต้องการวิเคราะห์ภาพนั้น`
**Primary Skill:** practice-based-research (framework ก่อน)
**Secondary Skill:** visual-analysis (วิเคราะห์ภาพผลงาน)
**Decision Criterion:** ถ้าโจทย์คือ "วิจัยเชิงปฏิบัติ" → practice-based; ถ้าคือ "วิเคราะห์ภาพเดียว" → visual-analysis
**Assertion:** [ ] Claude ถามเพื่อ clarify ก่อน trigger

### TE-004 — Pipeline vs. Single Skill
**Input:** `อยากเขียนบทความวิจัยตั้งแต่ต้น มีงานวิจัยสร้างสรรค์ด้วย`
**Primary Skill:** arts-research-pipeline (ครบวงจร)
**Expected:** Pipeline trigger ไม่ใช่แยก paper-writer
**Assertion:** [ ] arts-research-pipeline ถูกเลือก ไม่ใช่ arts-paper-writer โดยตรง

### TE-005 — Short Ambiguous Prompt
**Input:** `review`
**Expected:** Claude ถามว่า review อะไร — ไม่ trigger ทันที
**Assertion:** [ ] ถาม clarifying question ก่อน trigger

### TE-006 — Citation Format vs. Research Quality
**Input:** `ตรวจสอบว่า reference list ของฉันถูกต้องไหม`
**Primary Skill:** arts-citation-formatter (format verification)
**Secondary Skill:** arts-paper-reviewer (อาจ check citation quality ใน review)
**Decision:** ถ้าแค่ "format" → citation-formatter; ถ้า "quality + format" ในบริบท review → paper-reviewer
**Assertion:** [ ] Claude เลือกตาม context ที่ชัดเจนกว่า

### TE-007 — Thai Language Context
**Input:** `ทำ bibliography`
**Expected Skill:** arts-citation-formatter
**Risk:** ภาษาไทยสั้นมาก อาจไม่ trigger
**Assertion:** [ ] arts-citation-formatter ถูก trigger แม้ prompt สั้น

### TE-008 — English Prompt for Thai Context
**Input:** `I need to write a research paper about traditional Thai pottery`
**Expected Skill:** arts-paper-writer
**Note:** prompt เป็น English แต่หัวข้อไทย — ควร trigger arts-paper-writer ไม่ใช่ generic writing
**Assertion:** [ ] TCI + Thai journal awareness ปรากฏในผลลัพธ์

---

## Decision Framework สำหรับ Edge Cases

```
ถ้า prompt กล่าวถึง "วิจัยเชิงสร้างสรรค์ครบวงจร" → arts-research-pipeline
ถ้า prompt กล่าวถึง "หาแหล่งข้อมูล/literature" → arts-deep-research  
ถ้า prompt กล่าวถึง "เขียนบทความ/abstract/exegesis" → arts-paper-writer
ถ้า prompt กล่าวถึง "ตรวจ/review/peer review" → arts-paper-reviewer
ถ้า prompt กล่าวถึง "อ้างอิง/citation/bibliography" → arts-citation-formatter
ถ้า prompt กล่าวถึง "วิจัยเชิงปฏิบัติ/ผลงานสร้างสรรค์เป็นส่วนหนึ่ง" → practice-based-research
ถ้า prompt กล่าวถึง "วิเคราะห์ภาพ/งานศิลปะ" → visual-analysis
```

## Results Log

| Case ID | Date | Primary Correct | Secondary Correct | Clarification Asked | Notes |
|---------|------|-----------------|-------------------|---------------------|-------|
| TE-001 | | | | | |
| TE-002 | | | | | |
| TE-003 | | | | | |
| TE-004 | | | | | |
| TE-005 | | | | | |
| TE-006 | | | | | |
| TE-007 | | | | | |
| TE-008 | | | | | |
