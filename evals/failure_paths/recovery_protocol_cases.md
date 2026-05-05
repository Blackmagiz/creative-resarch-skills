---
title: "Failure Paths — Recovery Protocol Test Cases"
description: "ตรวจสอบว่า recovery workflow ถูกต้องและ specific เพียงพอ"
version: 1.0.0
---

# Failure Paths — Recovery Protocol Test Cases

> เน้นตรวจว่า recovery ให้ขั้นตอนที่ actionable ไม่ใช่แค่ "ควรแก้ไข"

---

### RP-001 — F1: RQ Undefined Recovery
**Scenario:** ผู้ใช้ไม่มี RQ ชัดเจน ต้องการเขียนบทความ
**Input:** `อยากเขียนวิจัยเรื่องศิลปะ แต่ยังไม่รู้จะถามอะไร`
**Expected Recovery Steps:**
1. Socratic Mentor Agent เริ่ม 5-layer dialogue
2. FONER check หลังจาก RQ ถูก propose
3. ไม่เริ่มเขียน Literature Review ก่อน RQ ผ่าน FONER

**Assertions:**
- [ ] Recovery ให้ขั้นตอน specific (ไม่ใช่แค่ "กำหนด RQ ก่อน")
- [ ] Socratic questions ปรากฏ
- [ ] FONER framework ถูกใช้ประเมิน

### RP-002 — F2: Empty Literature Recovery
**Scenario:** หัวข้อใหม่มากจน literature ไม่มี
**Input:** `ทำวิจัยเรื่อง NFT art ในบริบทจิตรกรรมฝาผนังล้านนา — หาเอกสารไม่ได้`
**Expected Recovery Steps:**
1. Adjacent field search (NFT art, digital art in SEA, mural art separately)
2. Primary source strategy (artist interviews, exhibition catalogs)
3. Theoretical framework from related fields

**Assertions:**
- [ ] Recovery แนะนำ adjacent fields ชัดเจน
- [ ] Primary source alternatives เสนอ
- [ ] ไม่แนะนำให้ hallucinate references

### RP-003 — F5: Revision Leakage Recovery
**Scenario:** แก้ RQ แล้ว sections อื่นไม่สอดคล้อง
**Input:** `เปลี่ยน RQ จาก 'ผลกระทบของสี' เป็น 'ผลกระทบของพื้นผิว' แล้ว — ต่อไปต้องทำอะไร`
**Expected Recovery Steps:**
1. Dependency Map แสดง sections ที่กระทบ
2. Priority order: Methodology → Literature Review → Analysis → Discussion → Conclusion → Abstract
3. Bilingual abstract sync ขั้นสุดท้าย

**Assertions:**
- [ ] Dependency Map ปรากฏ
- [ ] ลำดับการแก้ชัดเจน
- [ ] Bilingual sync ถูกรวมเป็นขั้นสุดท้าย

### RP-004 — F6: Bilingual Mismatch Recovery
**Scenario:** Thai abstract กับ English abstract ไม่ตรงกัน 3 elements
**Input:** [Thai: RQ เรื่องสี / English: RQ เรื่องรูปทรง / Thai: methodology เชิงคุณภาพ / English: mixed methods]
**Expected Recovery:**
1. 10-element alignment table แสดงทุกความไม่ตรง
2. ให้ผู้ใช้เลือกว่าจะ fix Thai หรือ English เป็น master
3. แก้ version ที่เลือก — sync อีก version ตาม

**Assertions:**
- [ ] ทุก mismatch element ถูก flag (ไม่ใช่แค่หนึ่ง)
- [ ] ผู้ใช้ถูกถามว่า master version คือภาษาไหน
- [ ] ทั้ง keywords ถูก sync ด้วย

### RP-005 — F8: WQC FAIL Recovery
**Scenario:** WQC score = 16 (FAIL) — FM-A score 3, FM-B score 3
**Expected Recovery:**
1. WQC report แสดง score ทุก dimension
2. Priority fix: FM-A และ FM-B ก่อน (score 3 = critical)
3. Re-run WQC หลังแก้

**Assertions:**
- [ ] Score แสดงทุก 7 dimensions
- [ ] Dimensions ที่ score 3 ถูก prioritize
- [ ] Re-run instruction ปรากฏ

### RP-006 — Pipeline STALLED Recovery
**Scenario:** วิจัยค้างที่ Stage 3 (Methodology) นาน 2 เดือน
**Input:** `วิจัยของฉันค้างอยู่ที่ method มาสองเดือนแล้ว`
**Expected Recovery:**
1. Pipeline Orchestrator ตรวจ State = STALLED
2. Resume Protocol 5 steps
3. Material Freshness Check (literature อายุ > 6 เดือน ต้อง update)
4. Blocker Identification

**Assertions:**
- [ ] STALLED state ถูก recognize
- [ ] Research Passport ถูก retrieve หรือ reconstruct
- [ ] Material Freshness Check ปรากฏ
- [ ] Blocker ถูก identify (ไม่ใช่แค่ "กลับไปทำต่อ")

---

## Results Log

| Case ID | Failure Type | Recovery Actionable? | Steps Complete? | Result | Notes |
|---------|-------------|---------------------|-----------------|--------|-------|
| RP-001 | F1 RQ Undefined | | | | |
| RP-002 | F2 Empty Lit | | | | |
| RP-003 | F5 Rev Leakage | | | | |
| RP-004 | F6 Bilingual | | | | |
| RP-005 | F8 WQC FAIL | | | | |
| RP-006 | Pipeline STALLED | | | | |
