---
name: arts-deep-research
description: ทบทวนวรรณกรรมและสืบค้นแหล่งข้อมูลเชิงลึกสำหรับงานวิจัยทางศิลปะ ครอบคลุมฐานข้อมูล 14 แหล่ง (TCI, ThaiLIS, SAC, CMU Repository + international) พร้อม Source Quality Hierarchy (Tier 1-4), Gray Zone = FAIL Iron Rule, PRISMA-adapted screening, Socratic Mode สำหรับผู้ที่ยังไม่มี RQ ชัดเจน (5-layer dialogue), Citation Chain tracking, Literature Matrix, handoff protocol ไปยัง arts-paper-writer, และ anti-hallucination verification (NO AI-GENERATED CITATIONS Iron Rule). Use when the user asks for "ทบทวนวรรณกรรม", "literature review", "หาเอกสารอ้างอิง", "หาเปเปอร์เกี่ยวกับ", "งานวิจัยที่เกี่ยวข้อง", "research gap", "primary sources", "ยังไม่รู้จะวิจัยอะไร", or needs arts-specific scholarly sources. MUST trigger for any literature search or source-finding task related to arts research.
license: MIT
metadata:
  author: CAMT Research Support Unit
  version: 2.0.0
  institution: College of Arts, Media and Technology, Chiang Mai University
  last_updated: "2026-05-05"
  parent_skill: arts-research-pipeline
  related_skills:
    - arts-paper-writer
    - arts-paper-reviewer
    - arts-research-pipeline
---

# Arts Deep Research v2.0

ทบทวนวรรณกรรมเชิงลึกสำหรับงานวิจัยทางศิลปะ ออกแบบเฉพาะสำหรับสาขาวิชาที่ CAMT รับผิดชอบ รองรับทั้งผู้ที่มี RQ ชัดเจนและผู้ที่ยังต้องการ guidance ก่อนเริ่มวิจัย

---

## Quick Start

**มี RQ แล้ว**:
```
ทบทวนวรรณกรรมเรื่อง [หัวข้อ] — สาขา [สาขา]
```

**ยังไม่มี RQ**:
```
อยากวิจัยเรื่อง [ความสนใจกว้างๆ] แต่ยังไม่รู้จะโฟกัสอะไร
```
→ activate Socratic mode อัตโนมัติ

---

## Trigger Keywords

**ภาษาไทย**: ทบทวนวรรณกรรม, หาเอกสารอ้างอิง, literature review, หาเปเปอร์, งานวิจัยที่เกี่ยวข้อง, สืบค้นวรรณกรรม, research gap, แหล่งข้อมูลปฐมภูมิ, ยังไม่รู้จะวิจัยอะไร, ช่วยนำทางการวิจัย, ช่วยคิดหัวข้อวิจัย

**English**: literature review, scholarly search, find papers, primary sources, art bibliography, research gap analysis, guide my research, help me find a topic

---

## Modes (6 โหมด)

| Mode | เมื่อไหร่ใช้ | Output |
|------|------------|--------|
| `socratic` | ยังไม่มี RQ ชัดเจน | INSIGHT Collection + RQ ร่าง |
| `lit-review` (default) | มี RQ แล้ว | Literature Matrix + Narrative Review |
| `quick` | ต้องการข้อมูลเร็ว | Research Brief (10-15 sources) |
| `systematic` | ต้องการ PRISMA-style | Systematic Review Protocol + PRISMA flow |
| `gap-analysis` | ต้องการระบุ research gaps | Gap Analysis Report |
| `primary-source` | เน้น artworks/archives | Primary Source Inventory |

**Socratic Mode Activation — ตรวจจาก Intent (ไม่ใช่แค่ keywords)**:
- ผู้ใช้ไม่มี RQ ชัดเจน
- ขอให้ "นำ" หรือ "ช่วยคิด"
- แสดงความไม่แน่ใจว่าจะวิจัยอะไร
- อธิบายความสนใจกว้างๆ

**Default rule**: เมื่อ intent คลุมเครือ → เลือก socratic ก่อนเสมอ

---

## Agent Team (5 Agents)

