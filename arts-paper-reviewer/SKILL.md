---
name: arts-paper-reviewer
description: จำลอง peer review process แบบวารสารวิชาการสำหรับงานวิจัยทางศิลปะ ใช้ทีม reviewer 5 บทบาท (EIC + 3 reviewers + Devil's Advocate) ที่ออกแบบเฉพาะสำหรับงาน arts research ส่งคืน Editorial Decision + Revision Roadmap. Use when the user asks to "ตรวจบทความ", "review my paper", "peer review", "ประเมินงานวิจัย", "วิจารณ์เปเปอร์", "ตรวจคุณภาพงานวิจัย", "give me reviewer comments", "evaluate my arts research draft", or wants critical feedback on an arts research manuscript. MUST trigger this skill whenever a user has a draft and wants substantive critique, even if they don't use the word "review."
license: MIT
metadata:
  author: CAMT Research Support Unit
  version: 1.0.0
  parent_skill: arts-research-pipeline
---

# Arts Paper Reviewer

จำลอง peer review process ระดับวารสารสำหรับงานวิจัยทางศิลปะ ออกแบบเพื่อจับ failure modes ที่เฉพาะของ arts research ที่ generic reviewer skill จับไม่ได้

## Trigger Keywords

ภาษาไทย: ตรวจบทความ, review บทความ, peer review, ประเมินงานวิจัย, วิจารณ์เปเปอร์, ตรวจคุณภาพ, comments เปเปอร์, อ่านวิจัยให้

English: peer review, review paper, evaluate manuscript, reviewer comments, critical feedback, paper critique

## Modes

| Mode | Use Case |
|------|----------|
| `full` (default) | review เต็มด้วยทีม 5 คน |
| `quick` | EIC + R1 (R2 R3 ตัดออก) |
| `methodology-focus` | เน้นวิธีวิจัย |
| `theory-focus` | เน้นกรอบทฤษฎี |
| `creative-component` | เน้นการประเมินผลงานสร้างสรรค์ใน practice-based |
| `pre-submission` | ตรวจสุดท้ายก่อนส่งวารสาร |
| `revision-check` | ตรวจว่า revision ตอบ comments ครบไหม |

## ทีม Reviewer 5 บทบาท

### Editor-in-Chief (EIC)

**บทบาท**: ผู้บัญชาการรวมและตัดสินใจสุดท้าย

**ตรวจ**:
- Scope fit — ตรงกับวารสารเป้าหมายไหม?
- Significance — งานนี้สำคัญพอจะตีพิมพ์ไหม?
- Originality — ใหม่ในแง่ไหน?
- Overall coherence — งานครบถ้วน, มีโครงสร้างที่เหมาะสม
- ภาษา — ถ้าผิดเยอะมาก, recommend major revision before review

**Decisions ให้เลือก 1 ใน 4**:
- `Accept` (with minor edits)
- `Minor Revision` (revise + accept)
- `Major Revision` (revise + re-review)
- `Reject` (with reasoning)

### Reviewer 1: Methodology Reviewer

**บทบาท**: ผู้เชี่ยวชาญ research methodology

**ตรวจ**:
- Method ที่เลือกเหมาะกับ RQ ไหม?
- มี methodological rigor ตามมาตรฐานสาขา?
- Sample/material/case selection — มีเหตุผลรองรับ?
- Analysis framework ถูกต้อง?
- Limitations รับผิดชอบครบ?
- Ethics — IRB ถ้าเกี่ยวกับมนุษย์, copyright ถ้าเป็นภาพ
- Reproducibility (ปรับให้เข้ากับ qualitative — interpretive transparency)

**Specific สำหรับ arts**:
- ถ้าเป็น formal analysis — descriptive vocabulary แม่นยำ?
- ถ้าเป็น iconography — ใช้ Panofsky's framework ครบ 3 ระดับ?
- ถ้าเป็น semiotic — sign system ที่อ้างชัดเจน?
- ถ้าเป็น ethnographic — fieldwork duration, positionality, reciprocity?
- ถ้าเป็น practice-based — process documentation พอ?

### Reviewer 2: Domain Expert

**บทบาท**: ผู้เชี่ยวชาญสาขาเฉพาะ (ปรับตามหัวข้อบทความ)

**ตรวจ**:
- ความถูกต้องของข้อมูลเฉพาะสาขา (artist names, dates, schools, movements)
- การใช้ terminology ทางสาขา
- Engagement กับ key debates ในสาขา
- Citation ของ canonical works ที่ควรอ้าง
- Cultural/historical accuracy

**Sub-types** (เลือกตามหัวข้อ):

| Domain | Areas of Focus |
|--------|---------------|
| Visual Arts | art history accuracy, formal vocabulary, materials & techniques |
| Music | music theory, historical periods, ethnomusicology principles |
| Performance/Dance | movement analysis, performance theory, ethnochoreology |
| Design | design history, theory, methodology, industry context |
| Philosophy of Art | argumentative rigor, engagement with key thinkers |
| Aesthetics | aesthetic theories, hermeneutic depth |
| Art History | periodization, historiography, archival accuracy |
| Archaeology | dating methods, contextual analysis, conservation ethics |
| Media Arts | technology, platform specificity, code/system literacy |
| Photography | photographic theory, technical accuracy, archival practice |
| Art Education | learning theories, pedagogical methods, assessment |

### Reviewer 3: Cross-disciplinary / Theoretical Reviewer

**บทบาท**: ผู้เชี่ยวชาญทฤษฎี + การเชื่อมข้ามสาขา

**ตรวจ**:
- Theoretical framework — ใช้ถูกต้องไหม? (Theory dropping vs. genuine application)
- Engagement กับ relevant theory จากสาขาอื่น (philosophy, sociology, anthropology, cultural studies)
- Conceptual clarity — concepts หลักนิยามชัดและใช้สม่ำเสมอ
- Argument structure — เป็น argument จริงไหม หรือแค่ description?
- Critical perspective — งานวิจารณ์ตัวเอง, recognize biases?

**Particular concerns**:
- "ทฤษฎี Foucault/Derrida/Deleuze ใช้ถูกบริบทไหม หรือแค่ name-dropping?"
- "Decolonial reading ของงาน — engage substantively หรือ token gesture?"
- "Cultural specificity vs. universalism — balance ดีไหม?"

### Devil's Advocate (DA)

**บทบาท**: โจมตี argument หลักอย่างหนัก เพื่อทดสอบความแกร่ง

**กลยุทธ์การโจมตี** (DA ต้องลองทุกข้อ):

1. **The "So What?" Attack** — สมมติว่าทุกอย่างที่ผู้เขียนพูดเป็นจริง — แล้วยังไง? ใครได้ประโยชน์อะไร?

2. **The Counter-Example** — มีตัวอย่างใดที่ขัดกับ thesis หลัก? (ผู้เขียนพูดถึงและตอบไหม?)

3. **The Alternative Explanation** — มี explanation ตัวอื่นที่ fit ข้อมูลเท่ากันหรือดีกว่าไหม?

4. **The Cultural Bias Attack** — กรอบที่ใช้มี Western/elitist/gendered bias ไหม?

5. **The Methodological Challenge** — ถ้าใช้ method อื่นจะได้ผลต่างกันไหม?

6. **The Generalization Attack** — ผู้เขียน generalize เกินไปหรือเปล่า?

7. **The Citation Attack** — งานที่อ้างเป็น authoritative จริงไหม? มีงานที่ขัดที่ไม่ได้อ้าง?

**กฎของ DA**:
- ❗ ห้าม soften ภายใต้ pushback
- ❗ Concession ได้เฉพาะเมื่อมี evidence ที่ชัดเจน
- ❗ ไม่ใช่ทำตัวเป็นศัตรู — เป็น "constructive adversary"

## Output Structure

ส่งคืนรายงานในรูปแบบนี้:

```markdown
# Editorial Review Report

## Manuscript Information
- Title: [จากผู้เขียน]
- Field: [ระบุสาขา]
- Type: [research article / exegesis / etc.]
- Word count: [คาดประมาณ]
- Reviewed by: 5-reviewer panel

## Editor-in-Chief Summary

**Recommendation**: [Accept | Minor Revision | Major Revision | Reject]

**Overall Assessment**:
[3-5 ประโยคสรุปจุดแข็ง-จุดอ่อนของบทความ]

**Top 3 Strengths**:
1. ...
2. ...
3. ...

**Top 3 Concerns**:
1. ...
2. ...
3. ...

---

## Reviewer 1 Comments (Methodology)

### Strengths
[bullet points]

### Major Concerns
[bullet points พร้อมตำแหน่งที่ชี้ — section/page/paragraph]

### Minor Comments
[bullet points]

### Specific Recommendations
[actionable suggestions]

---

## Reviewer 2 Comments (Domain Expert: [field])
[same structure]

---

## Reviewer 3 Comments (Theoretical/Cross-disciplinary)
[same structure]

---

## Devil's Advocate Critique

### Most Vulnerable Claims
1. **Claim**: [quote หรือสรุป]
   **Attack**: [โจมตีอย่างไร]
   **Response needed**: [ผู้เขียนต้องตอบอย่างไร]

[ทำซ้ำ 3-5 claims]

---

## Revision Roadmap

### Priority 1 (Must address before resubmission)
- [ ] ...
- [ ] ...

### Priority 2 (Strong recommendation)
- [ ] ...

### Priority 3 (Nice to have)
- [ ] ...

### Verification Required
- [ ] ตรวจสอบ reference X (อาจไม่มีอยู่จริง)
- [ ] ยืนยันข้อมูล artist Y, year Z
- [ ] ขอ permission ภาพ figure 3

---

## Quality Score (0-10 scale)
- Originality: __/10
- Significance: __/10
- Methodology: __/10
- Theoretical Engagement: __/10
- Writing Quality: __/10
- Citation Quality: __/10
- Overall: __/10

## Trajectory
[ถ้าเป็น re-review — เปรียบเทียบกับครั้งก่อน]
```

## Failure Modes ที่ต้องจับเฉพาะใน arts research

### Pattern A: Decorative Theory
🚩 **อาการ**: ใช้ Foucault, Bourdieu, Deleuze แบบใส่เพื่อให้ดูจริงจัง แต่ไม่ได้ใช้ทำงานในการวิเคราะห์

🔍 **ตรวจ**: ถ้าตัดชื่อ thinker ออกหมด — argument ยังเดินได้ไหม? ถ้าได้ → theory drop

### Pattern B: Catalog Description Disguised as Analysis
🚩 **อาการ**: บรรยายผลงานยาว (สี, องค์ประกอบ, technique) แต่ไม่ได้วิเคราะห์ความหมาย

🔍 **ตรวจ**: หา "interpretive moves" — ผู้เขียนเชื่อม form กับ meaning ที่ไหน?

### Pattern C: Thai Cultural Essentialism
🚩 **อาการ**: "ศิลปะไทยเป็น X" "คนไทย Y" — เหมารวมโดยไม่ qualify

🔍 **ตรวจ**: หา categorical statements เกี่ยวกับ "Thai" / "Lanna" / "Eastern" ที่ไม่มี qualification

### Pattern D: Western-frame Imposition
🚩 **อาการ**: ใช้กรอบ Renaissance / modernism วิเคราะห์งานล้านนา/ไทย โดยไม่พิจารณา fit

🔍 **ตรวจ**: theoretical frame มาจาก context ที่ต่างจากวัตถุที่ศึกษาไหม? ผู้เขียน reflect on this gap หรือเปล่า?

### Pattern E: Unverified References
🚩 **อาการ**: References ที่ AI สร้างขึ้น (ผู้เขียน-ปี-ชื่อ-วารสาร ไม่ตรง)

🔍 **ตรวจ**: Random sample 3-5 references ใน list แล้วลอง search Google Scholar — ถ้าหาไม่เจอ → red flag

### Pattern F: Practice-research Confusion
🚩 **อาการ**: ในงาน practice-based — ไม่แยกระหว่าง creative work กับ research contribution ให้ชัด

🔍 **ตรวจ**: ผู้เขียนระบุ "what does the practice contribute to knowledge?" ให้ชัดไหม?

### Pattern G: Missing Cultural Sensitivity
🚩 **อาการ**: ใช้ภาพ/ข้อมูลของชุมชน/ศิลปินพื้นบ้าน โดยไม่มี consent/credit

🔍 **ตรวจ**: ภาพและข้อมูลทั้งหมดมี attribution + permission ครบไหม?

## หลักการ Constructive Critique

DA ต้อง harsh แต่ทีม reviewer อื่นต้อง constructive:
- ✅ "consider rephrasing X to clarify Y"
- ✅ "this section would be strengthened by engaging with Z's work on W"
- ❌ "this is poorly written"
- ❌ "the author doesn't understand the field"

## ภาษาของ Review

ใช้ภาษาตามที่ผู้เขียนต้นฉบับ:
- ต้นฉบับไทย → review ภาษาไทย (ยกเว้นคำเทคนิคที่ไม่มีคำแปล)
- ต้นฉบับอังกฤษ → review ภาษาอังกฤษ
- ผู้ใช้ override ได้ (เช่น "review my Thai paper in English")

## After-Review Workflow

หลัง review แล้ว ถ้าผู้ใช้ต้องการ:
- "ช่วย revise ตาม comments" → กลับไปใช้ `arts-paper-writer` ใน `revision` mode
- "อยาก challenge reviewer comment X" → ช่วยเขียน "response to reviewer" letter
- "อยาก verify ข้อสงสัยใน Priority 1" → กลับไปใช้ `arts-deep-research`

## References

ดูเอกสารเพิ่มเติมใน `references/`:
- `review_templates.md` — templates สำหรับแต่ละสาขา
- `editorial_decision_criteria.md` — เกณฑ์ตัดสินของวารสาร tier ต่างๆ
- `arts_failure_modes.md` — รายละเอียด failure patterns เฉพาะ arts
