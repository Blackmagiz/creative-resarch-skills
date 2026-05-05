---
title: "Pipeline Flow — State Machine Test Cases"
description: "ตรวจสอบ State Machine transitions ใน arts-research-pipeline"
version: 1.0.0
---

# Pipeline Flow — State Machine Test Cases

> อ้างอิง: arts-research-pipeline/agents/pipeline_orchestrator_agent.md — State Machine

---

## State Machine Reference

```
IDLE → INTAKE → PLAN → RESEARCH → [INTEGRITY-1] → METHOD → WRITE
     → [INTEGRITY-2] → REVIEW → [ACCEPT | MINOR | MAJOR | REJECT]
     → FINALIZE → COMPLETED

Special States: STALLED, FAILED
```

---

### SM-001 — Normal Forward Transition
**Scenario:** New project เริ่มต้นปกติ
**Flow:** IDLE → INTAKE → PLAN
**Test:** ส่ง project brief → confirm → ไปต่อ
**Assertions:**
- [ ] State INTAKE ปรากฏใน Research Passport
- [ ] หลัง confirm → state update เป็น PLAN
- [ ] Complexity Score ถูกคำนวณที่ INTAKE

### SM-002 — INTEGRITY-1 Gate
**Scenario:** Research เสร็จ แต่ literature quality ต่ำ — Tier 3 ทั้งหมด
**Flow:** RESEARCH → [INTEGRITY-1 FAIL] → back to RESEARCH
**Test:** [Bibliography ที่มีแต่ exhibition catalogs ไม่มี peer-reviewed]
**Assertions:**
- [ ] INTEGRITY-1 gate ปรากฏ
- [ ] INTEGRITY-1 FAIL ถ้า Tier 1 < 50%
- [ ] State กลับเป็น RESEARCH (ไม่ไป METHOD)
- [ ] Research Passport update เป็น RESEARCH (retry)

### SM-003 — INTEGRITY-2 Gate (Pre-submission)
**Scenario:** Draft เสร็จ ต้องผ่าน quality check ก่อน review
**Flow:** WRITE → [INTEGRITY-2] → REVIEW
**Test:** [Draft ที่ WQC score = 16 FAIL]
**Assertions:**
- [ ] INTEGRITY-2 gate ปรากฏ
- [ ] WQC FAIL → State ไม่ไป REVIEW
- [ ] State กลับเป็น WRITE (revision)
- [ ] WQC score ถูกบันทึกใน Research Passport

### SM-004 — ACCEPT Branch
**Scenario:** Review Decision = Accept
**Flow:** REVIEW → ACCEPT → FINALIZE → COMPLETED
**Assertions:**
- [ ] State update: REVIEW → FINALIZE
- [ ] Finalization checklist ปรากฏ
- [ ] State จบที่ COMPLETED
- [ ] Process Summary Template ถูกเสนอ

### SM-005 — MAJOR Revision Branch
**Scenario:** Review Decision = Major Revision
**Flow:** REVIEW → MAJOR → [loop back] → WRITE
**Assertions:**
- [ ] State = MAJOR REVISION
- [ ] Revision Package ถูกสร้าง
- [ ] State loop กลับ WRITE (ไม่ข้ามไป FINALIZE)
- [ ] Research Passport บันทึก revision round number

### SM-006 — REJECT Branch
**Scenario:** Review Decision = Reject
**Flow:** REVIEW → REJECT → [options: revise for other journal OR terminate]
**Assertions:**
- [ ] State = REJECTED
- [ ] Claude เสนอ options (ไม่ terminate ทันที)
- [ ] ถ้าเลือก revise → เสนอ alternative journals
- [ ] Research Passport บันทึก rejection + reason

### SM-007 — STALLED State Detection
**Scenario:** ไม่มีความคืบหน้า > 4 สัปดาห์
**Trigger:** "วิจัยค้างอยู่นานมากแล้ว" / ไม่มีการ update
**Assertions:**
- [ ] STALLED state ถูก recognize
- [ ] Resume Protocol เสนอ (5 steps)
- [ ] Blocker ถูกถาม

### SM-008 — FAILED State
**Scenario:** FONER FAIL + ผู้ใช้ไม่สามารถ reframe RQ
**Flow:** [FONER FAIL] × 3 → FAILED
**Assertions:**
- [ ] FAILED state ปรากฏหลังจาก 3 FONER fails
- [ ] Claude เสนอ alternative approach (เช่น เปลี่ยน research type)
- [ ] Research Passport บันทึก failure reason

### SM-009 — Checkpoint Type Selection
**Scenario:** Low complexity project (score = 2)
**Expected:** SLIM checkpoint ถูกเลือก (ไม่ใช่ FULL)
**Test:** [Project: เขียน essay เดี่ยว, หัวข้อเป็น field ที่คุ้นเคย, ไม่มี primary data]
**Assertions:**
- [ ] Complexity Score ≤ 3 → SLIM checkpoint
- [ ] SLIM checkpoint ใช้เวลาน้อยกว่า FULL
- [ ] MANDATORY gates ยังคงปรากฏ (ไม่ skip)

### SM-010 — Research Passport Continuity
**Scenario:** Resume session ใหม่ — ต้องการ restore state
**Test:** "ช่วยดูว่าวิจัยของฉันอยู่ที่ไหน"
**Assertions:**
- [ ] Research Passport ถูก retrieve (หรือ reconstruct จาก conversation)
- [ ] Stage Status ทุก stage ถูกแสดง
- [ ] Active Blockers ถูกแสดง (ถ้ามี)
- [ ] Next recommended action ปรากฏ

---

## Results Log

| Case ID | State Transition | Passport Updated? | Iron Rules OK? | Result | Notes |
|---------|-----------------|------------------|----------------|--------|-------|
| SM-001 | IDLE→PLAN | | | | |
| SM-002 | INTEGRITY-1 | | | | |
| SM-003 | INTEGRITY-2 | | | | |
| SM-004 | ACCEPT | | | | |
| SM-005 | MAJOR | | | | |
| SM-006 | REJECT | | | | |
| SM-007 | STALLED | | | | |
| SM-008 | FAILED | | | | |
| SM-009 | Checkpoint | | | | |
| SM-010 | Resume | | | | |
