---
name: revision_tracking_template
purpose: Log การ revise ตาม reviewer comments + Response to Reviewers letter
parent_skill: arts-paper-writer
version: 2.0.0
---

# Revision Tracking Template

---

## Cover Page

```
Manuscript Title: [ชื่อบทความ]
Manuscript ID: [ถ้ามี]
Journal: [ชื่อวารสาร]
Date of Submission (original): 
Date of Decision: 
Decision: □ Minor Revision  □ Major Revision
Date of Revised Submission: 
Authors: 
```

---

## Response to Reviewers Letter

```
Dear Editor and Reviewers,

We sincerely thank the reviewers for their thorough and constructive 
comments. We have carefully addressed all concerns as detailed below. 
All changes in the revised manuscript are highlighted in [track changes / 
yellow highlight / bold text] for easy reference.

We provide a point-by-point response to each comment, using the 
following format:
  REVIEWER COMMENT: [quoted comment]
  AUTHOR RESPONSE: [our response]
  CHANGE IN MANUSCRIPT: [what was changed, where]

We hope the revised manuscript now meets the journal's standards.

Sincerely,
[Author names]
```

---

## Revision Log

### Editor-in-Chief (EIC) Comments

---

#### EIC Comment 1

**REVIEWER COMMENT**:
> [วาง comment ของ EIC ตรงนี้]

**Priority**: □ P1 — Must fix  □ P2 — Should fix  □ P3 — Optional

**AUTHOR RESPONSE**:
> [We agree with / We respectfully note that...]
> [อธิบายสิ่งที่ทำ]

**CHANGE IN MANUSCRIPT**:
> Section: [ชื่อ section]
> Location: [paragraph / line]
> 
> **Original text**:
> "[paste ข้อความเดิม]"
> 
> **Revised text**:
> "[paste ข้อความใหม่]"

**Anti-leakage Check**: ✅ ผ่าน / ⚠️ [sections ที่ต้องแก้ตาม]

---

#### EIC Comment 2

**REVIEWER COMMENT**:
> [...]

*(ทำซ้ำสำหรับทุก EIC comment)*

---

### Reviewer 1 (R1 — Methodology) Comments

---

#### R1 Comment 1

**REVIEWER COMMENT**:
> [...]

**Priority**: □ P1  □ P2  □ P3

**AUTHOR RESPONSE**:
> [...]

**CHANGE IN MANUSCRIPT**:
> Section: 
> Original: "[...]"
> Revised: "[...]"

**Anti-leakage Check**: ✅ / ⚠️

---

*(ทำซ้ำ pattern สำหรับ R1 Comment 2, 3, ...)*

---

### Reviewer 2 (R2 — Domain Expert) Comments

*(pattern เดียวกัน)*

---

### Reviewer 3 (R3 — Cross-disciplinary) Comments

*(pattern เดียวกัน)*

---

### Devil's Advocate (DA) Comments

---

#### DA Comment 1 [CRITICAL]

**REVIEWER COMMENT**:
> [DA CRITICAL comment — ต้องแก้ไม่ว่ากรณีใด]

**Priority**: P1 — CRITICAL (DA CRITICAL blocks Accept)

**AUTHOR RESPONSE**:
> [...]

**CHANGE IN MANUSCRIPT**:
> [...]

**Anti-leakage Check**: ✅ / ⚠️

---

## Summary Table (for editorial office)

| Comment ID | Reviewer | Priority | Status | Location in MS |
|-----------|---------|---------|--------|---------------|
| EIC-1 | EIC | P1 | ✅ Done | Introduction, para 2 |
| EIC-2 | EIC | P2 | ✅ Done | Abstract |
| R1-1 | R1 | P1 | ✅ Done | Methodology |
| R1-2 | R1 | P2 | ✅ Done | Analysis, para 3 |
| R2-1 | R2 | P1 | ✅ Done | Lit Review |
| R3-1 | R3 | P2 | ✅ Done | Discussion |
| DA-1 | DA | P1 CRITICAL | ✅ Done | Discussion, para 4 |

**Total P1 comments**: [n] — **All addressed**: ✅ / ❌ [n remaining]
**Total P2 comments**: [n] — **Addressed**: [n/n]
**Total P3 comments**: [n] — **Addressed**: [n/n] (optional)

---

## Revision Completeness Checklist

- [ ] ทุก P1 comment ได้รับการแก้ไขใน manuscript จริง
- [ ] ทุก DA CRITICAL comment ได้รับการแก้ไข
- [ ] Anti-leakage check ผ่านทุก revision
- [ ] Abstract (ทั้งสองภาษา) อัปเดตถ้า findings/RQ เปลี่ยน
- [ ] References เพิ่มตาม reviewer requests
- [ ] Track changes / highlights ทำแล้วใน revised manuscript
- [ ] Response Letter ครบทุก comment
- [ ] Revised manuscript + Response Letter พร้อม submit

---

## Template: Handling Disagreement

ถ้า author ไม่เห็นด้วยกับ reviewer comment:

```
REVIEWER COMMENT:
> [comment ที่ author ไม่เห็นด้วย]

AUTHOR RESPONSE:
We appreciate the reviewer's perspective on this point. However, we 
respectfully offer an alternative view: [เหตุผลที่ไม่เห็นด้วย + หลักฐาน]

To address the reviewer's underlying concern, we have [compromise action]:
[อธิบาย compromise ที่ทำ]

We hope this revision satisfactorily addresses the reviewer's concern 
while maintaining the integrity of our [argument/finding/method].

CHANGE IN MANUSCRIPT:
Section: [...]
[บรรยาย compromise change ที่ทำ]
```

**หมายเหตุ**: ห้าม disagree โดยไม่ทำ compromise change ใดเลย — ต้องแสดงว่า acknowledge ความกังวลของ reviewer

---

## Template: Handling "No Change Needed"

สำหรับ P3 comments ที่ author ตัดสินใจไม่แก้:

```
REVIEWER COMMENT:
> [P3 suggestion]

AUTHOR RESPONSE:
We thank the reviewer for this suggestion. After careful consideration, 
we have decided not to incorporate this change because [clear reason].

[ถ้ายอมรับ suggestion บางส่วน:]
However, we have [partial action] to partially address this concern.

CHANGE IN MANUSCRIPT: No change (or: Minor clarification added in [section])
```
