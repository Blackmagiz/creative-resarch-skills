---
title: "Output Quality — Bilingual Abstract Test Cases"
description: "ตรวจสอบ Thai/English abstract alignment และคุณภาพ"
version: 1.0.0
---

# Output Quality — Bilingual Abstract Test Cases

> อ้างอิง: arts-paper-writer/agents/bilingual_abstract_agent.md — 10-element alignment check

---

## 10-Element Alignment Checklist

| # | Element | Thai | English | Aligned? |
|---|---------|------|---------|---------|
| 1 | Background/context | | | |
| 2 | Research problem | | | |
| 3 | Objective/RQ | | | |
| 4 | Methodology | | | |
| 5 | Creative work/practice | | | |
| 6 | Key findings | | | |
| 7 | Contribution | | | |
| 8 | Conclusion | | | |
| 9 | Word count (200-300) | | | |
| 10 | Keywords (5-7) | | | |

---

### BA-001 — Generate Both Abstracts
**Input:** [Paper content + RQ + Methodology summary]
**`เขียน abstract ทั้งภาษาไทยและภาษาอังกฤษ`**
**Assertions:**
- [ ] Thai abstract ≥ 200 คำ, ≤ 300 คำ
- [ ] English abstract ≥ 200 words, ≤ 300 words
- [ ] English = rewrite ไม่ใช่ word-for-word translation (ตรวจโดยอ่านความเป็นธรรมชาติ)
- [ ] ทั้งคู่ครบ 5 ส่วน (Background, Problem, Objective, Method, Findings)

### BA-002 — Misaligned Abstract Detection
**Input:** [Thai abstract: "การวิจัยนี้ศึกษาจิตรกรรม" / English abstract: "This study examines sculpture"]
**Expected:** Claude detect ความไม่ตรง (จิตรกรรม ≠ sculpture)
**Assertions:**
- [ ] Alignment table ปรากฏ
- [ ] Element ที่ไม่ตรงถูก highlight
- [ ] แนะนำการแก้ไข

### BA-003 — Direct Translation Detection
**Input:** `แปล abstract ภาษาไทยนี้เป็นอังกฤษ: [Thai abstract]`
**Expected:** Claude ทำ rewrite เป็น academic English ไม่ใช่แปลตรงๆ
**Assertions:**
- [ ] ภาษาอังกฤษมีความเป็น academic register
- [ ] โครงสร้างประโยคเหมาะสมกับ English academic writing
- [ ] ไม่มีรูปแบบประโยคที่ตรงกับภาษาไทยมากเกินไป

### BA-004 — Keyword Language Match
**Input:** [Thai keywords: "จิตรกรรม, สี, พื้นที่, ร่วมสมัย, อัตลักษณ์"]
**Expected:** English keywords ควรเป็น "painting, color, space, contemporary, identity" (ไม่ใช่ transliteration)
**Assertions:**
- [ ] English keywords เป็น academic terms ไม่ใช่ transliteration
- [ ] จำนวน keywords ตรงกัน (5-7 ทั้งคู่)

---

## Results Log

| Case ID | Thai WC | English WC | 10-Elem Aligned | Result | Notes |
|---------|---------|------------|-----------------|--------|-------|
| BA-001 | | | | | |
| BA-002 | | | | | |
| BA-003 | | | | | |
| BA-004 | | | | | |
