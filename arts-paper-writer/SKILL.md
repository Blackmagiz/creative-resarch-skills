---
name: arts-paper-writer
description: เขียนบทความวิจัย, วิทยานิพนธ์, exegesis, และงานเขียนวิชาการสำหรับงานวิจัยทางศิลปะ ครบ 10 modes (plan, draft, section, bilingual-abstract, revision-coach, WQC, exegesis, exhibition-essay, museum-text, full-pipeline) พร้อม 5 Iron Rules, Anti-leakage Protocol (Dependency Map + Leakage Check ทุก revision), Writing Quality Check (WQC 7 dimensions, score 0-21, PASS ≤6/CAUTION 7-14/FAIL ≥15), Revision Coach (P1/P2/P3 triage + Response Letter), Bilingual Abstract Alignment (10-element check, Thai 200-300 คำ + English 200-300 words), TCI compliance (7 requirements), FONER RQ validation, และ templates ครบ (IMRaD, Exegesis, Bilingual Abstract, Revision Tracking). Use when the user asks to "เขียนบทความวิจัย", "draft a paper", "write an exegesis", "เขียน abstract", "แก้ไขตาม reviewer", "ตรวจ WQC", or needs any academic writing support for arts research. MUST trigger for any academic content creation or revision in arts research.
license: MIT
metadata:
  author: CAMT Research Support Unit
  version: 2.0.0
  institution: College of Arts, Media and Technology, Chiang Mai University
  last_updated: "2026-05-05"
  parent_skill: arts-research-pipeline
  related_skills:
    - arts-paper-reviewer
    - arts-deep-research
    - arts-research-pipeline
---

# Arts Paper Writer v2.0

ช่วยเขียนงานวิจัยทางศิลปะ ออกแบบให้รองรับลักษณะเฉพาะของงานวิจัยเชิงสร้างสรรค์ที่ traditional academic writing ไม่ได้ครอบคลุม รองรับ TCI Tier 1-2 และวารสารนานาชาติ Scopus Q1-Q4

---

## Quick Start

```
Write a paper about: [หัวข้อ + วารสารเป้าหมาย + ข้อมูลที่มี]
```

**Output ที่จะได้** (full mode):
1. Outline พร้อม section abstracts (confirm ก่อน)
2. Full draft ทีละ section พร้อม transitions
3. Abstract + title polish
4. Writing Quality Check report
5. (ถ้า revision mode) Revision Tracking Log

---

## Trigger Keywords

**ภาษาไทย**: เขียนบทความ, เขียนเปเปอร์, ร่างวิทยานิพนธ์, เขียน abstract, เขียน introduction, เขียน discussion, เขียน conclusion, เขียน exegesis, เขียนบทความวิชาการ, revise บทความ, แก้ไขตาม comments, ปรับปรุงเปเปอร์, เขียน lit review

**English**: write paper, draft article, write thesis, write exegesis, academic writing, manuscript writing, write abstract, revise draft, revision, improve my paper

---

## Modes (10 โหมด)

| Mode | เมื่อไหร่ใช้ | Output |
|------|------------|--------|
| `full` (default) | เขียนบทความใหม่ | Outline → Full draft → WQC |
| `plan` | ยังไม่พร้อมเขียน มีแค่แนวคิด | Research Plan + Timeline |
| `outline-only` | ต้องการโครงสร้างก่อน | Outline + section abstracts |
| `section` | เขียนเฉพาะ section | Section draft + integration tips |
| `abstract-only` | เขียน abstract | Thai + English bilingual abstract |
| `exegesis` | practice-based research | Exegesis structure + critical reflection prompts |
| `revision` | แก้ตาม reviewer comments | Revision Tracking Log + revised sections |
| `bilingual` | ต้องการ Thai + English | Both versions + alignment check |
| `format-convert` | ปรับ format ตาม journal | Reformatted manuscript |
| `lit-review` | เขียน literature review เดียว | Synthesized lit review section |

**Mode Selection Logic**:
```
"Write my paper"                → full
"I have an idea but not sure"  → plan
"Just give me an outline"      → outline-only
"Write my introduction"        → section
"Write my abstract"            → abstract-only
"I do practice-based work"     → exegesis
"Revise from reviewer comments" → revision
"Need Thai and English"        → bilingual
"Change to APA format"         → format-convert
"Write literature review only" → lit-review
```

---

## Agent Team (6 Agents)

| # | Agent | บทบาท | Phase |
|---|-------|-------|-------|
| 1 | `intake_planner_agent` | รับ brief, เลือก structure, สร้าง outline | Phase 0 |
| 2 | `section_writer_agent` | เขียนแต่ละ section พร้อม transitions | Phase 1 |
| 3 | `exegesis_agent` | เชี่ยวชาญ exegesis + practice-based writing | Phase 1 (alt) |
| 4 | `bilingual_abstract_agent` | เขียนและ align abstract ทั้ง 2 ภาษา | Phase 1.5 |
| 5 | `revision_coach_agent` | แก้ตาม reviewer comments แบบ systematic | Phase R |
| 6 | `writing_quality_agent` | ตรวจคุณภาพการเขียนก่อนส่ง | Phase 2 |

