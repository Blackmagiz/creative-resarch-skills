---
name: re_review_protocol
purpose: โปรโตคอลสำหรับ re-review mode — ตรวจว่า revision ตอบ comments ครบไหม
---

# Re-Review Protocol (Verification Review)

## ภาพรวม

Re-review mode ใช้หลัง author ส่ง revised manuscript มา เป้าหมายคือตรวจ**อย่างเป็นระบบ**ว่า revision แก้ไขปัญหาที่ระบุใน Revision Roadmap ครบหรือไม่ และมีปัญหาใหม่เกิดขึ้นจากการแก้ไขหรือไม่

## Input ที่ต้องการ

1. **Revision Roadmap** จาก review ครั้งแรก (Priority 1, 2, 3)
2. **Revised manuscript** ฉบับใหม่
3. **Response to Reviewers letter** (ถ้ามี — ช่วยให้ตรวจได้เร็วขึ้น)

## R&R Traceability Matrix (แก่นของ re-review)

สร้างตารางนี้สำหรับทุกปัญหาใน Priority 1 (บังคับ) และ Priority 2 (ตรวจตามสมควร):

| # | ปัญหาจาก Review ครั้งแรก | Reviewer | Priority | Author's Response (จาก letter) | ตรวจใน manuscript | ผล |
|---|--------------------------|----------|----------|-------------------------------|------------------|----|
| 1 | [ปัญหา] | [R1/R2/DA] | P1 | "[quote จาก response letter]" | [section/page] | ✅ Addressed / ⚠️ Partial / ❌ Not addressed |

## เกณฑ์การตัดสิน

### ✅ Addressed (แก้แล้ว)
- ปัญหาถูกแก้ตรงประเด็น
- หลักฐานใน revised manuscript ชัดเจน
- ไม่สร้างปัญหาใหม่จากการแก้

### ⚠️ Partially Addressed (แก้บางส่วน)
- แก้บางส่วนของปัญหาแต่ยังไม่ครบ
- หรือแก้แล้วแต่ยังต้องชี้แจงเพิ่ม
- → ยังต้องแก้ใน revision ถัดไป

### ❌ Not Addressed (ไม่ได้แก้)
- ปัญหาที่ Priority 1 ไม่ได้แก้ไขเลย → Major concern ต่อเนื่อง
- หรือแก้ผิดทิศทาง

## ปัญหาใหม่จากการแก้ไข

การแก้ไขบางครั้งสร้างปัญหาใหม่ Re-review ต้องตรวจ:
- มีส่วนที่ผู้เขียนเพิ่มเข้ามาแล้วมีปัญหาใหม่ไหม?
- Structure เปลี่ยนแล้ว coherence ลดลงไหม?
- References ใหม่ที่เพิ่มมาถูกต้องไหม?

## Output ของ Re-review

```markdown
# Re-Review Report (Verification Review)

**บทความ**: [ชื่อ]
**Re-review โดย**: EIC + Editorial Synthesizer
**คำตัดสิน**: [Accept / Minor Revision เพิ่มเติม / Major Revision ต่อเนื่อง]

## R&R Traceability Matrix
[ตารางตามรูปแบบข้างต้น]

## สรุป

- Priority 1 ที่แก้แล้ว: X/Y items
- Priority 1 ที่ยังไม่แก้: [ระบุ]
- ปัญหาใหม่ที่พบ: [ระบุถ้ามี]

## คำตัดสิน

[Accept]: ปัญหาสำคัญทั้งหมดได้รับการแก้ไข
[Minor Revision]: มีปัญหาเล็กน้อยที่ยังค้างอยู่ → ระบุ
[Major Revision]: Priority 1 บางข้อยังไม่ได้แก้ หรือมีปัญหาใหม่สำคัญ → ระบุ

## ขั้นตอนถัดไป
[ระบุชัดเจน]
```

## ⚠️ IRON RULE

Re-review ห้าม "rubber stamp" — ทุก Priority 1 item ต้องตรวจสอบอย่างอิสระใน manuscript จริง ไม่ใช่เชื่อตาม Response to Reviewers letter เพียงอย่างเดียว
