---
name: failure_paths
purpose: Failure scenarios, trigger conditions, และ recovery strategies สำหรับ arts-deep-research
---

# Failure Paths — Arts Deep Research

## ตารางสรุป Failure Scenarios

| Scenario | Trigger | Recovery Strategy |
|----------|---------|-----------------|
| RQ ไม่ converge | Socratic > 10 rounds ยังไม่ได้ RQ | เสนอ 3 candidate RQs หรือแนะนำ lit-review ก่อน |
| Literature หาไม่พอ | bibliography < 10 sources verified | ขยาย search strategy, เพิ่ม keywords, ลองฐานข้อมูลอื่น |
| References หลายรายการเป็น AI-generated | > 30% ของ suggested refs verify ไม่ผ่าน | แจ้งผู้ใช้ทันที, ทำ manual search ใหม่ |
| Primary sources เข้าไม่ได้ | archive/collection ปิด/ต้องขออนุญาต | แนะนำ alternative collections, ติดต่อ institution |
| สาขาเฉพาะ — literature น้อยมาก | งาน peer-reviewed < 5 ชิ้น | ขยายไปสาขาใกล้เคียง, รวม grey literature ที่ authoritative |
| ขัดแย้งระหว่าง sources สำคัญ | 2 seminal works ให้ข้อมูลขัดกัน | รายงานทั้งสองฝั่ง, อธิบาย context ของแต่ละฝั่ง |
| งานไทยน้อยมาก | TCI/ThaiLIS ไม่มีงานที่เกี่ยวข้อง | ระบุ gap นี้ใน literature review, แนะนำ primary sources ไทย |
| ผู้ใช้หยุดกลางทาง | ไม่ response > 2 rounds | บันทึก progress ปัจจุบัน, แนะนำจุด re-entry |

## รายละเอียด Recovery

### RQ ไม่ converge หลัง 10 rounds
```
1. สรุปสิ่งที่ได้จาก dialogue จนถึงตอนนี้
2. เสนอ 3 candidate RQs จาก insights ที่สะสมมา
3. ให้ผู้ใช้เลือก 1 หรือ combine
4. ถ้ายังไม่ชัด → แนะนำ lit-review mode ก่อน (เพื่อ explore field)
```

### References AI-generated เยอะเกินไป
```
⚠️ แจ้งผู้ใช้ทันทีว่าพบปัญหา
ห้ามใช้ unverified references ต่อไป
เสนอ 2 ทางเลือก:
1. ทำ manual search ใหม่ด้วย databases ที่เชื่อถือได้
2. ผู้ใช้ provide references ของตัวเองสำหรับ verification
```

### Primary Sources เข้าไม่ได้
```
1. ระบุ alternative collections ที่อาจมีงานเดียวกัน
2. แนะนำ inter-library loan / digital archive request
3. สำหรับงานไทย: แนะนำ CMUL, หอสมุดแห่งชาติ, หอจดหมายเหตุแห่งชาติ
4. ถ้าเป็น collection เฉพาะ: แนะนำติดต่อ curator โดยตรง
```