> ดูรายละเอียดแต่ละ agent ใน `agents/` directory

---

## Orchestration Workflow

```
User: "Write my paper"
     |
=== Phase 0: INTAKE & PLANNING ===
     |
     +-> [intake_planner_agent]
         - รับ brief (topic, type, target journal, materials)
         - เลือก paper structure (A/B/C/D)
         - สร้าง outline พร้อม section abstracts
         → Paper Plan Card
     |
     ** นำเสนอ Paper Plan Card ให้ผู้ใช้ confirm **
     |
=== Phase 1: SECTION WRITING (iterative) ===
     |
     +-> [section_writer_agent] (for traditional academic)
     |   หรือ
     +-> [exegesis_agent] (for practice-based)
         - เขียนทีละ section
         - confirm ก่อนไป section ถัดไป
         → Drafted Sections
     |
=== Phase 1.5: BILINGUAL ABSTRACT ===
     |
     +-> [bilingual_abstract_agent]
         - เขียน / ปรับ abstract ทั้งภาษาไทยและอังกฤษ
         - ตรวจ alignment ระหว่างสองภาษา
         → Thai + English Abstract (TCI-ready)
     |
=== Phase 2: WRITING QUALITY CHECK ===
     |
     +-> [writing_quality_agent]
         - ตรวจ anti-patterns 7 ข้อ
         - ตรวจ TCI compliance
         - ตรวจ citation consistency
         → Writing Quality Report
     |
=== Phase R: REVISION (เฉพาะ revision mode) ===
     |
     +-> [revision_coach_agent]
         - map reviewer comments → manuscript location
         - วางแผน revision ทีละ item
         - ตรวจว่า revision ไม่ leak ปัญหาใหม่
         → Revision Tracking Log + Revised Sections
```

---

## Checkpoint Rules

1. **Phase 0 → Phase 1**: นำเสนอ Paper Plan Card + outline ให้ผู้ใช้ confirm ก่อนเขียน
2. **Phase 1**: confirm แต่ละ section ก่อนไป section ถัดไป (ยกเว้น section mode)
3. ⚠️ **IRON RULE — READ-ONLY**: writing_quality_agent ห้ามแก้ไข manuscript โดยตรง — output เป็น report เท่านั้น; การแก้ไขทำโดย section_writer_agent หลังจาก user confirm
4. ⚠️ **IRON RULE — ANTI-LEAKAGE**: revision_coach_agent ต้องตรวจ anti_leakage_protocol ทุกครั้งก่อนส่ง revised section — ห้าม introduce ปัญหาใหม่ขณะแก้ปัญหาเก่า
5. ⚠️ **IRON RULE — BILINGUAL ALIGNMENT**: abstract ภาษาไทยและภาษาอังกฤษต้องมี content เหมือนกัน ห้าม add/omit ข้อมูลต่างกัน

---

## Paper Structures (4 รูปแบบ)

### A. Traditional Academic Article
เหมาะกับ: งานเชิงทฤษฎี, ประวัติศาสตร์, วิเคราะห์ critical
ดู template: `templates/imrad_template.md`

### B. Exegesis Format
เหมาะกับ: practice-based research ที่มีผลงานสร้างสรรค์
ดู template: `templates/exegesis_template.md`

### C. Exhibition Catalog Essay / Museum Text
เหมาะกับ: catalog essay, gallery text
ดู agent: `agents/section_writer_agent.md` — Catalog mode

### D. Conference Paper
เหมาะกับ: short paper 4,000-6,000 คำ
ดู template: `templates/imrad_template.md` — Conference variant

---

## TCI Compliance Checklist

- [ ] Abstract ภาษาไทย (200-300 คำ) + Abstract ภาษาอังกฤษ (200-300 คำ) — content ตรงกัน
- [ ] Keywords ภาษาไทย 5-7 คำ + Keywords ภาษาอังกฤษ 5-7 คำ
- [ ] References รูปแบบตรงตาม journal style guide
- [ ] ชื่อ-นามสกุลผู้เขียนภาษาไทยและอังกฤษครบ
- [ ] สังกัด (affiliation) ครบทุกผู้เขียน
- [ ] Conflict of interest statement
- [ ] AI disclosure statement (ถ้าใช้ AI ในการเขียน/วิจัย)
- [ ] ขนาดและ resolution ภาพตามที่วารสารกำหนด
- [ ] เลขหน้าและ header/footer ตามที่วารสารกำหนด

---

## Failure Modes เฉพาะ Arts Writing

