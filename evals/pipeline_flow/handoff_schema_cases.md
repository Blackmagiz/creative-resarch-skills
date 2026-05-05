---
title: "Pipeline Flow — Handoff Schema Test Cases"
description: "ตรวจสอบการส่งต่อข้อมูลระหว่าง skills ผ่าน handoff schemas"
version: 1.0.0
---

# Pipeline Flow — Handoff Schema Test Cases

> อ้างอิง: shared/handoff_schemas.md — 5 handoff schemas

---

## Handoff Schema Reference

| Schema | From | To | Trigger Phrase |
|--------|------|----|----------------|
| Research Package | arts-deep-research | arts-paper-writer | "เริ่มเขียนได้เลย", "ready to write" |
| Review Package | arts-paper-writer | arts-paper-reviewer | "ส่งตรวจ", "ready for review" |
| Revision Package | arts-paper-reviewer | arts-paper-writer | "แก้ไขตาม reviewer", "revise" |
| Re-review Package | arts-paper-writer | arts-paper-reviewer re-review | "ส่งตรวจรอบสอง", "re-review" |
| Citation Package | arts-paper-writer | arts-citation-formatter | "จัดรูปแบบ reference", "format citations" |

---

### PF-HS-001 — Research → Write Handoff
**Scenario:** Literature review เสร็จแล้ว ส่งต่อให้ paper writer
**Input:** [Literature Matrix + Research Brief] `เริ่มเขียนได้เลย`
**Expected:** Research Package handoff schema ถูกใช้
**Assertions:**
- [ ] Research Package มี: Literature Matrix, Source Quality Summary, Research Gap Statement, Suggested Framework, RQ Version
- [ ] arts-paper-writer รับข้อมูลครบก่อนเริ่ม Intake Planning
- [ ] ไม่มีการ re-ask ข้อมูลที่ส่งมาแล้วใน package

### PF-HS-002 — Write → Review Handoff
**Scenario:** บทความเสร็จแล้ว ส่งให้ reviewer
**Input:** [Full draft] `ส่งตรวจ`
**Expected:** Review Package ครบถ้วน
**Assertions:**
- [ ] Review Package มี: manuscript, metadata (journal target, submission type), Author's Note, WQC score (ถ้ามี), Special concerns
- [ ] arts-paper-reviewer ได้รับ context journal ที่ต้องการส่ง
- [ ] EIC Agent เห็น journal context ก่อนเริ่ม review

### PF-HS-003 — Review → Revision Handoff
**Scenario:** Reviewer ส่ง comments กลับ
**Input:** [Review Report with P1/P2/P3 comments] `แก้ไขตาม reviewer`
**Expected:** Revision Package ถูกส่งไปยัง arts-paper-writer (Revision Coach mode)
**Assertions:**
- [ ] Revision Package มี: Original manuscript, Reviewer comments (prioritized), Editorial Decision, Deadline (ถ้าระบุ)
- [ ] Revision Coach Agent รับ P1/P2/P3 classification ที่มีอยู่แล้ว (ไม่ classify ซ้ำ)
- [ ] Anti-leakage warning ปรากฏทันที

### PF-HS-004 — Re-review Handoff
**Scenario:** แก้ไขเสร็จแล้ว ส่งตรวจรอบสอง
**Input:** [Revised manuscript + Response Letter] `ส่งตรวจรอบสอง`
**Expected:** Re-review Package ถูกส่ง
**Assertions:**
- [ ] Re-review Package มี: Revised manuscript, Response Letter, Original reviewer comments, Changes summary
- [ ] R&R Traceability Matrix ถูกสร้างขึ้น
- [ ] P1 items ถูกตรวจจาก manuscript (ไม่ใช่แค่ Response Letter) ⚠️ IRON RULE

### PF-HS-005 — Citation Handoff
**Scenario:** บทความเสร็จแล้ว ต้องการ format references
**Input:** [Bibliography list] `จัดรูปแบบ reference ทั้งหมด`
**Expected:** Citation Package ถูกส่ง
**Assertions:**
- [ ] Citation Package มี: bibliography list, target style (APA/Chicago/TCI), journal name, special source types
- [ ] arts-citation-formatter รู้ journal target ก่อนเริ่ม format
- [ ] Verification status ถูก request สำหรับทุก entry

### PF-HS-006 — Missing Package Data
**Scenario:** ผู้ใช้ trigger handoff โดยไม่มีข้อมูลครบ
**Input:** `เริ่มเขียนได้เลย` [โดยไม่มี Literature Matrix หรือ RQ]
**Expected:** arts-paper-writer detect ว่า package ไม่ครบ และถาม
**Assertions:**
- [ ] Missing fields ถูกระบุ (ไม่ใช่แค่ "ต้องการข้อมูลเพิ่ม")
- [ ] ถามเฉพาะ fields ที่ขาด

---

## Results Log

| Case ID | Schema | Package Complete? | No Re-ask? | Iron Rules? | Result | Notes |
|---------|--------|------------------|------------|-------------|--------|-------|
| PF-HS-001 | Research | | | | | |
| PF-HS-002 | Review | | | | | |
| PF-HS-003 | Revision | | | | | |
| PF-HS-004 | Re-review | | | | | |
| PF-HS-005 | Citation | | | | | |
| PF-HS-006 | Missing Data | | | | | |