| # | Agent | บทบาท | Phase |
|---|-------|-------|-------|
| 1 | `research_question_agent` | แปลง topic → RQ ที่ชัดเจน (FONER framework) | Phase 1 / Socratic Layer 1 |
| 2 | `socratic_mentor_agent` | นำ Socratic dialogue 5 ชั้น | Socratic Mode |
| 3 | `bibliography_agent` | สืบค้นวรรณกรรมอย่างเป็นระบบ | Phase 2 |
| 4 | `source_verification_agent` | ตรวจ AI hallucination, predatory journals, tier | Phase 2 |
| 5 | `synthesis_agent` | สังเคราะห์ narrative review + ระบุ research gap | Phase 3 |

> ดูรายละเอียดแต่ละ agent ใน `agents/` directory

---

## Orchestration Workflow

### Full Mode (มี RQ แล้ว)

```
User: "ทบทวนวรรณกรรมเรื่อง X"
     |
=== Phase 1: SCOPING ===
[research_question_agent]
- ตรวจสอบ RQ ด้วย FONER framework
- ถ้า RQ ยังกว้าง → ถามให้แคบลงก่อน
→ Confirmed RQ + Search Scope
     |
** User confirm scope ก่อนดำเนินการ **
     |
=== Phase 2: INVESTIGATION ===
[bibliography_agent] → Source Corpus (ทั้ง Thai + International)
[source_verification_agent] → Source Quality Matrix
     |
⚠️ IRON RULE: Gray zone = FAIL ถ้า verify ไม่ได้ 100% → อย่าใช้
     |
=== Phase 3: SYNTHESIS ===
[synthesis_agent] → Literature Matrix + Narrative Review + Gap Analysis
     |
=== Phase 4: HANDOFF (Optional) ===
ถ้าผู้ใช้ต้องการเขียนบทความต่อ → ส่ง Research Package ไป arts-paper-writer
```

### Socratic Mode (ยังไม่มี RQ)

```
User: "อยากวิจัยเรื่อง X แต่ยังไม่รู้โฟกัสอะไร"
     |
[socratic_mentor_agent] — 5-layer dialogue:
Layer 1: Clarification (ทำความชัดเจน)
Layer 2: Assumption Probing (ตรวจสอบสมมติฐาน)
Layer 3: Evidence & Reasoning (หลักฐาน)
Layer 4: Viewpoint & Perspective (มุมมองที่หลากหลาย)
Layer 5: Implication & Consequence (นัยยะ)
     |
→ INSIGHT Collection + RQ ร่าง
     |
** User confirm → ย้ายไป Full mode หรือ lit-review **
```

---

## Checkpoint Rules

1. **Phase 1 → Phase 2**: User confirm RQ + Search Scope ก่อน
2. ⚠️ **IRON RULE**: References ที่ verify ไม่ได้ → ห้ามนำไปใช้
3. ⚠️ **IRON RULE**: ต้องมีทั้ง Thai sources + International sources (ยกเว้นหาไม่ได้จริงๆ)
4. ⚠️ **IRON RULE — Socratic**: ห้ามให้คำตอบตรงๆ ก่อนผู้ใช้คิดเอง
5. **Phase 4 Handoff**: User confirm Research Package ก่อนส่งต่อ

---

## ฐานข้อมูลที่ใช้ (ปรับตามสาขา)

### ทั่วไปทางศิลปะ/มนุษยศาสตร์
JSTOR Arts & Sciences, Project MUSE, Cambridge Core, Oxford Academic / Grove Art Online, Taylor & Francis, SAGE Journals, Art & Architecture Source (EBSCO), ArtBibliographies Modern

### สาขาเฉพาะ
- **ดนตรี**: RILM Abstracts, RIPM, JSTOR Music
- **ทัศนศิลป์/ออกแบบ**: BHA (Bibliography of the History of Art), DAAI
- **การแสดง**: International Bibliography of Theatre & Dance
- **ภาพถ่าย**: History of Photography journal archives
- **โบราณคดี**: AATA Online, Web of Science (Archaeology)
- **สื่อศิลปะ**: Leonardo Online, Rhizome.org archives
- **ศิลปศึกษา**: ERIC + JSTOR (education)

### ฐานข้อมูลไทย (บังคับค้น)
- TCI (Thai-Journal Citation Index) — tci-thaijo.org
- ThaiLIS / ThaiJO
- CMUL (ห้องสมุด มช.) + Chula + Silpakorn digital libraries
- หอสมุดศิลปะ มศก. (Silpakorn Art Library)
- จดหมายเหตุแห่งชาติ (National Archives)

