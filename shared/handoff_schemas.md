---
name: handoff_schemas
purpose: Format มาตรฐานสำหรับส่งข้อมูลระหว่าง skills
version: 2.0.0
scope: ALL skills in camt-arts-research-skills
---

# Handoff Schemas — Inter-Skill Data Transfer

*เอกสารนี้กำหนด format มาตรฐานสำหรับการส่งข้อมูลระหว่าง skills ใน pipeline*

---

## Schema 1: Research Package (arts-deep-research → arts-paper-writer)

ใช้เมื่อ arts-deep-research เสร็จแล้วและพร้อมส่งต่อ arts-paper-writer

```markdown
## Research Package v2.0

**Date**: [date]
**From**: arts-deep-research
**To**: arts-paper-writer
**Mode requested**: [full / exegesis / section]

### Research Question (FONER-verified)
[ระบุ RQ ที่ผ่าน FONER assessment แล้ว]

FONER: F✅ O✅ N✅ E✅ R✅

### Research Context
[2-3 ประโยค summary ของ context และ gap]

### Literature Matrix Summary
**Total sources**: [n]
**Key frameworks**: [list 2-3]
**Research gap**: [1-2 ประโยค]
**Missing canonical works**: [list ถ้ามี]

### Key Sources (Top 10 most important)
| # | Author, Year | Core Argument | Relevance to RQ |
|---|------------|--------------|----------------|
| 1 | | | |
| ... | | | |

### Recommended Paper Structure
[ ] Structure A (Traditional Academic)
[ ] Structure B (Exegesis)
[ ] Structure C (Catalog Essay)
[ ] Structure D (Conference)
Rationale: [เหตุผล]

### Target Journal
Journal: [ชื่อ]
Tier: [TCI / Scopus Q]
Citation style: [APA 7 / Chicago / TCI]
Word limit: [n]
Language: [Thai / English / Bilingual]

### Materials Available
[ ] Full Literature Matrix (attached)
[ ] Primary source list
[ ] Analysis notes (from Stage 3)
[ ] Creative work documentation (if practice-based)
```

---

## Schema 2: Review Package (arts-paper-writer → arts-paper-reviewer)

ใช้เมื่อ manuscript draft พร้อมสำหรับ peer review

```markdown
## Review Package v2.0

**Date**: [date]
**From**: arts-paper-writer
**To**: arts-paper-reviewer
**Mode requested**: [full / pre-submission / quick]

### Manuscript Information
Title: [ชื่อ]
Authors: [list]
Target journal: [ชื่อ + tier]
Word count: [n]
Structure: [A/B/C/D]
Language: [Thai / English / Bilingual]

### Writing Quality Check Result
WQC Score: [n/35]
Anti-pattern findings: [summary]
TCI compliance: [✅/⚠️]
Status: [PASS / CAUTION / FAIL]

### Author's Concerns
[สิ่งที่ author ไม่แน่ใจและอยากให้ reviewer ช่วยตรวจ]

### Manuscript (attached)
[draft document]
```

---

## Schema 3: Revision Package (arts-paper-reviewer → arts-paper-writer revision mode)

ใช้หลัง peer review เสร็จ และ author ต้องการ revise

```markdown
## Revision Package v2.0

**Date**: [date]
**From**: arts-paper-reviewer
**To**: arts-paper-writer (revision mode)

### Editorial Decision
Decision: [ACCEPT / MINOR REVISION / MAJOR REVISION / REJECT]
Priority 1 comments: [n]
Priority 2 comments: [n]
DA CRITICAL: [n]

### Revision Roadmap (Priority 1 — Must fix)
| ID | Reviewer | Issue | Location | Action Required |
|----|---------|-------|---------|----------------|
| EIC-1 | EIC | | | |
| R1-1 | R1 | | | |
| DA-1 | DA | | | |

### Original Manuscript (attached)
### Reviewer Reports (attached)
```

---

## Schema 4: Re-review Package (arts-paper-writer → arts-paper-reviewer re-review mode)

ใช้เมื่อส่ง revised manuscript กลับ reviewer

```markdown
## Re-review Package v2.0

**Date**: [date]
**From**: arts-paper-writer (revision mode)
**To**: arts-paper-reviewer (re-review mode)

### Revision Summary
Priority 1 comments addressed: [n/n]
Priority 2 comments addressed: [n/n]
DA CRITICAL comments addressed: [n/n]

### Revised Manuscript (attached)
### Original Revision Roadmap (attached)
### Response to Reviewers Letter (attached)

### Author Notes
[สิ่งที่ author ต้องการให้ reviewer ทราบ รวมถึง comments ที่ disagree]
```

---

## Schema 5: Citation Package (arts-paper-writer → arts-citation-formatter)

```markdown
## Citation Package v2.0

**Date**: [date]
**From**: arts-paper-writer
**To**: arts-citation-formatter

### Citation Requirements
Target style: [APA 7 / Chicago 17 / TCI / MLA 9]
Journal: [ชื่อ]
Language: [Thai / English / Mixed]

### Sources to Format
[List ของ references ที่ต้องการ format — ระบุชนิด: journal / book / catalog / etc.]

### Special Source Types (non-standard)
[exhibition catalogs, artist statements, interviews, performances, etc.]
```

---

## Trigger Phrases สำหรับ Handoffs

| จาก skill | ไปยัง skill | Trigger phrase |
|---------|-----------|--------------|
| arts-deep-research | arts-paper-writer | "Research Package พร้อมแล้ว / ส่งต่อให้ arts-paper-writer" |
| arts-paper-writer | arts-paper-reviewer | "Draft พร้อม review / ส่งให้ reviewer" |
| arts-paper-reviewer | arts-paper-writer | "Revision Roadmap พร้อม / แก้ตาม comments" |
| arts-paper-writer | arts-paper-reviewer | "Revision เสร็จ / re-review" |
| arts-paper-writer | arts-citation-formatter | "จัด references ตาม [style]" |
