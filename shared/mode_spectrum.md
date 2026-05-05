---
name: mode_spectrum
purpose: แผนภาพและตารางแสดง modes ทั้งหมดของทุก skill
version: 2.0.0
scope: Reference สำหรับ user และ orchestration agents
---

# Mode Spectrum — All Skills

*เอกสารนี้รวม modes ของทุก skill ไว้ในที่เดียว เพื่อให้ pipeline_orchestrator_agent และผู้ใช้เลือก mode ได้ถูกต้อง*

---

## arts-research-pipeline

| Mode | เมื่อใช้ | Route |
|------|---------|-------|
| `full` | เริ่มงานใหม่ครบวงจร | ทุก 10 stages |
| `quick` | เร่งด่วน / conference | Stages 0,1,4,5,8 |
| `practice-based` | มีผลงานสร้างสรรค์ | Stage 3→practice, Stage 4→exegesis |
| `historical` | ประวัติศาสตร์ศิลป์ | Stage 3→archival |
| `theoretical` | ปรัชญา/theory | Stage 3→conceptual |
| `ethnographic` | ภาคสนาม | Stage 3→fieldwork |
| `educational` | ศิลปศึกษา | Stage 3→action research |
| `resume` | กลับมาทำต่อ | resume_protocol |

---

## arts-deep-research

| Mode | เมื่อใช้ | Agent chain |
|------|---------|------------|
| `socratic` | RQ ยังไม่ชัด | socratic_mentor + RQ agent |
| `full` | RQ ชัดแล้ว ต้องการ lit ครบ | RQ + bibliography + source_verification + synthesis |
| `quick` | ต้องการ brief เร็ว | bibliography (quick) + synthesis |
| `systematic` | PRISMA-style review | ทุก agent + PRISMA protocol |
| `update` | อัปเดต lit เดิม | bibliography (incremental) + synthesis |
| `verify-only` | ตรวจ references เท่านั้น | source_verification |

---

## arts-paper-writer

| Mode | เมื่อใช้ | Agent chain |
|------|---------|------------|
| `full` | เขียนใหม่ครบ | intake → section → bilingual → WQC |
| `plan` | ยังไม่พร้อมเขียน | intake (plan mode only) |
| `outline-only` | ต้องการโครงสร้าง | intake → outline output |
| `section` | เขียน section เดียว | section_writer |
| `abstract-only` | เขียน abstract | bilingual_abstract_agent |
| `exegesis` | practice-based | intake → exegesis_agent → bilingual → WQC |
| `revision` | แก้ตาม reviewer | revision_coach + anti_leakage |
| `bilingual` | Thai + English | bilingual_abstract_agent |
| `format-convert` | ปรับ format | section_writer (format mode) |
| `lit-review` | เขียน lit review เดียว | section_writer (lit review) |

---

## arts-paper-reviewer

| Mode | เมื่อใช้ | Agent chain |
|------|---------|------------|
| `full` | review ครั้งแรก | ทุก 7 agents |
| `re-review` | ตรวจ revision | field_analyst + EIC + synthesizer |
| `quick` | ประเมินเร็ว | field_analyst + EIC |
| `methodology-focus` | เน้น method | field_analyst + EIC + R1 |
| `theory-focus` | เน้น theory | field_analyst + EIC + R3 |
| `creative-component` | เน้น practice-based | field_analyst + R1 + R2 |
| `pre-submission` | ตรวจก่อนส่งจริง | ทุก 7 + TCI checklist |
| `guided` | เรียนรู้จาก process | ทุก 7 + Socratic layer |

---

## Quick Mode Selection Guide

**สำหรับ pipeline_orchestrator_agent ใช้ตาราง Decision Matrix นี้**:

```
"เพิ่งมีแนวคิด ยังไม่รู้จะทำอะไร"
  → pipeline: full | deep-research: socratic | paper-writer: plan

"มี RQ แล้ว ต้องการค้นหา literature"
  → deep-research: full

"มี literature แล้ว ต้องการเขียน"
  → paper-writer: full (หรือ exegesis ถ้า practice-based)

"เขียนเสร็จแล้ว ต้องการ review"
  → paper-reviewer: full (หรือ pre-submission ถ้าใกล้ submit)

"ได้ reviewer comments มา ต้องการแก้"
  → paper-writer: revision

"แก้แล้ว ต้องการตรวจซ้ำ"
  → paper-reviewer: re-review

"ต้องการแค่ abstract"
  → paper-writer: abstract-only

"ต้องการแค่ verify references"
  → deep-research: verify-only | citation-formatter: verify
```
