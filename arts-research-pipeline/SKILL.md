---
name: arts-research-pipeline
description: ตัวจัดการ pipeline งานวิจัยเชิงสร้างสรรค์ทางศิลปะแบบครบวงจร 10 ขั้นตอน พร้อม Adaptive Checkpoint System (FULL/SLIM/MANDATORY), State Machine (IDLE→INTAKE→PLAN→RESEARCH→INTEGRITY-1→METHOD→WRITE→INTEGRITY-2→REVIEW→FINALIZE→COMPLETED), Research Passport (persistent state tracking), FONER Framework (RQ evaluation), และ Resume Protocol สำหรับงานที่ค้างกลางคัน ใช้ 10 Iron Rules ป้องกัน workflow errors รองรับ TCI Tier 1-2 และ Scopus Q1-Q4 สำหรับนักวิจัย CAMT ม.เชียงใหม่. Use when the user wants to start a complete arts research project from scratch, needs end-to-end orchestration, asks about "งานวิจัยศิลปะ", "วิจัยสร้างสรรค์", "creative research", "arts research pipeline", "วิจัยทัศนศิลป์/ดนตรี/นาฏศิลป์/ออกแบบ", "pipeline ค้าง", "resume งานวิจัย", or wants to coordinate multiple research stages. MUST trigger whenever a user mentions starting an arts/creative research project or asks about pipeline status.
license: MIT
metadata:
  author: CAMT Research Support Unit
  version: 2.0.0
  institution: College of Arts, Media and Technology, Chiang Mai University
  last_updated: "2026-05-05"
  related_skills:
    - arts-deep-research
    - arts-paper-writer
    - arts-paper-reviewer
    - arts-citation-formatter
    - practice-based-research
    - visual-analysis
---

# Arts Research Pipeline v2.0 (CAMT Edition)

ตัวจัดการ workflow งานวิจัยเชิงสร้างสรรค์ทางศิลปะแบบครบวงจร พร้อม Adaptive Checkpoint System, State Machine, และ Research Passport รองรับ TCI Tier 1-2 และวารสารนานาชาติ Scopus Q1-Q4

---

## Quick Start

```
"เริ่มงานวิจัยเรื่อง [หัวข้อ]"
```

**Output ที่จะได้**:
1. Project Brief Card + Complexity Assessment
2. Research Passport (อัปเดตทุก checkpoint)
3. Adaptive Checkpoints ตาม complexity
4. Coordination ของ skills ทั้ง pipeline

---

## Trigger Keywords

**ภาษาไทย**: งานวิจัยศิลปะ, วิจัยสร้างสรรค์, วิจัยเชิงสร้างสรรค์, วิจัยทางศิลปะ, pipeline งานวิจัย, จัดการงานวิจัย, เริ่มทำวิจัยศิลปะ, วิจัยทัศนศิลป์, วิจัยดนตรี, วิจัยนาฏศิลป์, วิจัยออกแบบ

**English**: arts research, creative research, artistic research, practice-based research, research pipeline, end-to-end research workflow

---

## Modes (8 โหมด)

| Mode | เมื่อไหร่ใช้ | Pipeline |
|------|------------|---------|
| `full` (default) | เริ่มงานวิจัยใหม่ครบวงจร | ทุก 10 stages |
| `quick` | เร่งด่วน, conference, abstract | Stages 1,4,5,8 |
| `practice-based` | มีผลงานสร้างสรรค์เป็น core | ปรับ Stage 3 → practice-based, Stage 4 → exegesis |
| `historical` | ประวัติศาสตร์ศิลป์/โบราณคดี | ปรับ Stage 3 → archival research |
| `theoretical` | ปรัชญาศิลป์, สุนทรียศาสตร์ | ปรับ Stage 3 → conceptual analysis |
| `ethnographic` | ดนตรีชาติพันธุ์, performance | ปรับ Stage 3 → fieldwork |
| `educational` | ศิลปศึกษา, นวัตกรรมการสอน | ปรับ Stage 3 → action research |
| `resume` | กลับมาทำต่อหลัง stall | ดู `references/resume_protocol.md` |

