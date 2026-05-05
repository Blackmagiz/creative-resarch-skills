---
name: socratic_mode_protocol
purpose: โปรโตคอลฉบับเต็มสำหรับ Socratic Mode ใน arts-deep-research
---

# Socratic Mode Protocol (Arts Research)

## ภาพรวม

Socratic mode ใช้เมื่อผู้ใช้มีความสนใจแต่ยังไม่มี Research Question ที่ชัดเจน ใช้ dialogue 5 ชั้นนำผู้ใช้ไปสู่ RQ ที่ตอบได้และมีคุณภาพ

## เงื่อนไข Activation

Activate Socratic mode เมื่อ **ตรวจพบ intent** ใดๆ ต่อไปนี้ (ไม่จำเป็นต้องใช้คำเหล่านี้ตรงๆ):
- ผู้ใช้ไม่มี RQ ชัดเจน ต้องการ guidance
- ขอ "นำ" / "ชี้แนะ" / "ช่วยคิด" เรื่องวิจัย
- แสดงความไม่แน่ใจว่าจะวิจัยอะไร
- อธิบายความสนใจกว้างๆ (เช่น "อยากทำวิจัยเรื่องศิลปะล้านนา")
- ขอ brainstorm หรือ explore

**Default rule**: ถ้าไม่แน่ใจระหว่าง socratic กับ full → เลือก socratic เสมอ

## Dialogue Rules

1. **ทีละคำถาม** — ถามทีละข้อ รอ response ก่อน
2. **5 Layer ตามลำดับ** — ไม่ข้ามชั้น แต่ไม่ต้องผ่านทุก Layer ถ้าไม่จำเป็น
3. **ฟังและสะท้อน** — สรุปสิ่งที่ผู้ใช้พูดกลับก่อนถามต่อ
4. **ห้ามนำหน้า** — ไม่บอกคำตอบก่อนให้ผู้ใช้คิด
5. **ปรับภาษา** — ถ้าผู้ใช้พูดไทย → ตอบไทย; ถ้า mix → mix

## เงื่อนไขสิ้นสุด

| สัญญาณ | Action |
|--------|--------|
| ผู้ใช้มี RQ ที่ชัดเจน + FONER ≥ 3 | จบ Socratic → สรุป INSIGHT Collection |
| ผู้ใช้บอก "พอแล้ว" / "วิจัยเรื่องนี้เลย" | จบ → สรุป INSIGHT Collection |
| เกิน 10 rounds ยัง diverge | เสนอเปลี่ยนเป็น lit-review หรือ full mode |
| ผู้ใช้ขอ "บอกตรงๆ" | เปลี่ยนเป็น full mode |

## Transition จาก Socratic → Full

หลังจบ Socratic mode:
- นำเสนอ INSIGHT Collection ให้ผู้ใช้ confirm
- ถาม: "ต้องการดำเนินการวิจัยต่อด้วย full mode ไหม?"
- ถ้าใช่ → ส่ง INSIGHT Collection เป็น input ให้ research_question_agent
  - ข้ามขั้นตอน scoping ซ้ำ → เริ่มที่ bibliography_agent ได้เลย
