---
title: "Trigger Accuracy — Negative Cases"
description: "Prompts ที่ไม่ควร trigger arts skills — ทดสอบ precision (ไม่ trigger เกินจำเป็น)"
version: 1.0.0
---

# Trigger Accuracy — Negative Cases

> PASS = ไม่มี arts skill ถูก trigger | FAIL = arts skill ถูก trigger โดยไม่จำเป็น

---

## คำถามทั่วไป — ไม่ควร trigger art skills

### TN-001
**Input:** `ช่วยแปลภาษาไทยเป็นอังกฤษหน่อย`
**Expected:** ไม่มี skill ถูก trigger / ตอบตรงๆ
**Risk:** arts-paper-writer อาจ trigger เพราะเกี่ยวกับ "ภาษา"
**Assertion:** [ ] ไม่มี arts skill SKILL.md ถูกอ่าน

### TN-002
**Input:** `สูตรทำผัดไทยคืออะไร`
**Expected:** ไม่มี skill ถูก trigger
**Assertion:** [ ] ตอบตรงๆ ไม่มี skill overhead

### TN-003
**Input:** `ช่วยเขียน Python script วนลูปนับเลข 1-100`
**Expected:** ไม่มี arts skill (อาจเป็น coding tool)
**Risk:** arts-paper-writer trigger เพราะ "เขียน"
**Assertion:** [ ] arts-paper-writer ไม่ถูก trigger

### TN-004
**Input:** `วิเคราะห์ข้อมูลทางสถิติจาก Excel file นี้`
**Expected:** xlsx skill / ไม่ใช่ visual-analysis
**Risk:** visual-analysis trigger เพราะ "วิเคราะห์"
**Assertion:** [ ] visual-analysis ไม่ถูก trigger

### TN-005
**Input:** `สร้าง PowerPoint เกี่ยวกับประวัติศาสตร์ไทย`
**Expected:** pptx skill
**Risk:** arts-paper-writer trigger เพราะ "ประวัติศาสตร์"
**Assertion:** [ ] arts-paper-writer ไม่ถูก trigger

---

## คำถามที่คล้าย arts แต่ไม่ใช่วิจัย

### TN-006
**Input:** `อยากวาดรูปเป็น ควรเรียนอะไร`
**Expected:** ตอบตรงๆ เรื่องการศึกษาศิลปะ (ไม่ใช่ research skill)
**Risk:** arts-research-pipeline หรือ practice-based-research อาจ trigger
**Assertion:** [ ] ไม่มี arts research skill ถูก trigger

### TN-007
**Input:** `ภาพนี้สวยไหม`
**Expected:** ความเห็นส่วนตัว / ไม่ใช่ formal analysis
**Risk:** visual-analysis trigger เพราะ "ภาพ"
**Assertion:** [ ] visual-analysis ไม่ถูก trigger เว้นแต่ผู้ใช้ขอ "วิเคราะห์"

### TN-008
**Input:** `อ้างอิง Wikipedia ได้ไหม`
**Expected:** ตอบตรงๆ เรื่อง source quality (ไม่ต้อง invoke citation formatter)
**Risk:** arts-citation-formatter trigger เพราะ "อ้างอิง"
**Assertion:** [ ] arts-citation-formatter ไม่ถูก trigger สำหรับคำถามทั่วไป

### TN-009
**Input:** `เขียน short story เรื่องนักดนตรี`
**Expected:** creative writing (ไม่ใช่ arts research)
**Risk:** arts-paper-writer trigger
**Assertion:** [ ] arts-paper-writer ไม่ถูก trigger (วิจัยกับ creative writing ต่างกัน)

### TN-010
**Input:** `summarize this research paper for me`
**Expected:** สรุปตรงๆ / ไม่ต้อง invoke reviewer
**Risk:** arts-paper-reviewer trigger
**Assertion:** [ ] arts-paper-reviewer ไม่ถูก trigger สำหรับการสรุปทั่วไป

---

## Results Log

| Case ID | Date | Result | Notes |
|---------|------|--------|-------|
| TN-001 | | | |
| TN-002 | | | |
| TN-003 | | | |
| TN-004 | | | |
| TN-005 | | | |
| TN-006 | | | |
| TN-007 | | | |
| TN-008 | | | |
| TN-009 | | | |
| TN-010 | | | |