---

## Agent Team (2 Agents)

| # | Agent | บทบาท |
|---|-------|-------|
| 1 | `intake_assessment_agent` | รับ brief, complexity assessment, mode selection |
| 2 | `pipeline_orchestrator_agent` | ควบคุม state machine, checkpoints, Research Passport |

> ดูรายละเอียดใน `agents/` directory

---

## Adaptive Checkpoint System

### 3 Checkpoint Types

```
FULL      → สรุปครบ + artifacts + next steps + risk check
SLIM      → สรุปสั้น 3-5 bullet + next step เดียว
MANDATORY → checklist ทุกข้อ, ห้ามข้าม (Integrity Gates)
```

### Complexity Score → Checkpoint Level

| Score | Level | Checkpoint Pattern |
|-------|-------|------------------|
| 0-2 | LOW | SLIM ทั้งหมด (ยกเว้น MANDATORY) |
| 3-4 | MEDIUM | FULL: Stage 1,4,5 / SLIM: อื่นๆ |
| ≥5 | HIGH | FULL ทั้งหมด (ยกเว้น MANDATORY ที่บังคับ) |

ดูรายละเอียด: `agents/pipeline_orchestrator_agent.md` — Complexity Score Calculation

---

## Pipeline 10 ขั้นตอน

```
Stage 0:   INTAKE ASSESSMENT          → intake_assessment_agent
           [CHECKPOINT-0: MANDATORY — Project Brief Card confirm]
Stage 1:   PLAN                       → arts-deep-research (Socratic)
           [CHECKPOINT-1: FULL/SLIM]
Stage 2:   RESEARCH                   → arts-deep-research (full)
           [INTEGRITY GATE 1: MANDATORY — verify all sources]
Stage 2.5: INTEGRITY CHECK 1          → source_verification_agent
           [CHECKPOINT-2: SLIM]
Stage 3:   METHOD / CREATE            → practice-based-research / visual-analysis / etc.
           [CHECKPOINT-3: FULL/SLIM]
Stage 4:   WRITE                      → arts-paper-writer (full/exegesis)
           [INTEGRITY GATE 2: MANDATORY — citation + claim check]
Stage 4.5: INTEGRITY CHECK 2          → pipeline_orchestrator_agent
           [CHECKPOINT-4: MANDATORY]
Stage 5:   REVIEW                     → arts-paper-reviewer (pre-submission or full)
           [CHECKPOINT-5: FULL — Editorial Decision]
Stage 6:   REVISE (if needed)         → arts-paper-writer (revision)
           [CHECKPOINT-6: SLIM]
Stage 7:   VERIFY                     → arts-paper-writer (WQC) + arts-citation-formatter
           [CHECKPOINT-7: MANDATORY — TCI compliance]
Stage 8:   FINALIZE                   → final formatting + submission package
           [CHECKPOINT-8: FULL — submission confirmation]
Stage 9:   PROCESS SUMMARY (optional) → pipeline_orchestrator_agent
```

---

## State Machine

```
IDLE → INTAKE → PLAN → RESEARCH → [INTEGRITY-1] → METHOD →
WRITE → [INTEGRITY-2] → REVIEW →
  ├─ ACCEPT → FINALIZE → COMPLETED
  ├─ MINOR → REVISE → VERIFY → FINALIZE → COMPLETED
  ├─ MAJOR → REVISE → VERIFY → REVIEW (re-review) → ...
  └─ REJECT → DIAGNOSE → [restart relevant stage]

STALLED (> 2 weeks) → resume_protocol
FAILED → failure_paths.md → recovery → resume
```

---

## Research Passport

อัปเดตทุก checkpoint — ดู template ใน `templates/research_passport_template.md`

**ข้อมูลที่ track**:
- Stage status (✅/🔄/⏳/❓)
- Key deliverables ต่อ stage
- Materials inventory
- Key decisions log
- Active blockers

