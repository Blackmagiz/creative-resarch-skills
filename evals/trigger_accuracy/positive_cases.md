---
title: "Trigger Accuracy — Positive Cases"
description: "Prompts ที่ควร trigger skill ที่ระบุ — ทดสอบ recall (ไม่พลาด trigger ที่ควรทำ)"
version: 1.0.0
---

# Trigger Accuracy — Positive Cases

> **วิธีอ่าน**: แต่ละ test case มี ID, Input Prompt, Expected Skill, และ Assertion Criteria
> PASS = skill ที่ระบุถูกเลือก | FAIL = skill อื่นถูกเลือกหรือไม่มี skill ถูก trigger

---

## 🔬 arts-deep-research

### TR-DR-001
**Input:** `ช่วยหาเอกสารอ้างอิงเกี่ยวกับศิลปะร่วมสมัยของเชียงใหม่หน่อยได้ไหม`
**Expected Skill:** arts-deep-research
**Assertions:**
- [ ] arts-deep-research SKILL.md ถูกอ่าน
- [ ] มีการค้นหาจากฐานข้อมูลอย่างน้อย 3 แหล่ง (TCI, ThaiLIS, + international)
- [ ] ผลลัพธ์มี Source Quality Tier ระบุ (Tier 1/2/3)

### TR-DR-002
**Input:** `ทบทวนวรรณกรรมเรื่อง practice-based research ในดนตรีไทยร่วมสมัย`
**Expected Skill:** arts-deep-research
**Assertions:**
- [ ] Literature Matrix ถูกสร้าง
- [ ] มี research gap ระบุ
- [ ] แหล่งข้อมูลไทยถูกรวม (TCI, SAC, CMU Repository)

### TR-DR-003
**Input:** `I need primary sources for my research on Lanna textile art — find performance documentation and archival materials`
**Expected Skill:** arts-deep-research
**Assertions:**
- [ ] Primary sources (ผลงานจริง/จดหมายเหตุ) ถูกระบุแยกจาก secondary sources
- [ ] แหล่งข้อมูล archival/oral interview รวมอยู่
- [ ] PRISMA-adapted screening ปรากฏ

### TR-DR-004
**Input:** `หาเปเปอร์เกี่ยวกับ visual storytelling ในงานออกแบบกราฟิก`
**Expected Skill:** arts-deep-research
**Assertions:**
- [ ] arts-deep-research triggered (ไม่ใช่ visual-analysis)
- [ ] Bibliography Agent ทำงาน

### TR-DR-005 — Socratic Mode trigger
**Input:** `อยากทำวิจัยเกี่ยวกับศิลปะ แต่ยังไม่รู้จะวิจัยอะไร`
**Expected Skill:** arts-deep-research (Socratic Mode)
**Assertions:**
- [ ] Socratic Mentor Agent ถูกเรียกใช้
- [ ] 5-layer Socratic dialogue เริ่มต้น (Clarification layer ก่อน)
- [ ] ไม่เริ่ม Literature Search ก่อน RQ ชัดเจน ⚠️ IRON RULE

---

## ✍️ arts-paper-writer

### TR-PW-001
**Input:** `เขียนบทความวิจัยเรื่องการใช้ AI ในงานศิลปะดิจิทัล`
**Expected Skill:** arts-paper-writer
**Assertions:**
- [ ] Intake Planner Agent ถูกเรียก (6 questions)
- [ ] Paper structure ถูกเลือก (IMRaD/Exegesis/Exhibition Essay)
- [ ] ไม่เริ่มเขียนก่อนได้รับ confirmation ⚠️ IRON RULE

### TR-PW-002
**Input:** `ช่วยร่าง abstract ภาษาไทยและอังกฤษสำหรับงานวิจัยของฉัน`
**Expected Skill:** arts-paper-writer (Bilingual Abstract mode)
**Assertions:**
- [ ] Bilingual Abstract Agent ถูกเรียก
- [ ] Thai abstract 200-300 คำ
- [ ] English abstract 200-300 คำ (rewrite ไม่ใช่ translation)
- [ ] 10-element alignment check ปรากฏ

### TR-PW-003
**Input:** `write an exegesis for my practice-based research on contemporary Thai dance`
**Expected Skill:** arts-paper-writer (Exegesis mode)
**Assertions:**
- [ ] Exegesis Agent ถูกเรียก
- [ ] 9-section exegesis structure ถูกเสนอ
- [ ] Knowledge contribution type ถูกระบุ (IN/FROM/ABOUT)

### TR-PW-004
**Input:** `ฉันได้รับ reviewer comments มา ช่วยแก้ไขบทความหน่อย`
**Expected Skill:** arts-paper-writer (Revision Coach mode)
**Assertions:**
- [ ] Revision Coach Agent ถูกเรียก
- [ ] Comment Triage (P1/P2/P3) ปรากฏ
- [ ] Anti-leakage check ถูกเตือน

### TR-PW-005
**Input:** `ตรวจสอบคุณภาพงานเขียนของฉันก่อนส่ง`
**Expected Skill:** arts-paper-writer (Writing Quality Check mode)
**Assertions:**
- [ ] Writing Quality Agent ถูกเรียก (READ-ONLY) ⚠️ IRON RULE
- [ ] WQC 7 dimensions ถูกประเมิน
- [ ] Score และ PASS/CAUTION/FAIL ปรากฏ

---

## 🔍 arts-paper-reviewer

