---
name: writing_quality_check
purpose: เกณฑ์ตรวจคุณภาพงานเขียน 7 dimensions พร้อม scoring rubrics
parent_skill: arts-paper-writer
version: 2.0.0
---

# Writing Quality Check — Detailed Rubrics

## Anti-Pattern Rubrics (ดู writing_quality_agent.md สำหรับ overview)

### Pattern A: Art Talk Without Rigor

**คำอธิบาย**: ใช้ภาษาที่ฟังดูมี aesthetic แต่ไม่มี argument ที่ analyzable หรือ falsifiable

**Severity 0** (ไม่พบ):
- ทุกประโยคมี specific, analyzable claim

**Severity 1** (เล็กน้อย):
- 1-2 ประโยค evocative เกินไป แต่ argument โดยรวมยังชัด
- ตัวอย่าง: "งานชิ้นนี้มีพลังงานเฉพาะตัว" (ประโยคเดียว ก่อน specific analysis)

**Severity 2** (ปานกลาง):
- ย่อหน้าหนึ่งเป็น "art talk" ทั้งย่อหน้า
- ตัวอย่าง: "ความงามที่หลั่งไหลซ่านไปทั่วผืนผ้าใบ สะท้อนถึงวิญญาณของศิลปิน..."

**Severity 3** (รุนแรง):
- Section ทั้ง section เป็น art talk โดยไม่มี analyzable content
- ไม่สามารถ extract specific claims ได้เลย

**Test**: ตัดคำ/วลีที่ evocative ออก — ยังมี argument ที่ analyzable เหลืออยู่ไหม?

---

### Pattern B: Description-Only

**คำอธิบาย**: บรรยายผลงาน/ข้อมูลโดยไม่ทำ analysis หรือ interpretation

**Test**: ย่อหน้านี้มี interpretive move ไหม? (ความหมาย, นัยยะ, significance)

**Severity 0**: ทุกย่อหน้า Analysis มี Description → Analysis → Interpretation

**Severity 1**: มี 1-2 ย่อหน้าที่บรรยายอย่างเดียว ในงานที่ analysis โดยรวมดี

**Severity 2**: Section Analysis มีย่อหน้าที่บรรยายอย่างเดียวมากกว่าครึ่ง

**Severity 3**: Section Analysis เป็นการบรรยายตลอดโดยไม่มี interpretation เลย

---

### Pattern C: Decorative Theory

**คำอธิบาย**: cite ทฤษฎี/นักทฤษฎีโดยไม่ได้ใช้ทฤษฎีนั้นใน analysis จริง

**Test**: ตัดชื่อนักทฤษฎีและชื่อทฤษฎีออก — argument ยังเดินได้ไหม? ถ้าใช่ = Decorative

**Severity 0**: ทุกทฤษฎีที่ cite ถูกใช้ใน analysis อย่างชัดเจน

**Severity 1**: 1 ทฤษฎีที่ mention แล้วไม่ได้ใช้ในรายละเอียด

**Severity 2**: 2-3 ทฤษฎีที่ name-drop โดยไม่ได้ใช้จริง

**Severity 3**: Framework section มีทฤษฎีมากมายแต่ Analysis ไม่ได้ใช้สักทฤษฎี

---

### Pattern D: Overclaim

**คำอธิบาย**: claims ที่ขอบเขตเกินกว่าหลักฐานที่มี

**Test signals**:
- "เปลี่ยนวงการ" / "เป็นครั้งแรก" / "ทั้งหมด" / "พิสูจน์ว่า"
- Scope เกินกว่า sample ที่ศึกษา (เช่น ศึกษา 3 ชิ้น → claim "งานศิลปะไทยทั้งหมด")

**Severity 0**: ทุก claim มี hedge ที่เหมาะสม (suggests, indicates, in this case)

**Severity 1**: 1-2 overclaim เล็กน้อย ที่แก้ได้ด้วย hedging

**Severity 2**: หลาย overclaim ใน Discussion หรือ Conclusion

**Severity 3**: Contribution claims ใน Abstract/Conclusion ไม่สัมพันธ์กับ evidence เลย

---

### Pattern E: Thai Cultural Essentialism

**คำอธิบาย**: กล่าวถึง "ศิลปะไทย" / "วัฒนธรรมไทย" แบบเหมารวมโดยไม่ระบุ specificity

**Test signals**:
- "ศิลปะไทยมีลักษณะ X" (โดยไม่ระบุ period, region, school)
- "คนไทยมองว่า..." (generalizing ethnicity)
- "ความเป็นไทย" เป็น monolithic concept

**Severity 0**: ทุก statement เกี่ยวกับวัฒนธรรมไทยระบุ context ที่ specific

**Severity 1**: 1-2 statements กว้างไป แต่แก้ได้ด้วยการเพิ่ม qualifier

**Severity 2**: Pattern นี้ปรากฏทั่วไปใน Introduction หรือ Conclusion

**Severity 3**: Thesis หลักของงานอาศัย essentialist claim โดยไม่ problematize

---

### Pattern F: Bilingual Drift

**คำอธิบาย**: Thai abstract และ English abstract มีเนื้อหาไม่ตรงกัน

**ตรวจ element ต่อ element ตาม bilingual_abstract_agent alignment table**

**Severity 0**: ทุก element align ครบ

**Severity 1**: เนื้อหาตรงกัน แต่ emphasis ต่างกันเล็กน้อย

**Severity 2**: 1-2 element ขาดใน abstract ภาษาใดภาษาหนึ่ง

**Severity 3**: Findings หรือ Implication ใน Thai abstract ≠ English abstract

---

### Pattern G: Leaky Revision

**คำอธิบาย**: revision แก้ comment ข้อหนึ่ง แต่ทำให้ section อื่นไม่ consistent

**ใช้ Dependency Map จาก anti_leakage_protocol.md ในการตรวจ**

**Severity 0**: ผ่าน anti_leakage_protocol ทุกข้อ

**Severity 1**: Minor inconsistency เล็กน้อย (เช่น terminology ต่างกัน)

**Severity 2**: 1-2 sections ไม่ consistent หลัง revision

**Severity 3**: RQ หรือ argument หลักไม่ consistent ระหว่าง sections

---

## Scoring Summary

| Anti-Pattern | Max | Score | Weight |
|-------------|-----|-------|--------|
| A: Art Talk | 3 | — | Critical |
| B: Description-Only | 3 | — | Critical |
| C: Decorative Theory | 3 | — | High |
| D: Overclaim | 3 | — | High |
| E: Essentialism | 3 | — | High |
| F: Bilingual Drift | 3 | — | Critical (TCI) |
| G: Leaky Revision | 3 | — | Critical |
| **Total** | **21** | **—** | |

**Thresholds**:
- 0-6: ✅ PASS
- 7-14: ⚠️ CAUTION — address before submission
- 15-21: ❌ FAIL — major revision required

**Single-dimension FAIL rule**: ถ้า dimension ใดได้ score 3 (รุนแรง) → ต้องแก้ไขก่อน ไม่ว่า total score จะเท่าไหร่