---

## Iron Rules

⚠️ **IRON RULE**: ห้าม skip MANDATORY checkpoints — รวมถึง Integrity Gate 1 (Stage 2.5) และ Integrity Gate 2 (Stage 4.5)

⚠️ **IRON RULE**: Research Passport ต้องอัปเดตที่ทุก checkpoint ห้าม pipeline ดำเนินต่อโดยไม่มี passport update

⚠️ **IRON RULE**: ถ้า failure path ถูก trigger ต้องรัน recovery protocol ก่อน resume — ห้าม ignore failure

⚠️ **IRON RULE — STALL**: ถ้าผู้ใช้กลับมาหลัง > 2 weeks ต้องรัน `resume_protocol` ก่อนเสมอ ห้าม assume stage ก่อนหน้าเสร็จสมบูรณ์

---

## Core Philosophy (ไม่เปลี่ยนแปลง)

1. **Multiple ways of knowing** — ความรู้ทางศิลปะมาจากการปฏิบัติ, การวิเคราะห์, การตีความ, และการไตร่ตรอง
2. **Practice as research** — งานสร้างสรรค์เป็น academic contribution ได้
3. **Hermeneutic rigor** — ความเข้มงวดอยู่ที่การตีความที่มีหลักฐานและ self-reflexivity
4. **Cultural situatedness** — ตระหนักบริบทไทย/ล้านนา/อาเซียน ไม่ใช้กรอบตะวันตกครอบทุกอย่าง
5. **Ethics of representation** — จริยธรรมในการนำเสนอภาพ บุคคล วัฒนธรรม มรดก

---

## Failure Handling

ดู `references/failure_paths.md` สำหรับ 8 failure scenarios:
F1: RQ Collapse Late | F2: Literature Too Thin | F3: Method-Finding Disconnect | F4: Pipeline Stall | F5: Skill Handoff Failure | F6: Scope Creep | F7: Reviewer Reject (Fundamental) | F8: Deadline Collapse

---

## Files Index

### Agents
| ไฟล์ | บทบาท |
|------|-------|
| `agents/intake_assessment_agent.md` | Brief intake + complexity assessment |
| `agents/pipeline_orchestrator_agent.md` | State machine + Adaptive Checkpoints + Passport |

### References
| ไฟล์ | วัตถุประสงค์ |
|------|------------|
| `references/failure_paths.md` | 8 failure scenarios + recovery |
| `references/resume_protocol.md` | กลับมาทำต่อหลัง stall |

### Templates
| ไฟล์ | วัตถุประสงค์ |
|------|------------|
| `templates/research_passport_template.md` | Research Passport บันทึก state ทั้ง pipeline |
| `templates/process_summary_template.md` | สรุปบทเรียนหลัง pipeline เสร็จ |

---

## Target Journals (CAMT Edition)

**TCI ในประเทศ**: วารสารวิชาการศิลปะ การออกแบบ และสถาปัตยกรรม | วารสารศิลปกรรมศาสตร์ จุฬาฯ | วารสารหน้าจั่ว | วารสารวิจิตรศิลป์ มช.

**ต่างประเทศ**: *Leonardo* (MIT Press) | *International Journal of Art & Design Education* | *Design Studies* | *Performance Research* | *Asian Theatre Journal* | *Journal of Visual Culture*

---

## Version History

| Version | วันที่ | การเปลี่ยนแปลง |
|---------|-------|--------------|
| 2.0.0 | 2026-05-05 | เพิ่ม Adaptive Checkpoint System (FULL/SLIM/MANDATORY), State Machine, Research Passport, pipeline_orchestrator_agent, intake_assessment_agent, resume_protocol, process_summary, failure_paths ครบ 8 scenarios, Iron Rules ทุก stage, ขยายเป็น 10 stages (เพิ่ม Stage 0 intake + Stage 9 process summary) |
| 1.0.0 | — | Initial release |
