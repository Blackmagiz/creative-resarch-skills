---
name: failure_paths
purpose: 8 failure scenarios ใน visual-analysis + recovery strategies
parent_skill: visual-analysis
version: 1.0.0
---

# Failure Paths — Visual Analysis

| # | ชื่อ | Trigger | ผลกระทบ | Recovery |
|---|-----|---------|---------|---------|
| F1 | No Image / Unverifiable Image | วิเคราะห์ภาพที่ไม่มีหรือ resolution ต่ำเกินไป | description ผิดพลาด | หยุด → ขอภาพที่ชัดกว่า หรือ note ข้อจำกัดใน analysis |
| F2 | Method-Object Mismatch | ใช้ Panofsky กับ abstract art ที่ไม่มี iconography | analysis ไม่ match content | เลือก method ที่เหมาะกับประเภทงาน (formal / semiotic) |
| F3 | Description-Only | บรรยาย visual elements ตลอดโดยไม่ตีความ | ไม่ใช่ analysis — เป็นแค่ description | เพิ่ม interpretive moves ทุก 2-3 ย่อหน้า |
| F4 | Context Overload | ใส่ context ประวัติศาสตร์มากจนบดบัง formal analysis | ไม่ได้ analyze ตัวงาน | balance: formal first → context บริบทหนุน |
| F5 | Subjective Overclaim | "งานนี้ทำให้รู้สึก X" โดยไม่มี visual evidence | Impressionistic ไม่ใช่ Academic | link ทุก interpretation กลับไปยัง specific visual elements |
| F6 | Western Framework Imposition | ใช้ iconography แบบ Western กับงานไทย/พุทธโดยไม่ adapt | misreading เชิงวัฒนธรรม | เพิ่ม Thai/Buddhist iconographic sources + note framework limitations |
| F7 | Missing Primary Source Access | วิเคราะห์จาก reproduction โดยไม่ระบุ | ข้อมูล scale/texture/color ไม่น่าเชื่อถือ | note ใน methodology: "analyzed from digital reproduction" + ข้อจำกัด |
| F8 | Comparative Analysis Imbalance | compare งาน 2 ชิ้นแต่ focus ชิ้นเดียว | comparison ไม่ fair | ตรวจ: แต่ละงานได้รับ analytical depth เท่ากันไหม |

---

## Detailed Recovery: F2 — Method-Object Mismatch

**Guide: Which method for which art type?**

| ประเภทงาน | Method ที่เหมาะ | Method ที่ไม่เหมาะ |
|---------|--------------|----------------|
| Abstract art | Formal, Semiotic | Iconographic (ไม่มี subject matter) |
| Religious Thai art | Iconographic (Thai-Buddhist), Contextual | Western iconography อย่างเดียว |
| Contemporary installation | Semiotic, Contextual, Formal | Historical iconography |
| Photography | Formal, Semiotic, Contextual | Iconographic (ยกเว้น staged photography) |
| Performance documentation | Contextual, Semiotic | Formal (ไม่ใช่ static image) |
| Traditional Thai painting | Iconographic (Thai), Formal, Historical | Western modernist frameworks |
| Design / poster | Semiotic, Formal, Contextual | Connoisseurship-based |

---

## Detailed Recovery: F6 — Western Framework Imposition

**สำหรับงานศิลปะไทย/ล้านนา/พุทธ**:

ต้องเพิ่มใน methodology:
```
1. ระบุว่าใช้ framework ใด (Panofsky, Barthes, etc.)
2. Note ข้อจำกัด: "framework นี้พัฒนาจาก Western tradition"
3. เสริมด้วย Thai/Buddhist iconographic tradition:
   - พระไตรปิฎก / Buddhist canonical texts
   - Nang Klao tradition
   - ตำราพิชัยสงคราม / พื้นเมืองเชียงใหม่
   - SAC databases สำหรับงานชาติพันธุ์วิทยา
4. Critical self-reflection: "การนำ framework นี้มาใช้กับงานไทยมีข้อจำกัดใน..."
```

**แหล่งข้อมูลไทย-พุทธสำหรับ iconography**:
- Ginsburg, H. — Thai Art and Culture
- Woodward, H. — Sacred Sculptures of Thailand  
- SAC (ศูนย์มานุษยวิทยาสิรินธร) — ฐานข้อมูลศิลปะพื้นบ้าน
- กรมศิลปากร — คลังข้อมูลมรดกทางวัฒนธรรม
