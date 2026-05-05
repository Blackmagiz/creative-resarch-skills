---
name: handoff_protocol
purpose: โปรโตคอลส่งต่อข้อมูลจาก arts-deep-research ไปยัง arts-paper-writer
---

# Handoff Protocol: arts-deep-research → arts-paper-writer

## ภาพรวม

หลังจาก arts-deep-research เสร็จสิ้น ผลลัพธ์สามารถส่งต่อให้ arts-paper-writer ได้โดยตรง ทำให้ arts-paper-writer ไม่ต้องทำ literature search ซ้ำ

## Materials ที่ส่งต่อ

| Material | จาก Agent | ใช้ใน arts-paper-writer |
|----------|----------|------------------------|
| Research Question Brief | research_question_agent | ข้ามขั้นตอน RQ scoping |
| Source Quality Matrix | source_verification_agent | ข้ามขั้นตอน literature search |
| Literature Synthesis | synthesis_agent | ใช้ตรงใน Literature Review section |
| INSIGHT Collection (Socratic) | socratic_mentor_agent | inform introduction + theoretical framework |

## Trigger

ผู้ใช้พูดว่า:
- "ช่วยเขียนบทความจากที่วิจัยมา"
- "ต่อด้วยการเขียนเลย"
- "handoff ไปที่ paper writer"

## กระบวนการ Handoff

```
1. arts-deep-research สรุป Research Package:
   - RQ Brief
   - Verified Source Matrix
   - Literature Synthesis
   - [ถ้ามี] INSIGHT Collection

2. แสดง Research Package ให้ผู้ใช้ confirm

3. ส่งต่อไปยัง arts-paper-writer
   → intake_agent ของ arts-paper-writer ตรวจว่ามี materials อะไรแล้วบ้าง
   → ข้ามขั้นตอนที่มีข้อมูลแล้ว
   → เริ่มที่ขั้นตอนที่ยังต้องทำ (เช่น outline หรือ drafting)
```

## Format ของ Research Package

```markdown
# Research Package — Handoff to arts-paper-writer

**วันที่**: [วันที่]
**หัวข้อวิจัย**: [ชื่อ]
**Mode ที่ใช้**: [full / lit-review / socratic+full]

## 1. Research Question Brief
[paste จาก research_question_agent]

## 2. Verified Sources (จาก Source Quality Matrix)
[รายการ sources ที่ผ่านการ verify — tier, DOI, status]

## 3. Literature Synthesis Summary
[paste จาก synthesis_agent — ย่อถ้ายาวมาก]

## 4. INSIGHT Collection (ถ้ามาจาก Socratic mode)
[paste จาก socratic_mentor_agent]

## คำแนะนำสำหรับ arts-paper-writer
- ข้ามขั้นตอน: [ระบุ]
- เริ่มที่: [ระบุ]
- โหมดที่แนะนำ: [full / exegesis / lit-review]
```