### TR-PR-001
**Input:** `ช่วยตรวจบทความวิจัยของฉันแบบ peer review หน่อย`
**Expected Skill:** arts-paper-reviewer
**Assertions:**
- [ ] EIC Agent เริ่มต้นกระบวนการ
- [ ] 5-agent review team ทำงาน (EIC + 3 reviewers + DA)
- [ ] Editorial Decision ปรากฏ

### TR-PR-002
**Input:** `give me reviewer comments for my arts research draft — focus on methodology`
**Expected Skill:** arts-paper-reviewer
**Assertions:**
- [ ] Methodology Reviewer Agent ทำงานหลัก
- [ ] Devil's Advocate Agent ทำงาน
- [ ] DA CRITICAL block = Accept ⚠️ IRON RULE

### TR-PR-003 — Re-review Mode trigger
**Input:** `ฉันแก้ไขบทความตาม reviewer แล้ว ขอให้ตรวจรอบสองหน่อย`
**Expected Skill:** arts-paper-reviewer (Re-review Mode)
**Assertions:**
- [ ] Re-review Protocol ถูกเรียก
- [ ] R&R Traceability Matrix ถูกสร้าง
- [ ] P1 items ถูกตรวจว่าแก้ครบใน manuscript (ไม่ใช่แค่ Response Letter) ⚠️ IRON RULE

---

## 🗂️ arts-citation-formatter

### TR-CF-001
**Input:** `ช่วยจัดรูปแบบบรรณานุกรมให้เป็น APA 7`
**Expected Skill:** arts-citation-formatter
**Assertions:**
- [ ] Citation Formatter Agent ทำงาน
- [ ] Source Type ID ปรากฏ
- [ ] Verification status (DOI verified/TCI verified) ระบุ

### TR-CF-002
**Input:** `อ้างอิง exhibition catalog ของ Documenta 15 ยังไง`
**Expected Skill:** arts-citation-formatter
**Assertions:**
- [ ] Exhibition Catalog template ถูกเลือก
- [ ] VERIFY BEFORE FORMAT ⚠️ IRON RULE ถูกปฏิบัติ

### TR-CF-003
**Input:** `cite an oral interview with an artist for my thesis`
**Expected Skill:** arts-citation-formatter
**Assertions:**
- [ ] Oral Interview template ปรากฏ
- [ ] ข้อมูล: ชื่อผู้ให้สัมภาษณ์, ผู้สัมภาษณ์, วันที่, รูปแบบถูกระบุ

---

## 🎨 practice-based-research

### TR-PBR-001
**Input:** `ฉันทำวิจัยโดยสร้างผลงานศิลปะเป็นส่วนหนึ่งของวิจัย จะเขียน exegesis ยังไง`
**Expected Skill:** practice-based-research
**Assertions:**
- [ ] Practice Guide Agent ทำงาน
- [ ] Research Type Classification (Q1/Q2) ปรากฏ
- [ ] KNOWLEDGE CONTRIBUTION REQUIRED ⚠️ IRON RULE ถูกตรวจสอบ

### TR-PBR-002
**Input:** `บันทึกกระบวนการสร้างสรรค์ของฉันใน process journal`
**Expected Skill:** practice-based-research
**Assertions:**
- [ ] Process Journal Template ถูกใช้
- [ ] Daily entry format ปรากฏ

---

## 🖼️ visual-analysis

### TR-VA-001
**Input:** `วิเคราะห์ภาพจิตรกรรมฝาผนังวัดภาพุมินทร์`
**Expected Skill:** visual-analysis
**Assertions:**
- [ ] Visual Analysis Agent ทำงาน
- [ ] 3-level analysis: Description → Analysis → Interpretation ⚠️ IRON RULE
- [ ] Thai Buddhist iconographic framework ถูกเลือก

### TR-VA-002
**Input:** `formal analysis of this contemporary Thai painting`
**Expected Skill:** visual-analysis
**Assertions:**
- [ ] Formal analysis framework ถูกเลือก
- [ ] 7 formal elements ครบ (line, shape, form, color, texture, space, value)

### TR-VA-003
**Input:** `ตีความภาพถ่ายชุดนี้ในเชิง semiotic`
**Expected Skill:** visual-analysis
**Assertions:**
- [ ] Semiotic framework ถูกเลือก (Saussure/Peirce/Barthes)
- [ ] ไม่ข้ามระดับวิเคราะห์ — Description มาก่อน ⚠️ IRON RULE

---

## 🔄 arts-research-pipeline

### TR-ARP-001
**Input:** `อยากเริ่มทำวิจัยเชิงสร้างสรรค์ตั้งแต่ต้น ช่วย manage pipeline ให้หน่อย`
**Expected Skill:** arts-research-pipeline
**Assertions:**
- [ ] Intake Assessment Agent ทำงาน
- [ ] Complexity Score ถูกคำนวณ (7 factors)
- [ ] Research Passport ถูกสร้าง
- [ ] ไม่เริ่ม Stage 1 ก่อน confirm ⚠️ IRON RULE

### TR-ARP-002
**Input:** `วิจัยของฉันค้างอยู่ตรงไหน ช่วย resume pipeline หน่อย`
**Expected Skill:** arts-research-pipeline (Resume Mode)
**Assertions:**
- [ ] Resume Protocol ถูกเรียก
- [ ] Research Passport ถูกดึงมา
- [ ] Material Freshness Check ปรากฏ
