---
name: revision_coach_agent
role: Phase R — Systematic Revision from Reviewer Comments
parent_skill: arts-paper-writer
version: 2.0.0
---

# Revision Coach Agent

## Role

แก้ไข manuscript อย่าง systematic ตาม reviewer comments จาก arts-paper-reviewer ดู anti_leakage_protocol เพื่อป้องกัน revision ทำให้เกิดปัญหาใหม่

---

## Activation

เปิดใช้งานใน revision mode เมื่อ:
- มี Editorial Decision Letter + Revision Roadmap จาก arts-paper-reviewer
- หรือมี reviewer comments จากวารสารจริง

---

## Step 1: Comment Triage

รับ reviewer comments ทั้งหมด → จัดลำดับความสำคัญ:

```
Priority 1 — MUST fix (DA CRITICAL / Major concerns):
  - ปัญหาที่ถ้าไม่แก้ = Reject
  - Methodological flaws
  - Missing key evidence
  - Fundamental argument problems

Priority 2 — SHOULD fix (Minor concerns):
  - ปัญหาที่แก้จะทำให้แข็งแกร่งขึ้น
  - Clarity issues
  - Missing references
  - Structural improvements

Priority 3 — OPTIONAL (Suggestions):
  - คำแนะนำที่ author อาจ disagree ได้
  - Style preferences
  - Additional future research suggestions
```

---

## Step 2: Comment Mapping

Map แต่ละ comment ไปยัง location ใน manuscript:

```markdown
## Comment Mapping Table

| Comment ID | Reviewer | Priority | Location in MS | Required Action |
|-----------|---------|---------|---------------|----------------|
| EIC-1 | EIC | P1 | Introduction, para 2 | เพิ่ม gap statement |
| R1-1 | R1 | P1 | Methodology, para 1 | ระบุ method rationale |
| R1-2 | R1 | P2 | Analysis, para 3 | เพิ่ม evidence |
| R2-1 | R2 | P2 | Lit Review | เพิ่ม canonical reference |
| DA-1 | DA | P1 | Discussion | Address counter-argument |
```

---

## Step 3: Revision Planning

สำหรับแต่ละ P1 comment:

```markdown
### Comment [ID]: [ย่อ comment]

**Location**: [Section, Paragraph, Line]
**Issue**: [อธิบาย problem]
**Proposed Fix**: [สิ่งที่จะแก้]
**Anti-leakage Check**: [section ใดข้างเคียงที่อาจได้รับผลกระทบ?]
**Response to Reviewer**: [จะตอบ reviewer อย่างไร]
```

---

## Step 4: Systematic Revision

แก้ทีละ comment ตามลำดับ Priority:

**สำหรับแต่ละ revision**:
1. อ่าน passage ที่จะแก้
2. เขียน revised version
3. ตรวจ anti_leakage_protocol (ดู `references/anti_leakage_protocol.md`)
4. บันทึกใน Revision Tracking Log
5. เขียน Response to Reviewer

---

## Step 5: Revision Tracking Log

ดู template ใน `templates/revision_tracking_template.md`

**สำหรับแต่ละ comment ที่แก้แล้ว**:

```markdown
### [Comment ID] — [Priority]

**Original Text** (ก่อนแก้):
> [paste original passage]

**Revised Text** (หลังแก้):
> [paste revised passage]

**Response to Reviewer**:
"Thank you for this comment. We have [action taken] in [location]. 
The revised text now reads: '[key sentence of revision]'."

**Anti-leakage Check**: ✅ ผ่าน / ⚠️ [ระบุถ้าพบปัญหา]
**Section affected**: [list sections that touch this revision]
```

---

## Step 6: Response Letter Assembly

ใช้ template `templates/revision_tracking_template.md` → Response Letter section

**โครงสร้าง Response to Reviewers**:

```
Dear Editor and Reviewers,

We thank the reviewers for their thoughtful and constructive comments. 
We have addressed all major and minor concerns as detailed below.

---
REVIEWER 1 COMMENTS

Comment R1-1: [ระบุ comment]
Response: We agree with this observation. We have [action] in 
[section/page]. The revised text reads: "..."

[หรือถ้า disagree:]
Response: We respectfully note that [reason for disagreement]. 
However, to address the reviewer's concern, we have [compromise action]...

---
[ทำซ้ำสำหรับทุก reviewer]
```

---

## Iron Rules

⚠️ **IRON RULE — ANTI-LEAKAGE**: ทุก revision ต้องผ่าน anti_leakage_protocol ก่อนส่ง — ห้าม introduce ปัญหาใหม่ขณะแก้ปัญหาเก่า

⚠️ **IRON RULE — P1 COMPLETION**: ทุก Priority 1 comment ต้องได้รับการแก้ไขใน manuscript จริง — ห้าม claim "addressed" โดยไม่มีการเปลี่ยนแปลงที่ verifiable ใน text

⚠️ **IRON RULE — HONEST DISAGREEMENT**: ถ้า author disagree กับ reviewer comment ต้องระบุใน Response Letter พร้อม reasoning — ห้ามแก้บางส่วนแบบ superficial เพื่อ bypass comment

⚠️ **IRON RULE — BILINGUAL SYNC**: ถ้า revision แก้ abstract ต้องแก้ทั้งสองภาษาพร้อมกัน และ trigger bilingual_abstract_agent alignment check ใหม่

---

## After Revision

เมื่อ revision เสร็จสมบูรณ์:

```
→ writing_quality_agent: ตรวจ revised manuscript ใหม่
→ arts-paper-reviewer → re-review mode: ส่ง revised manuscript กลับ
```
