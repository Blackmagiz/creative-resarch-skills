# CAMT Arts Research Skills v2.0

**ชุด skill สำหรับนักวิจัยวิทยาลัยศิลปะ สื่อ และเทคโนโลยี (CAMT) มหาวิทยาลัยเชียงใหม่**

รองรับการทำวิจัยเชิงสร้างสรรค์ตั้งแต่ต้นจนจบ — ตั้งแต่การกำหนด RQ, ทบทวนวรรณกรรม, เขียนบทความ, ผ่าน peer review, ไปจนถึงการจัด citation ให้ตรงมาตรฐาน TCI Tier 1–2 และ Scopus Q1–Q4

---

## 7 Skills

| Skill | วัตถุประสงค์หลัก | Trigger keywords |
|-------|-----------------|-----------------|
| [arts-research-pipeline](#arts-research-pipeline) | จัดการ workflow ครบวงจร 10 ขั้นตอน | "เริ่มวิจัย", "pipeline", "resume งานวิจัย" |
| [arts-deep-research](#arts-deep-research) | ทบทวนวรรณกรรม + หาแหล่งข้อมูล 14 ฐาน | "ทบทวนวรรณกรรม", "หาเอกสาร", "literature review" |
| [arts-paper-writer](#arts-paper-writer) | เขียนบทความ / exegesis / abstract | "เขียนบทความ", "draft", "abstract", "exegesis" |
| [arts-paper-reviewer](#arts-paper-reviewer) | Peer review จำลอง 7 agents | "ตรวจบทความ", "review", "peer review" |
| [arts-citation-formatter](#arts-citation-formatter) | จัดรูปแบบ citation 10 ประเภท | "อ้างอิง", "citation", "bibliography" |
| [practice-based-research](#practice-based-research) | วิจัยเชิงปฏิบัติ + exegesis + process journal | "practice-based", "ผลงานสร้างสรรค์", "exegesis" |
| [visual-analysis](#visual-analysis) | วิเคราะห์งานทัศนศิลป์ 5 frameworks | "วิเคราะห์ภาพ", "formal analysis", "iconography" |

---

## โครงสร้างไฟล์

```
camt-arts-research-skills/
├── README.md                          ← ไฟล์นี้
│
├── arts-research-pipeline/            ← Pipeline manager
│   ├── SKILL.md
│   ├── agents/
│   │   ├── pipeline_orchestrator_agent.md
│   │   └── intake_assessment_agent.md
│   ├── references/
│   │   ├── failure_paths.md
│   │   └── resume_protocol.md
│   └── templates/
│       ├── research_passport_template.md
│       └── process_summary_template.md
│
├── arts-deep-research/                ← Literature research
│   ├── SKILL.md
│   ├── agents/
│   │   ├── research_question_agent.md
│   │   ├── socratic_mentor_agent.md
│   │   ├── bibliography_agent.md
│   │   ├── source_verification_agent.md
│   │   └── synthesis_agent.md
│   ├── references/
│   │   ├── failure_paths.md
│   │   ├── socratic_mode_protocol.md
│   │   └── handoff_protocol.md
│   └── templates/
│       ├── research_brief_template.md
│       └── literature_matrix_template.md
│
├── arts-paper-writer/                 ← Academic writing
│   ├── SKILL.md
│   ├── agents/
│   │   ├── intake_planner_agent.md
│   │   ├── section_writer_agent.md
│   │   ├── exegesis_agent.md
│   │   ├── bilingual_abstract_agent.md
│   │   ├── revision_coach_agent.md
│   │   └── writing_quality_agent.md
│   ├── references/
│   │   ├── failure_paths.md
│   │   ├── anti_leakage_protocol.md
│   │   ├── writing_quality_check.md
│   │   └── plan_mode_protocol.md
│   └── templates/
│       ├── imrad_template.md
│       ├── exegesis_template.md
│       ├── bilingual_abstract_template.md
│       └── revision_tracking_template.md
│
├── arts-paper-reviewer/               ← Peer review simulation
│   ├── SKILL.md
│   ├── agents/
│   │   ├── eic_agent.md
│   │   ├── field_analyst_agent.md
│   │   ├── methodology_reviewer_agent.md
│   │   ├── domain_reviewer_agent.md
│   │   ├── cross_disciplinary_reviewer_agent.md
│   │   ├── devils_advocate_agent.md
│   │   └── editorial_synthesizer_agent.md
│   ├── references/
│   │   ├── editorial_decision_criteria.md
│   │   ├── guided_mode_protocol.md
│   │   ├── quality_rubrics.md
│   │   └── re_review_protocol.md
│   └── templates/
│       ├── editorial_decision_template.md
│       ├── review_report_template.md
│       └── revision_response_template.md
│
├── arts-citation-formatter/           ← Citation formatting
│   ├── SKILL.md
│   ├── agents/
│   │   └── citation_formatter_agent.md
│   ├── references/
│   │   └── failure_paths.md
│   └── templates/
│       └── arts_citation_templates.md
│
├── practice-based-research/           ← Practice-led research
│   ├── SKILL.md
│   ├── agents/
│   │   └── practice_guide_agent.md
│   ├── references/
│   │   └── failure_paths.md
│   └── templates/
│       └── process_journal_template.md
│
├── visual-analysis/                   ← Visual art analysis
│   ├── SKILL.md
│   ├── agents/
│   │   └── visual_analysis_agent.md
│   ├── references/
│   │   └── failure_paths.md
│   └── templates/
│       └── analysis_worksheet_template.md
│
├── shared/                            ← Cross-skill resources
│   ├── cross_agent_quality_definitions.md  ← FM codes, IR codes, Source Tiers
│   ├── handoff_schemas.md                  ← 5 inter-skill data transfer formats
│   ├── tci_compliance_guide.md             ← TCI 7 requirements + checklist
│   └── mode_spectrum.md                    ← Mode tables ทุก skill
│
└── evals/                             ← Evaluation test suite
    ├── README.md
    ├── trigger_accuracy/
    │   ├── positive_cases.md          ← 34 prompts ที่ควร trigger
    │   ├── negative_cases.md          ← 10 prompts ที่ไม่ควร trigger
    │   └── edge_cases.md              ← 8 กรณีกำกวม
    ├── output_quality/
    │   ├── iron_rules_checklist.md    ← ตรวจ 10 Iron Rules
    │   ├── tci_compliance_cases.md    ← ตรวจ TCI 7 requirements
    │   └── bilingual_abstract_cases.md
    ├── failure_paths/
    │   ├── fm_detection_cases.md      ← FM-A ถึง FM-G
    │   └── recovery_protocol_cases.md
    └── pipeline_flow/
        ├── handoff_schema_cases.md    ← 5 handoff schemas
        └── state_machine_cases.md     ← 10 state transitions
```

---

## v2.0 Core Features

### Iron Rules (10 กฎที่ละเมิดไม่ได้)

| Code | Rule | บังคับใช้ใน |
|------|------|-----------|
| IR-1 | CONFIRM BEFORE ACT | ทุก skill |
| IR-2 | NO AI-GENERATED CITATIONS | arts-deep-research, arts-citation-formatter |
| IR-3 | GRAY ZONE = FAIL | arts-deep-research |
| IR-4 | DA CRITICAL BLOCKS ACCEPT | arts-paper-reviewer |
| IR-5 | ANTI-LEAKAGE | arts-paper-writer |
| IR-6 | BILINGUAL ALIGNMENT | arts-paper-writer |
| IR-7 | FONER FAIL = CANNOT WRITE | arts-paper-writer, arts-research-pipeline |
| IR-8 | THREE LEVELS REQUIRED | visual-analysis |
| IR-9 | EVIDENCE-BASED | visual-analysis |
| IR-10 | ETHICS FIRST | practice-based-research |

> รายละเอียดทั้งหมด: [shared/cross_agent_quality_definitions.md](shared/cross_agent_quality_definitions.md)

---

### Failure Modes (FM-A ถึง FM-G)

| Code | ชื่อ | ตรวจโดย |
|------|------|---------|
| FM-A | Decorative Theory | arts-paper-writer, arts-paper-reviewer |
| FM-B | Catalog Description | visual-analysis, arts-paper-reviewer |
| FM-C | Thai Cultural Essentialism | visual-analysis, arts-paper-reviewer |
| FM-D | Western Frame Imposition | visual-analysis, arts-paper-reviewer |
| FM-E | Unverified References | arts-deep-research, arts-citation-formatter |
| FM-F | Practice-Research Confusion | practice-based-research |
| FM-G | Missing Cultural Sensitivity | visual-analysis, arts-paper-reviewer |

---

### Adaptive Checkpoint System (arts-research-pipeline)

| Type | ใช้เมื่อ | Complexity Score |
|------|---------|-----------------|
| FULL | งานซับซ้อนสูง | ≥ 5 |
| SLIM | งานตรงไปตรงมา | 2–4 |
| MANDATORY | Integrity Gate — ข้ามไม่ได้เสมอ | ทุก score |

**Complexity Score** คำนวณจาก 7 ปัจจัย: research type, primary data, cross-cultural, multiple media, collaboration, timeline, journal tier

---

### State Machine (arts-research-pipeline)

```
IDLE → INTAKE → PLAN → RESEARCH
     → [INTEGRITY-1] → METHOD → WRITE
     → [INTEGRITY-2] → REVIEW
     → ACCEPT / MINOR / MAJOR / REJECT
     → FINALIZE → COMPLETED

พิเศษ: STALLED (ค้างกลางคัน), FAILED (FONER fail × 3)
```

**Research Passport** ติดตาม state ทุกขั้นตอน — ดู [arts-research-pipeline/templates/research_passport_template.md](arts-research-pipeline/templates/research_passport_template.md)

---

### Inter-Skill Handoff Schemas (5 schemas)

| จาก | ไปยัง | Schema | Trigger |
|-----|-------|--------|---------|
| arts-deep-research | arts-paper-writer | Research Package | "เริ่มเขียน", "ready to write" |
| arts-paper-writer | arts-paper-reviewer | Review Package | "ส่งตรวจ", "ready for review" |
| arts-paper-reviewer | arts-paper-writer | Revision Package | "แก้ไขตาม reviewer" |
| arts-paper-writer | arts-paper-reviewer | Re-review Package | "ส่งตรวจรอบสอง" |
| arts-paper-writer | arts-citation-formatter | Citation Package | "จัดรูปแบบ reference" |

> รายละเอียดทั้งหมด: [shared/handoff_schemas.md](shared/handoff_schemas.md)

---

### TCI Compliance (7 requirements)

TCI (Thai-Journal Citation Index) — บังคับสำหรับการตีพิมพ์ในวารสารไทย

1. Bilingual Abstract (Thai 200–300 คำ + English 200–300 words)
2. Bilingual Keywords (Thai 5–7 + English 5–7)
3. Author Information (ไทย + อังกฤษ + email + สังกัด)
4. Conflict of Interest Statement
5. AI Disclosure
6. References format (TCI standard + Thai romanization)
7. Figure Requirements (≥ 300 DPI + bilingual caption)

> รายละเอียด: [shared/tci_compliance_guide.md](shared/tci_compliance_guide.md)

---

## Typical Workflow

### เริ่มโครงการวิจัยใหม่
```
arts-research-pipeline → arts-deep-research → arts-paper-writer
→ arts-paper-reviewer → arts-paper-writer (revision) → arts-citation-formatter
```

### มีหัวข้อแล้ว เขียนบทความเลย
```
arts-paper-writer (plan mode) → arts-paper-writer (draft) → arts-paper-reviewer
```

### ตรวจ revision รอบสอง
```
arts-paper-writer (revision coach) → arts-paper-reviewer (re-review mode)
```

### วิจัยเชิงปฏิบัติ
```
practice-based-research → arts-paper-writer (exegesis mode) → arts-paper-reviewer
```

---

## Eval Suite

ทดสอบคุณภาพ skill ได้ที่ [evals/](evals/) ครอบคลุม:
- **Trigger accuracy**: 52 test cases (34 positive + 10 negative + 8 edge)
- **Output quality**: Iron Rules (10) + TCI compliance (7 requirements) + Bilingual abstract
- **Failure path coverage**: FM-A ถึง FM-G detection + 6 recovery scenarios
- **Pipeline flow**: 5 handoff schemas + 10 state transitions

เป้าหมาย baseline: Trigger precision ≥ 90%, Iron Rules compliance ≥ 90%, FM detection ≥ 85%

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 2.0.0 | 2026-05-05 | Iron Rules (IR-1–IR-10), Adaptive Checkpoint, State Machine, Research Passport, Re-review Mode, Anti-leakage Protocol, WQC (7 dimensions), Socratic Mode, FONER Framework, Revision Coach, shared/ resources, evals/ suite, 7-skill architecture (removed performance-arts-research) |
| 1.0.0 | 2026-04-01 | Initial release — 8 skills, basic SKILL.md structure |

---

## License

MIT — College of Arts, Media and Technology (CAMT), Chiang Mai University
