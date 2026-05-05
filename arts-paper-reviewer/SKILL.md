---
name: arts-paper-reviewer
description: จำลอง peer review process แบบวารสารวิชาการสำหรับงานวิจัยทางศิลปะ ใช้ทีม 7 agents (EIC, Field Analyst, Methodology Reviewer, Domain Reviewer, Cross-disciplinary Reviewer, Devil's Advocate, Editorial Synthesizer) พร้อม Iron Rules: READ-ONLY agents (ไม่แก้ manuscript), DA CRITICAL BLOCKS ACCEPT, Re-review Mode พร้อม R&R Traceability Matrix (ตรวจ P1 items ใน manuscript ไม่ใช่แค่ Response Letter), Failure Mode detection (FM-A ถึง FM-G), TCI/Scopus editorial standards, และ 8 modes (standard, re-review, guided, quick, methodology-focus, theory-focus, creative-component, pre-submission). Use when the user asks to "ตรวจบทความ", "review my paper", "peer review", "ประเมินงานวิจัย", "ตรวจ revision", "re-review", "give me reviewer comments", or wants critical feedback on an arts research manuscript. MUST trigger whenever a user wants substantive critique or peer review simulation.
license: MIT
metadata:
  author: CAMT Research Support Unit
  version: 2.0.0
  institution: College of Arts, Media and Technology, Chiang Mai University
  last_updated: "2026-05-05"
  parent_skill: arts-research-pipeline
  related_skills:
    - arts-paper-writer
    - arts-deep-research
    - arts-research-pipeline
---

# Arts Paper Reviewer v2.0

จำลอง peer review process ระดับวารสารสำหรับงานวิจัยทางศิลปะ ออกแบบเพื่อจับ failure modes ที่เฉพาะของ arts research ที่ generic reviewer skill จับไม่ได้ รองรับวารสาร TCI Tier 1-2 และวารสารนานาชาติ Scopus Q1-Q4

---

## Quick Start

```
Review this paper: [วาง draft หรือแนบไฟล์]
```

**Output ที่จะได้** (full mode):
1. Reviewer Configuration Card — ยืนยันตัวตน 5 reviewer ก่อน Phase 1
2. รายงาน reviewer อิสระ 5 ฉบับ (EIC, R1, R2, R3, DA)
3. Editorial Decision Letter + Revision Roadmap
4. (ถ้า Major/Minor) Revision Coaching แบบ Socratic (opt-in)

---

## Trigger Keywords

**ภาษาไทย**: ตรวจบทความ, review บทความ, peer review, ประเมินงานวิจัย, วิจารณ์เปเปอร์, ตรวจคุณภาพ, comments เปเปอร์, อ่านวิจัยให้, ตรวจก่อนส่งวารสาร, re-review, ตรวจ revision

**English**: peer review, review paper, evaluate manuscript, reviewer comments, critical feedback, paper critique, re-review, verify revision, guided review

---

## Modes (8 โหมด)

| Mode | เมื่อไหร่ใช้ | Agents | Output |
|------|------------|--------|--------|
| `full` (default) | review ครั้งแรก | ทั้ง 7 | 5 reports + Decision + Roadmap |
| `re-review` | หลัง author ส่ง revised กลับ | field_analyst + EIC + synthesizer | R&R Traceability Matrix + new decision |
| `quick` | ประเมินเร็ว | field_analyst + EIC | EIC assessment + key issues |
| `methodology-focus` | เน้น method | field_analyst + EIC + R1 | in-depth methodology report |
| `theory-focus` | เน้น theoretical framework | field_analyst + EIC + R3 | in-depth theory report |
| `creative-component` | เน้น practice-based work | field_analyst + R1 + R2 | creative work assessment |
| `pre-submission` | ตรวจสุดท้ายก่อนส่ง | ทั้ง 7 + TCI checklist | full review + compliance check |
| `guided` | เรียนรู้จากกระบวนการ | ทั้ง 7 + Socratic layer | Socratic guided review |

**Mode Selection Logic**:
```
"Review my paper"                    → full
"ช่วย review เร็วๆ"                  → quick
"ตรวจแค่ methodology"               → methodology-focus
"ตรวจ theory"                        → theory-focus
"ตรวจ creative work ด้วย"           → creative-component
"ตรวจก่อนส่งวารสารจริง"            → pre-submission
"อยากเรียนรู้จาก review"            → guided
"ส่ง revised กลับมาแล้ว"           → re-review
```

---

## Agent Team (7 Agents)

| # | Agent | บทบาท | Phase |
|---|-------|-------|-------|
| 1 | `field_analyst_agent` | วิเคราะห์สาขา กำหนดตัวตน reviewer ทั้ง 5 | Phase 0 |
| 2 | `eic_agent` | EIC — scope fit, originality, significance, overall | Phase 1 |
| 3 | `methodology_reviewer_agent` | R1 — method rigor, ethics, reproducibility | Phase 1 |
| 4 | `domain_reviewer_agent` | R2 — domain accuracy, citation quality, missing refs | Phase 1 |
| 5 | `cross_disciplinary_reviewer_agent` | R3 — theory depth, argument structure, cross-field | Phase 1 |
| 6 | `devils_advocate_agent` | DA — โจมตี argument หลัก 7 กลยุทธ์ | Phase 1 |
| 7 | `editorial_synthesizer_agent` | สังเคราะห์ → Editorial Decision + Revision Roadmap | Phase 2 |

> ดูรายละเอียดแต่ละ agent ใน `agents/` directory

---

## Orchestration Workflow (3 Phases)

```
User: "Review this paper"
     |
=== Phase 0: FIELD ANALYSIS & PERSONA CONFIGURATION ===
     |
     +-> [field_analyst_agent]
         - อ่านบทความทั้งฉบับ
         - ระบุ: สาขา, paradigm, method type, วารสารเป้าหมาย, ความสมบูรณ์
         - กำหนดตัวตน reviewer ทั้ง 5 ให้เฉพาะเจาะจงกับงานนั้น
         → Reviewer Configuration Card
     |
     ** นำเสนอ Reviewer Configuration Card ให้ผู้ใช้ยืนยัน (ปรับได้) **
     |
=== Phase 1: PARALLEL MULTI-PERSPECTIVE REVIEW ===
     |
     |-> [eic_agent]                          → EIC Review Report
     |-> [methodology_reviewer_agent]         → R1 Methodology Report
     |-> [domain_reviewer_agent]              → R2 Domain Expert Report
     |-> [cross_disciplinary_reviewer_agent]  → R3 Cross-disciplinary Report
     +-> [devils_advocate_agent]              → DA Critique (7 attack strategies)
     |
     ⚠️ IRON RULE: ทั้ง 5 review อย่างอิสระ ห้ามอ่าน report ของกันและกัน
     |
=== Phase 2: EDITORIAL SYNTHESIS & DECISION ===
     |
     +-> [editorial_synthesizer_agent]
         Step 1: สร้าง Cross-reviewer Matrix
         Step 2: จัดลำดับ — DA CRITICAL → บล็อค Accept, consensus → P1
         Step 3: ออก Editorial Decision + Revision Roadmap
         → Editorial Decision Letter + Revision Roadmap
     |
=== Phase 2.5: REVISION COACHING [Optional — Minor/Major only] ===
     |
     +-> EIC นำ Socratic dialogue 5 ขั้น
         (ผู้ใช้บอก "บอกตรงๆ" หรือ "skip" → ข้ามได้)
```

---

## Checkpoint Rules

1. **Phase 0 → Phase 1**: นำเสนอ Reviewer Configuration Card — ผู้ใช้ยืนยันก่อน
2. ⚠️ **IRON RULE**: Reviewers 5 คน review อย่างอิสระ ห้ามอ้างอิง report ของกันและกัน
3. ⚠️ **IRON RULE**: Synthesizer ห้ามสร้าง comment ใหม่ที่ไม่มีใน Phase 1 reports
4. ⚠️ **IRON RULE**: DA CRITICAL → Editorial Decision ห้าม Accept ไม่ว่ากรณีใด
5. ⚠️ **IRON RULE — READ-ONLY**: ทุก reviewer ห้ามแก้ไขต้นฉบับโดยตรง — output เป็น report เท่านั้น

---

## Re-Review Mode (Verification Review)

ใช้หลัง author ส่ง revised manuscript กลับมา ตรวจว่า revision แก้ Priority 1 items ครบหรือไม่

**Input ที่ต้องการ**: Revision Roadmap + Revised manuscript + Response Letter (ถ้ามี)

**Output**: R&R Traceability Matrix + new Editorial Decision

⚠️ **IRON RULE**: ทุก Priority 1 item ต้องตรวจใน manuscript จริง — ห้าม rubber-stamp ตาม Response Letter

> ดูรายละเอียด: `references/re_review_protocol.md`

---

## Failure Modes เฉพาะ Arts Research

| Pattern | อาการ | วิธีตรวจ |
|---------|-------|---------|
| A: Decorative Theory | name-drop Foucault/Bourdieu โดยไม่ใช้จริง | ตัดชื่อออก — argument ยังเดินได้ไหม? |
| B: Catalog Description | บรรยายผลงานโดยไม่วิเคราะห์ความหมาย | หา "interpretive moves" ในบทความ |
| C: Thai Cultural Essentialism | "ศิลปะไทยเป็น X" แบบเหมารวม | ตรวจ categorical statements |
| D: Western-Frame Imposition | ใช้กรอบตะวันตกกับงานไทย/ล้านนาโดยไม่ reflect | framework ตรงบริบทไหม? |
| E: Unverified References | AI-generated references | random sample 3-5 refs → search จริง |
| F: Practice-Research Confusion | ไม่แยก creative work กับ knowledge contribution | ระบุ "what practice contributes to knowledge"? |
| G: Missing Cultural Sensitivity | ใช้ภาพ/ข้อมูลชุมชนไม่มี consent | attribution + permission ครบไหม? |

---

## Anti-Patterns (สิ่งที่ reviewer ห้ามทำ)

| # | Anti-Pattern | Correct Behavior |
|---|-------------|-----------------|
| 1 | สร้าง comment ที่ไม่มีใน Phase 1 | ทุกประเด็น → อ้างกลับ reviewer ใดคนหนึ่ง |
| 2 | Reviewers ซ้ำประเด็น | แต่ละ reviewer มุมมองต่างกัน |
| 3 | ละเลย DA CRITICAL | DA CRITICAL → Decision ≠ Accept |
| 4 | Rubber-stamp re-review | ตรวจ manuscript จริง ไม่ใช่เชื่อ Response Letter |
| 5 | Score inflation | scores ต้อง evidence-based เสมอ |
| 6 | แก้ต้นฉบับโดยตรง | READ-ONLY — report เท่านั้น |
| 7 | Feedback กว้างไม่ specific | ทุก critique → what / where / how to fix |

---

## TCI Compliance Checklist (pre-submission mode)

- [ ] Abstract ภาษาไทย + อังกฤษ ครบทั้งสองภาษา คุณภาพดีเท่ากัน
- [ ] Keywords ภาษาไทย 5-7 คำ + ภาษาอังกฤษ 5-7 คำ
- [ ] References รูปแบบตรงตาม journal style guide
- [ ] ชื่อ-นามสกุลผู้เขียนภาษาไทยและอังกฤษครบ
- [ ] สังกัด (affiliation) ครบทุกผู้เขียน
- [ ] Conflict of interest statement
- [ ] AI disclosure statement (ถ้าใช้ AI ในการเขียน/วิจัย)
- [ ] ขนาดและ resolution ภาพตามที่วารสารกำหนด

---

## Output Language

- บทความภาษาไทย → review ภาษาไทย (คำเทคนิคที่ไม่มีคำแปล ใส่ภาษาอังกฤษในวงเล็บ)
- บทความภาษาอังกฤษ → review ภาษาอังกฤษ
- ผู้ใช้ override ได้ เช่น "review my Thai paper in English"

---

## After-Review Workflow

| ต้องการ | ทำอย่างไร |
|--------|---------|
| revise ตาม comments | ใช้ `arts-paper-writer` → `revision` mode |
| เขียน Response to Reviewers | ใช้ template ใน `templates/revision_response_template.md` |
| verify reference ที่สงสัย | ใช้ `arts-deep-research` |
| ส่ง revised manuscript กลับมา | เรียก `re-review` mode |

---

## Files Index

### Agents
| ไฟล์ | บทบาท |
|------|-------|
| `agents/field_analyst_agent.md` | วิเคราะห์สาขา กำหนดตัวตน reviewer |
| `agents/eic_agent.md` | Editor-in-Chief |
| `agents/methodology_reviewer_agent.md` | R1 Methodology |
| `agents/domain_reviewer_agent.md` | R2 Domain Expert |
| `agents/cross_disciplinary_reviewer_agent.md` | R3 Cross-disciplinary/Theory |
| `agents/devils_advocate_agent.md` | Devil's Advocate |
| `agents/editorial_synthesizer_agent.md` | Editorial Synthesizer |

### References
| ไฟล์ | วัตถุประสงค์ |
|------|------------|
| `references/re_review_protocol.md` | โปรโตคอล re-review + R&R Traceability Matrix |
| `references/editorial_decision_criteria.md` | เกณฑ์ Accept/Minor/Major/Reject + TCI standards |
| `references/quality_rubrics.md` | Calibrated rubrics 0-10 + decision mapping |
| `references/guided_mode_protocol.md` | Socratic guided review — 5-layer dialogue |

### Templates
| ไฟล์ | วัตถุประสงค์ |
|------|------------|
| `templates/review_report_template.md` | Template สำหรับ reviewer แต่ละคน |
| `templates/editorial_decision_template.md` | Editorial Decision Letter มาตรฐาน TCI |
| `templates/revision_response_template.md` | Response to Reviewers — R→A→C format |

---

## Version History

| Version | วันที่ | การเปลี่ยนแปลง |
|---------|-------|--------------|
| 2.0.0 | 2026-05-05 | เพิ่ม re-review mode, field_analyst dynamic persona, 7 agents แยกไฟล์, Socratic guided review Phase 2.5, calibrated rubrics, TCI compliance checklist, Iron Rules ครบทุก phase |
| 1.0.0 | — | Initial release |
