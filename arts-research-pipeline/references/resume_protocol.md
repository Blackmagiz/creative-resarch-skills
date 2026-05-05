---
name: resume_protocol
purpose: โปรโตคอลกลับมาทำงานต่อหลัง pipeline หยุดชะงัก
parent_skill: arts-research-pipeline
version: 2.0.0
---

# Resume Protocol — Pipeline Stall Recovery

## เมื่อไหร่ใช้ Protocol นี้

- ผู้ใช้กลับมาหลังหยุดพักนาน (> 2 สัปดาห์)
- ขอ "ทำต่อจากที่หยุด" โดยไม่รู้ว่าหยุดตรงไหน
- Session ใหม่ที่ต้องการ context จาก session เก่า

---

## Step 1: Research Passport Retrieval

ถามผู้ใช้:
```
"มี Research Passport หรือเอกสาร progress ที่ทำไว้ก่อนหน้าไหม? 
ถ้ามี: แชร์มาได้เลย
ถ้าไม่มี: บอกว่า
  (a) หัวข้อวิจัยคืออะไร?
  (b) ครั้งสุดท้ายทำถึงขั้นตอนไหน?
  (c) มีไฟล์อะไรบ้างที่ทำไปแล้ว?"
```

---

## Step 2: State Reconstruction

สร้าง State Summary จากข้อมูลที่มี:

```markdown
## State Reconstruction

**Project**: [title]
**Last known stage**: [Stage N — ชื่อ]
**Materials confirmed available**:
- [ ] RQ document
- [ ] Literature Matrix
- [ ] Draft manuscript
- [ ] Review decision
- [ ] Revised manuscript

**Materials missing**:
- [ ] [list ที่ขาด]

**Estimated stage completion**:
| Stage | Status |
|-------|--------|
| 1: PLAN | ✅/⏳/❓ |
| 2: RESEARCH | ✅/⏳/❓ |
| 3: METHOD | ✅/⏳/❓ |
| 4: WRITE | ✅/⏳/❓ |
| 5: REVIEW | ✅/⏳/❓ |
| 6: REVISE | ✅/⏳/❓ |
| 7: VERIFY | ✅/⏳/❓ |
| 8: FINALIZE | ✅/⏳/❓ |
```

---

## Step 3: Material Freshness Check

ตรวจว่า materials ที่มีอยู่ยังใช้ได้หรือ outdated:

| Material | ตรวจ | Action ถ้า outdated |
|---------|-----|------------------|
| Literature Matrix | Sources > 2 ปี จำนวนมาก? | arts-deep-research → update search |
| Draft manuscript | ยังตอบ RQ ที่ตกลงไว้ไหม? | Re-confirm RQ ก่อน resume writing |
| Reviewer comments | มีวันหมดเวลา submission? | ตรวจ journal deadline |

---

## Step 4: Resume Plan

สร้าง Resume Plan สำหรับผู้ใช้:

```markdown
## Resume Plan

**กลับมาทำที่**: Stage [N] — [ชื่อ stage]
**เหตุผล**: [stage ก่อนหน้าเสร็จแล้ว / stage นี้ค้างอยู่กลางทาง]

**สิ่งที่ต้องทำก่อน resume**:
1. [ถ้า literature outdated]: update literature search
2. [ถ้า RQ เปลี่ยน]: FONER re-assessment
3. [ถ้า draft ค้างกลางทาง]: summary สิ่งที่เขียนไปแล้ว

**Resume action**:
→ [skill ที่จะเรียก + mode]
→ [input ที่ต้องใช้]
```

---

## Step 5: Research Passport Update

สร้าง/อัปเดต Research Passport พร้อม resume date

⚠️ **IRON RULE**: ห้าม assume ว่า stage ที่ผ่านมาเสร็จสมบูรณ์โดยไม่ verify กับ materials จริง