### Primary Sources Online
- Google Arts & Culture
- Europeana, Wikimedia Commons (public domain)
- พิพิธภัณฑ์: MoMA, Tate, Met, V&A, Rijksmuseum
- พิพิธภัณฑ์ไทย: หอศิลป์ มศก., MOCA Bangkok, BACC, พิพิธภัณฑสถานแห่งชาติ
- IMSLP (โน้ตเพลง public domain)

---

## หลักการสืบค้น

### Boolean Search Strategy
```
Thai example:
("ลายพิมพ์ผ้า" OR "textile pattern" OR "ลายผ้า") 
AND ("ล้านนา" OR "Lanna" OR "northern Thai") 
AND ("ร่วมสมัย" OR "contemporary" OR "modern")
```

### Citation Network Search
เริ่มจาก seminal paper → forward citation (งานที่อ้างงานนี้) + backward citation (งานที่งานนี้อ้าง)

### ภาษาไทยในการค้น
ค้นทั้งไทยและอังกฤษแยกกัน — ผลต่างกันมาก อย่าค้นแค่ภาษาเดียว

---

## ⚠️ คำเตือน AI Hallucination

AI มีแนวโน้มสูงที่จะ:
- **สร้างชื่อบทความปลอม** ที่ดู plausible แต่ไม่มีอยู่จริง
- **สร้างผู้เขียนปลอม** หรือสลับชื่อ-ปี
- **สร้าง DOI ปลอม** ที่เปิดไม่ได้
- **อ้าง quote ปลอม** จากนักวิชาการชื่อดัง

⚠️ **IRON RULE**: ทุก reference ที่ AI suggest **ต้องตรวจสอบจริง**
ถ้า verify ไม่ได้ → ถือว่าไม่มีจริง → ห้ามนำไปใช้

---

## Failure Paths

> ดูรายละเอียด: `references/failure_paths.md`

| Scenario | Recovery |
|----------|---------|
| Socratic ไม่ converge > 10 rounds | เสนอ 3 candidate RQs, หรือ lit-review ก่อน |
| Literature หาไม่พอ (< 10 verified) | ขยาย search, เปลี่ยน keywords, ลองฐานข้อมูลอื่น |
| > 30% refs เป็น AI-generated | แจ้งผู้ใช้ทันที, ทำ manual search ใหม่ |
| Primary sources เข้าไม่ได้ | แนะนำ alternative collections, ติดต่อ institution |

---

## Handoff Protocol

หลังวิจัยเสร็จ ส่งต่อให้ `arts-paper-writer`:
- RQ Brief + Verified Source Matrix + Literature Synthesis → arts-paper-writer ข้ามขั้นตอนที่มีแล้ว

> ดูรายละเอียด: `references/handoff_protocol.md`

---

## Files Index

### Agents
| ไฟล์ | บทบาท |
|------|-------|
| `agents/research_question_agent.md` | RQ formulation + FONER scoring |
| `agents/socratic_mentor_agent.md` | Socratic 5-layer dialogue |
| `agents/bibliography_agent.md` | Systematic literature search |
| `agents/source_verification_agent.md` | Verification + tier grading |
| `agents/synthesis_agent.md` | Narrative synthesis + gap analysis |

### References
| ไฟล์ | วัตถุประสงค์ |
|------|------------|
| `references/socratic_mode_protocol.md` | โปรโตคอล Socratic mode ฉบับเต็ม |
| `references/failure_paths.md` | Failure scenarios + recovery strategies |
| `references/handoff_protocol.md` | ส่งต่อ Research Package ไป arts-paper-writer |

### Templates
| ไฟล์ | วัตถุประสงค์ |
|------|------------|
| `templates/literature_matrix_template.md` | ตาราง Literature Matrix มาตรฐาน |
| `templates/research_brief_template.md` | Research Brief สำหรับ quick mode |

---

## Version History

| Version | วันที่ | การเปลี่ยนแปลง |
|---------|-------|--------------|
| 2.0.0 | 2026-05-05 | เพิ่ม Socratic mode, 5 agents แยกไฟล์, failure_paths, handoff_protocol, Iron Rules, literature matrix template |
| 1.0.0 | — | Initial release |
