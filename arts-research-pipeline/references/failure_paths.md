---
name: failure_paths
purpose: 8 failure scenarios ใน arts-research-pipeline + recovery strategies
parent_skill: arts-research-pipeline
version: 1.0.0
---

# Failure Paths — Arts Research Pipeline

## Overview

Pipeline failures คือสถานการณ์ที่ทำให้ workflow ทั้ง pipeline สะดุด แตกต่างจาก skill-level failures ตรงที่ pipeline failures ส่งผลต่อหลาย stages พร้อมกัน

---

## Failure Path Table

| # | ชื่อ | Trigger | Stage ที่กระทบ | Recovery |
|---|-----|---------|-------------|---------|
| F1 | RQ Collapse Late | RQ พัง (ไม่ specific / ไม่ original) ที่ Stage 4-5 | Stage 4-8 ทั้งหมด | Emergency reset → กลับ Stage 2 → FONER assessment ใหม่ |
| F2 | Literature Too Thin | ส่ง manuscript ไปยัง reviewer แต่ lit ยังบาง | Stage 5 → 6 block | กลับ Stage 3 → arts-deep-research → เพิ่ม sources → re-enter Stage 4 |
| F3 | Method-Finding Disconnect | Analysis findings ไม่ตอบ RQ | Stage 5 → decision ไม่ได้ | กลับ Stage 4 → re-analyze หรือ RQ adjustment |
| F4 | Pipeline Stall | ผู้ใช้หยุดกลางทาง >2 weeks ไม่มีความคืบหน้า | ทุก stage | Resume Protocol: อ่าน Research Passport → identify last stage → re-brief |
| F5 | Skill Handoff Failure | ข้อมูลจาก skill หนึ่งไม่ครบสำหรับ skill ถัดไป | ที่ transition point | ตรวจ handoff checklist → ส่ง missing materials กลับ source skill |
| F6 | Scope Creep | RQ ขยายตัวกลางโครงการ ทำให้ต้องทำงานเพิ่ม | Stage 3-5 | Scope Decision: expand timeline หรือ narrow RQ กลับ |
| F7 | Reviewer Reject (Fundamental) | Reject ที่มาจาก fundamental problem (ไม่ใช่ minor) | Stage 7 → pipeline restart | Diagnose: RQ problem? Lit problem? Method problem? → route กลับ stage ที่เหมาะ |
| F8 | Deadline Collapse | เวลาไม่พอสำหรับ pipeline ทั้งหมด | ทุก stage | Priority triage: identify minimum viable submission vs full pipeline |

---

## Stage-to-Skill Mapping

| Stage | Skill | Input | Output |
|-------|-------|-------|--------|
| 1: Topic & RQ | arts-deep-research (Socratic) | แนวคิดเบื้องต้น | RQ + FONER assessment |
| 2: Literature | arts-deep-research (full) | RQ | Literature Matrix |
| 3: Methodology | practice-based-research / visual-analysis | RQ + lit | Method plan |
| 4: Analysis | visual-analysis / practice-based-research | Data/artworks | Analysis notes |
| 5: Writing | arts-paper-writer | All above | Draft manuscript |
| 6: Internal review | arts-paper-writer (WQC) | Draft | Quality report |
| 7: Peer review | arts-paper-reviewer | Manuscript | Reviewer decision |
| 8: Revision | arts-paper-writer (revision) | Decision + comments | Revised manuscript |
| 9: Final check | arts-paper-reviewer (pre-submission) | Revised | TCI-ready |
| 10: Submission | — | Final manuscript | Submitted |

---

## Detailed Recovery: F1 — RQ Collapse Late

**Detection at Stage 4-5**:
- arts-paper-reviewer flag: RQ ไม่ specific / ไม่ original
- Analysis findings ไม่ convergent ไปทาง RQ เดิม
- Author เองบอกว่า "งานออกมาไม่ตรงที่คิดไว้"

**Emergency Reset Protocol**:
```
Step 1: บันทึก Research Passport ณ จุดที่ผิดพลาด
Step 2: กลับ Stage 2 (Literature) 
        — Literature ที่มีอยู่ยังใช้ได้? หรือต้องหาใหม่?
Step 3: FONER re-assessment กับ RQ ใหม่/ปรับ
Step 4: ตัดสินใจ:
        Option A: Adjust RQ ให้ตรงกับ findings ที่เกิดขึ้นจริง
        Option B: กลับ Stage 4 แล้ว re-analyze ด้วย RQ เดิม
        Option C: ปรับ scope ให้เล็กลง (narrow RQ)
Step 5: Update Research Passport → resume pipeline
```

---

## Detailed Recovery: F4 — Pipeline Stall

**Resume Protocol**:
```
1. อ่าน Research Passport (ถ้ามี) — สรุป progress ที่ผ่านมา
2. ถ้าไม่มี Research Passport:
   - ถามผู้ใช้: "ครั้งสุดท้ายที่ทำถึงขั้นตอนไหน? มีไฟล์อะไรบ้างที่ทำไปแล้ว?"
   - สร้าง Research Passport ใหม่จากสิ่งที่มี
3. ระบุ: Stage ล่าสุดที่เสร็จ + Stage ที่ต้องทำต่อ
4. ตรวจ: materials จาก Stage ก่อนหน้ายังใช้ได้ไหม?
   - Literature ยังทันสมัย (< 2 ปี)?
   - RQ ยังสอดคล้องกับความสนใจปัจจุบัน?
5. Resume จาก Stage ที่หยุด — ไม่จำเป็นต้องเริ่มใหม่
```

---

## Detailed Recovery: F5 — Skill Handoff Failure

**Handoff Checklist**:

| จาก Stage | ไปยัง Stage | Materials ที่ต้องครบ |
|---------|-----------|-------------------|
| Stage 1 → 2 | RQ → Literature | FONER-assessed RQ, Research context brief |
| Stage 2 → 3 | Literature → Method | Literature Matrix, identified gap, key frameworks |
| Stage 3 → 4 | Method → Analysis | Method plan, objects of study, analysis framework |
| Stage 4 → 5 | Analysis → Writing | Analysis notes, key arguments (3+), evidence list |
| Stage 5 → 6 | Writing → WQC | Complete draft (all sections), citation list |
| Stage 6 → 7 | WQC → Peer Review | WQC-passed draft, bilingual abstract |
| Stage 7 → 8 | Review → Revision | Editorial decision, reviewer comments (all), original MS |

**ถ้า materials ไม่ครบ**: กลับ source stage → ทำ missing materials → handoff ใหม่

---

## Detailed Recovery: F8 — Deadline Collapse

**Priority Triage Matrix**:

| เวลาที่เหลือ | Minimum Viable Submission | ข้ามขั้นตอนไหนได้ |
|----------|--------------------------|-----------------|
| < 1 week | draft ที่ดีที่สุดที่มี | ข้าม pre-submission review |
| 1-2 weeks | draft + WQC | ข้าม full peer review simulation |
| 2-4 weeks | draft + WQC + quick review | ใช้ quick mode แทน full mode |
| > 4 weeks | full pipeline | ไม่ข้ามขั้นตอนใด |

**ห้ามข้ามเสมอ**: TCI compliance check, bilingual abstract alignment, citation format check
