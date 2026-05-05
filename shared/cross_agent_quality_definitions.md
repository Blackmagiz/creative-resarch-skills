---
name: cross_agent_quality_definitions
purpose: คำนิยาม quality standards ที่ใช้ร่วมกันในทุก skill
version: 2.0.0
scope: ALL skills in camt-arts-research-skills
---

# Cross-Agent Quality Definitions

*เอกสารนี้กำหนดนิยามที่ใช้ร่วมกันใน agent ทุกตัวของ camt-arts-research-skills เพื่อความสอดคล้องกัน*

---

## 1. Source Quality Hierarchy

| Tier | คำอธิบาย | ตัวอย่าง | ใช้ใน academic work |
|------|---------|---------|-------------------|
| **Tier 1** | Peer-reviewed, vetted | JSTOR, Scopus journal articles, TCI-indexed articles | ✅ Primary sources |
| **Tier 2** | Grey literature จากแหล่งที่มีอำนาจ | Preprints (arXiv, SSRN), UN reports, government documents, conference proceedings | ✅ ด้วยความระมัดระวัง |
| **Tier 3** | Non-peer-reviewed แต่ legitimate | Exhibition catalogs, artist statements, museum publications, oral interviews (documented) | ✅ สำหรับ primary evidence ในงานศิลปะ |
| **❌** | Predatory / Unverifiable | Predatory journals, AI-generated references, anonymous internet sources | ❌ ห้ามใช้ |

⚠️ **IRON RULE — GRAY ZONE = FAIL**: source ที่ไม่สามารถยืนยันได้ว่าเป็น Tier 1-3 = ❌

---

## 2. Arts Research Failure Modes (7 Patterns)

ทุก skill และ agent ต้องตระหนักถึง failure modes เหล่านี้:

| Code | ชื่อ | อาการ | Test |
|------|-----|-------|------|
| **FM-A** | Decorative Theory | cite ทฤษฎีแต่ไม่ใช้ใน analysis | ตัดชื่อทฤษฎีออก — argument ยังเดินไหม? |
| **FM-B** | Catalog Description | บรรยายผลงานโดยไม่วิเคราะห์ | หา interpretive moves |
| **FM-C** | Thai Cultural Essentialism | "ศิลปะไทยทั้งหมด X" แบบเหมารวม | ตรวจ categorical statements |
| **FM-D** | Western Frame Imposition | ใช้กรอบตะวันตกกับงานไทยโดยไม่ reflect | framework ตรงบริบทไหม? |
| **FM-E** | Unverified References | AI-generated citations | random sample 3-5 → search จริง |
| **FM-F** | Practice-Research Confusion | ไม่แยก creative work กับ knowledge contribution | ระบุ "what practice contributes to knowledge"? |
| **FM-G** | Missing Cultural Sensitivity | ใช้ภาพ/ข้อมูลชุมชนไม่มี consent | attribution + permission ครบไหม? |

---

## 3. Iron Rules (Global)

Iron Rules เหล่านี้ใช้กับ agent ทุกตัวในทุก skill:

| Code | Rule | Scope |
|------|------|-------|
| **IR-1** | ห้ามแก้ไข manuscript โดยตรง — output เป็น report เท่านั้น | All reviewer agents |
| **IR-2** | Source Tier ❌ = ห้ามใช้ ไม่ว่ากรณีใด | All research agents |
| **IR-3** | DA CRITICAL → Editorial Decision ≠ Accept | arts-paper-reviewer |
| **IR-4** | ห้าม rubber-stamp re-review — ตรวจ manuscript จริง | arts-paper-reviewer |
| **IR-5** | Anti-leakage protocol ต้องรัน ทุก revision | arts-paper-writer |
| **IR-6** | Thai + English abstract ต้องมี content ตรงกัน | arts-paper-writer |
| **IR-7** | Integrity Gates ห้ามข้าม | arts-research-pipeline |
| **IR-8** | Research Passport ต้องอัปเดตทุก checkpoint | arts-research-pipeline |
| **IR-9** | FONER failure = ห้ามเริ่มเขียนบทความ | arts-deep-research |
| **IR-10** | Cultural consent required ก่อน involve ชุมชน/มรดก | All arts skills |

---

## 4. Checkpoint Definitions

| Type | คำนิยาม | ใช้เมื่อ |
|------|---------|--------|
| **FULL** | สรุปครบ + artifacts + next steps + risk check | งานซับซ้อน, stage สำคัญ, ครั้งแรก |
| **SLIM** | สรุปสั้น 3-5 bullet + next step เดียว | งานตรงไปตรงมา, user เชี่ยวชาญ |
| **MANDATORY** | ตรวจทุกข้อใน checklist — ห้ามข้าม | Integrity Gates, submission |

---

## 5. Priority Levels (Reviewer Comments & Tasks)

| Priority | นิยาม | Action |
|---------|------|--------|
| **P1** | ต้องแก้ไขก่อน submit — ถ้าไม่แก้ = Reject | แก้ทันที ก่อน P2 |
| **P2** | ควรแก้ไข — ทำให้งานแข็งแกร่งขึ้น | แก้หลัง P1 |
| **P3** | Optional — ผู้เขียนอาจ disagree ได้ | พิจารณา แต่ไม่บังคับ |

---

## 6. FONER Framework (Research Question Assessment)

ใช้ทุกครั้งที่ต้องประเมิน RQ:

| Criterion | คำถาม | Pass Condition |
|-----------|-------|--------------|
| **F** — Feasible | ทำได้จริงด้วย resources ที่มี? | YES + มี method ที่ชัดเจน |
| **O** — Original | เพิ่มอะไรใหม่ที่ยังไม่มี? | YES + gap ระบุได้ใน lit |
| **N** — Narratable | เล่าเป็น coherent story ได้? | YES + argument structure ชัด |
| **E** — Ethical | ไม่ละเมิด ethical standards? | YES + consent/attribution ครบ |
| **R** — Relevant | สำคัญต่อสาขา/ชุมชน/นโยบาย? | YES + significance ระบุได้ |

**FONER FAIL** (ข้อใดข้อหนึ่ง F) → ห้ามเริ่มเขียนบทความ

---

## 7. Analysis Levels (Visual & Content Analysis)

ทุก analysis ในงานศิลปะควรมีครบ 3 ระดับ:

| Level | คำนิยาม | คำถาม |
|-------|---------|-------|
| **1 — Description** | บรรยาย objective สิ่งที่เห็น/ได้ยิน | "อะไรอยู่ตรงหน้าเรา?" |
| **2 — Analysis** | แยกแยะ components, patterns, relationships | "ทำงานอย่างไร?" |
| **3 — Interpretation** | ความหมาย, นัยยะ (มีหลักฐาน) | "หมายความว่าอะไร?" |

ห้ามข้าม Level 1 → Level 3 โดยตรง

---

## 8. TCI Compliance Requirements

Requirements เหล่านี้ใช้กับทุกงานที่ target TCI journal:

| ข้อกำหนด | Detail |
|---------|--------|
| Abstract ภาษาไทย | 200-300 คำ |
| Abstract ภาษาอังกฤษ | 200-300 คำ — content ตรงกับภาษาไทย |
| Keywords ภาษาไทย | 5-7 คำ |
| Keywords ภาษาอังกฤษ | 5-7 คำ |
| ชื่อผู้แต่ง | ทั้งสองภาษา |
| Affiliation | ครบทุกผู้แต่ง |
| Conflict of interest | บังคับ |
| AI disclosure | บังคับ ถ้าใช้ AI |
| Citation format | ตาม journal style guide |
