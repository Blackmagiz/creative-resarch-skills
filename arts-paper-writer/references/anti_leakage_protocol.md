---
name: anti_leakage_protocol
purpose: ป้องกัน revision ทำให้เกิดปัญหาใหม่ในขณะแก้ปัญหาเก่า
parent_skill: arts-paper-writer
version: 2.0.0
---

# Anti-Leakage Protocol

## ปัญหา

การแก้ไขบทความตาม reviewer comments มักทำให้เกิด "revision leak" คือ:
- แก้ Introduction แต่ทำให้ Conclusion ไม่สอดคล้องกันอีกต่อไป
- เพิ่ม evidence ใน Analysis แต่ไม่ update Discussion
- เปลี่ยน RQ แต่ไม่แก้ Keywords และ Methodology
- แก้ theory framework แต่ไม่แก้ Lit Review

---

## Dependency Map

ทุก section มี upstream (สิ่งที่ขึ้นกับ) และ downstream (สิ่งที่ส่งผลต่อ):

```
Abstract ←→ ทุก section (mirror ทั้งหมด)
    ↑
Title → Keywords → [ไม่มี downstream]

Introduction (RQ/objectives)
    ↓
Literature Review (gap ที่ RQ จะตอบ)
    ↓
Methodology (method ที่เหมาะกับ RQ)
    ↓
Analysis/Findings (ตอบ RQ)
    ↓
Discussion (เชื่อมกลับ lit, นัยยะ)
    ↓
Conclusion (ตอบ RQ โดยตรง)
```

---

## Leakage Check Protocol

เรียกใช้ protocol นี้ **ทุกครั้ง** ที่ revision_coach_agent แก้ไข section:

### Step 1: Identify Changed Section

```
ฉันเพิ่งแก้ไข: [Section Name]
```

### Step 2: Check Downstream Sections

ดู Downstream Checklist ตาม section ที่แก้:

| Section ที่แก้ | Sections ที่ต้องตรวจ downstream |
|-------------|-------------------------------|
| Title | Keywords, Abstract (ทั้งสองภาษา) |
| Abstract | ตรวจ alignment ระหว่าง Thai/English |
| Introduction | Literature Review (gap ยังตรงไหม), Conclusion (RQ ตรงกันไหม) |
| RQ (ใน Intro) | Methodology, Analysis headings, Discussion, Conclusion, Abstract |
| Literature Review | Introduction gap statement, Discussion (เชื่อมกลับ lit) |
| Methodology | Analysis (method ที่ใช้ตรงกัน), Limitations ใน Discussion |
| Analysis/Findings | Discussion (findings ครบไหม), Conclusion (สรุปตรง) |
| Discussion | Conclusion (ไม่ขัดแย้ง), Limitations (consistent) |
| Conclusion | Abstract (implication ยังตรง) |
| References | Citation keys ใน text ยังตรงไหม |

### Step 3: Spot-Check Each Downstream Section

สำหรับแต่ละ section ที่ต้องตรวจ:
```
Q: [Section X] ยังสอดคล้องกับการเปลี่ยนแปลงใน [Section Y] ไหม?
A: ✅ ยังสอดคล้อง / ❌ ไม่สอดคล้อง → ต้องแก้ด้วย
```

### Step 4: Log Result

```markdown
## Anti-Leakage Check Log

**Revision**: [Comment ID] — [ย่อ description]
**Section changed**: [Section name]
**Downstream sections checked**:
| Section | Status | Action needed |
|---------|--------|--------------|
| [Section A] | ✅ | — |
| [Section B] | ❌ | [แก้อะไร] |

**Leakage found**: ✅ None / ⚠️ [n] sections need update
```

---

## Common Leakage Scenarios

### Scenario 1: RQ Changed

**Triggered by**: reviewer comment ว่า RQ ไม่ชัดเจน → author reframe RQ

**Must check**:
- [ ] Abstract (ทั้งสองภาษา) — update RQ statement
- [ ] Keywords — ยังตรงกับ revised RQ?
- [ ] Methodology — method ยัง appropriate กับ new RQ?
- [ ] Analysis headings — ยังตอบ new RQ?
- [ ] Discussion — implications ยังตรง?
- [ ] Conclusion — ตอบ new RQ โดยตรง?

---

### Scenario 2: Added New Evidence / Source

**Triggered by**: reviewer ขอให้เพิ่ม evidence หรือ canonical reference

**Must check**:
- [ ] Lit Review — เพิ่ม source ใน correct thematic cluster?
- [ ] References list — เพิ่ม full citation แล้วหรือยัง?
- [ ] Discussion — ถ้า source เปลี่ยน argument ต้องอัปเดต discussion ด้วย?
- [ ] In-text citations — format ถูกต้อง consistent ไหม?

---

### Scenario 3: Weakened or Removed Claim

**Triggered by**: DA CRITICAL — overclaim / ไม่มีหลักฐาน

**Must check**:
- [ ] Discussion — ถ้า claim ถูก scale down, implication ยัง valid ไหม?
- [ ] Conclusion — สรุปยังตรงกับ revised claim?
- [ ] Abstract — implication statement ยัง accurate ไหม?

---

### Scenario 4: Changed Theoretical Framework

**Triggered by**: reviewer ว่า theory ไม่ fit หรือ เป็น Decorative Theory

**Must check**:
- [ ] Introduction — theoretical framework introduction ยังตรง?
- [ ] Lit Review — งานที่เกี่ยวกับ new framework ครบไหม?
- [ ] Methodology — analysis framework section อัปเดตแล้วไหม?
- [ ] Analysis — ใช้ new framework จริงในการวิเคราะห์ไหม?
- [ ] Discussion — implications ตาม new framework ยัง consistent?

---

## Iron Rule

⚠️ **IRON RULE**: revision_coach_agent ต้องรัน anti_leakage_protocol ทุก revision ก่อนส่ง output ห้าม shortcut โดยบอกว่า "revision นี้ isolated ไม่กระทบ section อื่น" — ต้องตรวจทุกครั้งเสมอ