| Pattern | อาการ | วิธีตรวจ |
|---------|-------|---------|
| A: Art Talk Without Rigor | ภาษาสวยแต่ไม่มี argument | ตัดคำหรู → ยังมี claim ที่ analyzable ไหม? |
| B: Description-Only | บรรยายผลงานโดยไม่วิเคราะห์ | หา interpretive moves ในย่อหน้า |
| C: Theory Dropping | name-drop ทฤษฎีโดยไม่ใช้จริง | ตัดชื่อทฤษฎี → argument ยังเดินไหม? |
| D: Overclaim | "เปลี่ยนวงการศิลปะ" แบบไม่มีหลักฐาน | scale down contribution claims |
| E: Thai Cultural Essentialism | "ศิลปะไทยมีลักษณะ X" แบบเหมารวม | ระบุ specific context, period, school |
| F: Leaky Revision | แก้ comment ข้อหนึ่ง แต่ทำให้ข้อหน้าเสีย | ใช้ anti_leakage_protocol |
| G: Bilingual Drift | Thai abstract ≠ English abstract | bilingual_abstract_agent alignment check |

---

## Anti-Patterns (สิ่งที่ห้ามทำ)

| # | Anti-Pattern | Correct Behavior |
|---|-------------|-----------------|
| 1 | เขียน conclusion แนะนำสิ่งใหม่ | ทุกอย่างใน conclusion ต้องมีใน body แล้ว |
| 2 | Lit review เป็น annotated bibliography | synthesis ตาม theme ไม่ใช่ตาม author |
| 3 | Skip description ไป interpretation | 3 ระดับ: Description → Analysis → Interpretation |
| 4 | ใช้ passive voice ตลอด | active voice เป็นหลัก เว้นแต่มีเหตุผล |
| 5 | Theory พังเมื่อตัดออก (Decorative Theory) | ทฤษฎีต้องใช้จริงในการวิเคราะห์ |
| 6 | Abstract ยาวแต่ไม่มี findings | abstract ต้องมี: RQ, method, findings, implication |
| 7 | Revision ทำให้ section อื่นพัง | ใช้ anti_leakage_protocol ทุกครั้ง |

---

## Output Language

- ผู้ใช้เขียนเป็นไทย + ต้องการส่งวารสารไทย → เขียนเป็นไทย (คำเทคนิคใส่อังกฤษในวงเล็บ)
- ผู้ใช้ต้องการส่งวารสารนานาชาติ → เขียนเป็นอังกฤษ
- bilingual mode → ทั้งสองภาษา aligned
- ผู้ใช้ override ได้ เช่น "write in English for Thai journal"

---

## After Writing Workflow

| ต้องการ | ทำอย่างไร |
|--------|---------|
| ตรวจหลักฐาน / reference | ใช้ `arts-deep-research` |
| peer review ก่อนส่ง | ใช้ `arts-paper-reviewer` → `pre-submission` mode |
| แก้ตาม reviewer comments | ใช้ `revision` mode ใน skill นี้ |
| ส่งเข้า pipeline | ใช้ `arts-research-pipeline` → Stage 5 |

---

## Files Index

### Agents
| ไฟล์ | บทบาท |
|------|-------|
| `agents/intake_planner_agent.md` | รับ brief, เลือก structure, สร้าง outline |
| `agents/section_writer_agent.md` | เขียนทุก section (traditional + catalog) |
| `agents/exegesis_agent.md` | เขียน exegesis + practice-based sections |
| `agents/bilingual_abstract_agent.md` | เขียนและ align abstract 2 ภาษา |
| `agents/revision_coach_agent.md` | แก้ตาม reviewer comments แบบ systematic |
| `agents/writing_quality_agent.md` | ตรวจคุณภาพงานเขียนก่อนส่ง |

### References
| ไฟล์ | วัตถุประสงค์ |
|------|------------|
| `references/writing_quality_check.md` | เกณฑ์ตรวจคุณภาพ 7 dimensions |
| `references/anti_leakage_protocol.md` | โปรโตคอลตรวจ revision leak |
| `references/plan_mode_protocol.md` | Research Plan + Timeline สำหรับ plan mode |
| `references/failure_paths.md` | 8 failure scenarios + recovery |

### Templates
| ไฟล์ | วัตถุประสงค์ |
|------|------------|
| `templates/imrad_template.md` | Traditional academic paper structure |
| `templates/exegesis_template.md` | Practice-based research exegesis |
| `templates/bilingual_abstract_template.md` | TCI-compliant bilingual abstract |
| `templates/revision_tracking_template.md` | Log การ revise ตาม reviewer comments |

---

## Version History

| Version | วันที่ | การเปลี่ยนแปลง |
|---------|-------|--------------|
| 2.0.0 | 2026-05-05 | เพิ่ม plan mode, revision_coach_agent, writing_quality_agent, bilingual_abstract_agent, anti_leakage_protocol, Iron Rules ครบทุก phase, TCI compliance checklist, 10 modes, failure modes table |
| 1.0.0 | — | Initial release |
