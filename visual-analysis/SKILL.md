---
name: visual-analysis
description: วิเคราะห์งานทัศนศิลป์, ออกแบบ, ภาพถ่าย, และสื่อภาพ พร้อม 4 Iron Rules (THREE LEVELS REQUIRED: Description→Analysis→Interpretation, EVIDENCE-BASED INTERPRETATION, CULTURAL FRAMEWORK, IMAGE VERIFICATION), 5 analysis frameworks (formal analysis 7 elements, iconography/iconology Panofsky 3 levels, semiotic Saussure+Peirce+Barthes, thai-buddhist iconometric systems, contextual/social), Thai Buddhist additions (sìp-sǒng nák-sat iconography, mudrā system, Thai classical elements), Pre-analysis Checklist, Analysis Worksheet Template, และ Failure Mode detection FM-B (Catalog Description) + FM-C (Cultural Essentialism) + FM-D (Western Frame Imposition) + FM-G (Cultural Sensitivity). Use when the user asks to "วิเคราะห์ภาพ", "วิเคราะห์งานศิลปะ", "analyze artwork", "formal analysis", "iconography", "semiotic analysis", "วิเคราะห์ทัศนธาตุ", "ตีความผลงาน", or needs visual analysis of paintings, photographs, designs, or any visual material. MUST trigger whenever the user wants to analyze any visual material in any framework.
license: MIT
metadata:
  author: CAMT Research Support Unit
  version: 2.0.0
  parent_skill: arts-research-pipeline
---

# Visual Analysis

คู่มือวิเคราะห์งานทัศนศิลป์ ออกแบบ ภาพถ่าย และสื่อภาพ ครอบคลุมทั้งกรอบคลาสสิกและร่วมสมัย

## Trigger Keywords

ภาษาไทย: วิเคราะห์ภาพ, วิเคราะห์ผลงาน, วิเคราะห์ทัศนธาตุ, อ่านภาพ, ตีความผลงาน, วิจารณ์ศิลปะ, formal analysis, iconography, iconology

English: visual analysis, image analysis, formal analysis, iconographic analysis, iconology, art criticism, semiotic analysis, reading images

## Modes

| Mode | Use Case |
|------|----------|
| `formal` | Formal analysis เน้น visual elements |
| `iconographic` | Panofsky's three levels |
| `semiotic` | sign system analysis |
| `contextual` | social/historical context |
| `comparative` | comparative analysis ระหว่าง 2+ ผลงาน |
| `comprehensive` (default) | combined multi-method |

## ก่อนเริ่ม: ตรวจสอบสิ่งที่ user มี

- ภาพดู digital หรือเห็นจริง (มีผลต่อ description ที่เชื่อถือได้)?
- ข้อมูลพื้นฐาน: artist, title, year, medium, dimensions, location
- ภาพ resolution พอวิเคราะห์ details?
- มีข้อมูลบริบท (commission, audience, exhibition history)?

## Method 1: Formal Analysis

วิเคราะห์ visual elements โดยปราศจาก context (เป็นจุดเริ่ม ไม่ใช่จุดจบ)

### Visual Elements (ทัศนธาตุ)

ใช้ checklist นี้ แต่ไม่ต้องใช้ทุกข้อทุกครั้ง — เลือกที่สำคัญสำหรับงานนั้น:

**1. Line (เส้น)**
- ลักษณะ: ตรง/โค้ง/หัก/ต่อเนื่อง/ขาดตอน
- น้ำหนัก: หนา/บาง/แตกต่าง
- ทิศทาง: แนวนอน (สงบ), แนวตั้ง (มั่นคง/ทะยาน), เฉียง (เคลื่อนไหว)
- function: outline, contour, gestural, structural

**2. Shape & Form (รูปร่าง/รูปทรง)**
- Geometric vs organic
- 2D shape vs 3D form (perceived)
- Positive vs negative space
- Mass vs void

**3. Color (สี)**
- Hue (แม่สี)
- Value (น้ำหนักสี — สว่าง-มืด)
- Saturation (ความอิ่มสี)
- Color harmony: complementary, analogous, triadic
- Warm/cool palette
- Symbolic associations (ระวัง — culture-specific)

**4. Texture (พื้นผิว)**
- Actual texture (จับได้จริง — สำคัญใน sculpture, mixed media)
- Implied texture (illusion ผ่านการวาด)

**5. Space (ที่ว่าง)**
- Pictorial space: linear perspective, atmospheric perspective, isometric, flat
- Foreground/middleground/background
- Positive/negative space
- Depth cues

**6. Composition (การจัดวาง)**
- Symmetry/asymmetry
- Balance: formal, informal, radial
- Rule of thirds, golden ratio
- Focal point — อะไรดึงสายตาก่อน
- Visual flow / eye movement
- Rhythm & repetition

**7. Light & Shadow**
- Source: natural, artificial, multiple, direction
- Quality: hard, soft, diffused
- Function: descriptive, dramatic, symbolic
- Chiaroscuro, sfumato, tenebrism

**8. Scale & Proportion**
- Actual size of work
- Internal scale (figures relative to environment)
- Hierarchical scale (size = importance)

### Medium-Specific Considerations

**Painting**:
- Brushwork: visible, smooth, impasto, glazing
- Pigment behavior
- Support: canvas, panel, paper, wall

**Sculpture**:
- Material: marble, bronze, wood, mixed
- Technique: carving, modeling, assemblage, casting
- Viewing angles
- Relationship to architecture/site

**Photography**:
- Format: digital, film (35mm/medium/large), polaroid
- Black & white vs color
- Aperture/shutter effects
- Angle (high, eye-level, low, dutch)
- Print size & paper

**Print/Graphic Design**:
- Method: woodcut, etching, lithograph, screenprint, digital
- Edition & uniqueness
- Typography (ถ้าเกี่ยวข้อง)

**Digital/New Media**:
- Resolution
- Algorithmic vs hand-drawn
- Generative process
- Interactivity
- Platform specificity

### Formal Analysis Output Structure

```markdown
## Formal Analysis: [Title]

### Overview
[1-2 sentence statement of what work is and immediate visual impression]

### Detailed Description
[Systematic walk-through: what does the viewer see? Use present tense.]

### Element Analysis
[เลือก 3-5 elements ที่สำคัญที่สุด — วิเคราะห์ลึก]

### Compositional Strategy
[How are elements organized? What does the composition do?]

### Initial Interpretation
[What might these formal choices suggest? — careful, hedge claims]
```

## Method 2: Iconographic & Iconological Analysis (Panofsky)

Erwin Panofsky's framework (1939, "Studies in Iconology") = 3 ระดับ:

### Level 1: Pre-iconographic Description (Primary/Natural Subject)

อะไรคือสิ่งที่เห็น โดยไม่อ้างอิง culture-specific knowledge?
- "ผู้ชายถือดาบยืนอยู่บนภูเขา"
- "ผลไม้จัดวางบนผ้าปูโต๊ะ"

ทักษะที่ต้องใช้: practical experience (รู้ว่าผู้ชายคืออะไร, ดาบคืออะไร)

### Level 2: Iconographic Analysis (Secondary/Conventional Subject)

สิ่งที่เห็นหมายถึงอะไรในระบบสัญลักษณ์ทางวัฒนธรรม?
- "ผู้ชายถือดาบยืนบนภูเขา" → "นักบุญ Michael เหยียบ Lucifer"
- ต้องรู้: literary sources (Bible, mythology, allegory tradition, จิตรกรรมไทย — ชาดก, รามเกียรติ์)

ทักษะ: knowledge of literary sources, conventions

### Level 3: Iconological Analysis (Intrinsic Meaning)

ความหมายลึกที่บอกอะไรเกี่ยวกับ:
- Worldview ของช่วงเวลา/วัฒนธรรม
- Class, gender, ideology
- Symbolic relationships ที่ artist อาจไม่ได้ตั้งใจสื่อ

ทักษะ: synthetic intuition + cultural history

### ตัวอย่างการประยุกต์กับงานไทย

**จิตรกรรมฝาผนังวัดสุวรรณดาราราม**:
- Level 1: ผู้คนแต่งกายโบราณ ในบริบทพระราชวัง
- Level 2: ฉากในพระราชนิพนธ์เรื่องอิเหนา (ต้องรู้วรรณคดี)
- Level 3: การ legitimize อำนาจราชวงศ์ผ่านการนำเรื่องชาวต่างประเทศมาใช้, ความสัมพันธ์รัตนโกสินทร์-เอเชียอาคเนย์

### ⚠️ ข้อจำกัดของ Panofsky

- Eurocentric — สมมติว่ามี "literary tradition" ชัดเจน
- ลำดับชั้นแบบ Western — งานไทยอาจไม่แยกระดับชัด
- เน้น content เกินไป, ละเลย formal/material
- ปรับใช้ได้ แต่ต้อง recognize limitations

## Method 3: Semiotic Analysis

### Saussure's Foundations
- Signifier (รูป) + Signified (ความหมาย) = Sign
- Arbitrary relationship — convention ทำให้ผูกกัน
- Synchronic (ตอนนี้) vs diachronic (เปลี่ยนผ่านเวลา)

### Peirce's Trichotomy (ใช้บ่อยในงานศิลปะ)

| Type | Relationship | ตัวอย่าง |
|------|-------------|----------|
| Icon | คล้ายคลึง | ภาพถ่าย, portrait |
| Index | สัมผัสจริง/causal | รอยเท้า, ควัน → ไฟ |
| Symbol | convention | ธงชาติ, ลายไทย |

### Barthes: Denotation & Connotation

- **Denotation** — ความหมายตามตัวอักษร
- **Connotation** — ความหมายแฝง/วัฒนธรรม
- **Myth** — เมื่อ connotation กลายเป็น "common sense"

### Barthes' Studium & Punctum (สำหรับภาพถ่าย)

- Studium — ความสนใจทั่วไป, cultural meaning
- Punctum — รายละเอียดที่กระแทกใจส่วนตัว

### Application Steps

1. ระบุ signifiers สำคัญในภาพ (visual elements + content)
2. ระบุ signifieds — denotation
3. วิเคราะห์ connotations ใน specific cultural context
4. ระบุ codes ที่ภาพใช้ (genre conventions, period style, cultural rituals)
5. วิเคราะห์ how meaning is constructed — ผ่าน opposition? association? transformation?

## Method 4: Contextual / Social Art History

วิเคราะห์งานในบริบท — วิจารณ์ formalism ที่แยกงานจากสังคม

### Frameworks สำคัญ

**Marxist Art History (Hauser, Berger, Clark)**:
- ใครจ้าง? ใครเสพ? ใครได้ประโยชน์?
- Class dimensions
- Mode of production

**Feminist Art History (Pollock, Nochlin, Parker)**:
- "Why have there been no great women artists?" (Nochlin)
- Gender ใน representation
- Women as artists, audiences, subjects, patrons

**Postcolonial (Said, Bhabha, Mitter)**:
- "Orientalism" — Western representation ของ "Other"
- Hybridity, mimicry
- Decentering canon

**Visual Culture Studies (Mirzoeff, Mitchell)**:
- ทุก image, ไม่ใช่แค่ "art"
- Image as social agent

### Questions for Contextual Analysis

1. **Production**: ใครสร้าง? ทำที่ไหน? เมื่อไหร่? ภายใต้เงื่อนไขใด? (commission, copyright, freedom)
2. **Distribution**: ภาพเดินทางอย่างไร? ใครเห็น? (gallery, market, public, private)
3. **Reception**: ผู้ชมเป้าหมายคือใคร? ตอบสนองอย่างไร? (period reception vs current reception)
4. **Function**: งานนี้ทำหน้าที่อะไรในสังคม? (devotion, propaganda, decoration, critique)
5. **Power**: ภาพนี้ตอกย้ำหรือท้าทาย power structures?

## Method 5: Comparative Analysis

### Pair Selection Logic

อย่าเปรียบเทียบ random — มีเหตุผลในการเลือก:
- Same artist, different periods
- Same subject, different artists/periods
- Same style, different cultures
- Influence/dialogue (one work responds to another)
- Contrast to highlight specific issue

### Comparison Matrix

| Aspect | Work A | Work B | Comparison |
|--------|--------|--------|------------|
| Subject | ... | ... | similar/different in X way |
| Composition | ... | ... | ... |
| Color | ... | ... | ... |
| Context | ... | ... | ... |
| Function | ... | ... | ... |

### โครงสร้าง output

หลีกเลี่ยง "งาน A คือ X. งาน B คือ Y" (parallel description)
เน้น **integrated comparison**:

```
"แม้ทั้งสองผลงานใช้ภาพดอกบัวเป็น central motif แต่...
ในงานของ X ดอกบัวทำหน้าที่ A ผ่าน [evidence]
ขณะที่งานของ Y ดอกบัวทำหน้าที่ B ผ่าน [evidence]
ความแตกต่างนี้สะท้อน..."
```

## บริบทเฉพาะของศิลปะไทย/ล้านนา/อาเซียน

### กรอบที่ต้องตระหนัก

1. **Hierarchy of attention** — Western art history เน้น painting/sculpture, ละเลยงานช่าง, decorative arts ที่เป็นแกนของศิลปะไทย

2. **Anonymous tradition** — งานช่างไทยส่วนใหญ่ไม่มี attribution ชื่อบุคคล, biography-based analysis ใช้ไม่ได้

3. **Religious function** — งานพุทธศิลป์ทำหน้าที่ devotional ก่อน aesthetic, การวิเคราะห์แค่ formal aesthetic ขาดมิติ

4. **Material specificity** — ลายรดน้ำ, ลงรักปิดทอง, จารใบลาน, ผ้าทอ — แต่ละสื่อมีระบบ aesthetic ของตัวเอง

5. **Regional vs central** — งานล้านนา, อีสาน, ใต้ มีระบบสุนทรียะของตัวเอง ไม่ใช่ "เพี้ยน" จาก Bangkok standard

### Frameworks ที่ใช้ได้ดี

- "Lokavibhāga" (cosmology) สำหรับจิตรกรรมไตรภูมิ
- Concept of "Citra" ในศิลปกรรมพุทธ
- "Lai Thai" classification system
- งานของ Forrest McGill, Apinan Poshyananda, Sant Suchittranonth, Henry Ginsburg, ยุคก่อน — ปริซึ่มผสานไทย+โลก

## Workflow

```
1. รับข้อมูลผลงาน (artist, title, year, medium, dimensions)
2. ดูภาพและทำ formal description ก่อน (ห้ามรีบไป interpretation)
3. ถาม user ว่าต้องการ method ไหน (formal/iconographic/semiotic/contextual/comparative)
4. ทำการวิเคราะห์ตาม method
5. ระวัง over-interpretation — เก็บ claim ที่มี evidence support เท่านั้น
6. ระบุ limitations ของการวิเคราะห์
7. ส่ง output เป็น structured markdown
```

## Anti-patterns

🚫 **Skip to interpretation** — กระโดดข้าม description ไปสู่ "ภาพนี้แสดงถึง..."
🚫 **Cultural assumption** — สมมติว่า audience เข้าใจ symbolism เดียวกับเรา
🚫 **Romantic art talk** — "ภาพนี้สื่อความรู้สึก..." โดยไม่ระบุ visual evidence
🚫 **Gendered/ethnic essentialism** — "ศิลปินผู้หญิงมักจะ..." "งานของชาวล้านนาเป็น..."
🚫 **Provenance-blind** — ไม่ตรวจสอบว่าภาพ authentic, ใส่ตำแหน่ง, ปีถูก

## References

- Panofsky, E. (1939). *Studies in Iconology.*
- Barthes, R. (1977). *Image-Music-Text.*
- Berger, J. (1972). *Ways of Seeing.*
- Mitchell, W.J.T. (2005). *What Do Pictures Want?*
- Pollock, G. (1988). *Vision and Difference.*
- D'Alleva, A. (2012). *Methods & Theories of Art History (2nd ed.).*

ไทย/อาเซียน:
- McGill, F. (2003). *The Kingdom of Siam: The Art of Central Thailand.*
- Apinan Poshyananda (1992). *Modern Art in Thailand.*
- ศิลป์ พีระศรี (กลุ่มบทความ)
- ดู references/ สำหรับรายการเพิ่มเติม

---

## Iron Rules

⚠️ **IRON RULE — THREE LEVELS**: ทุก analysis section ต้องผ่านครบ 3 ระดับ (Description → Analysis → Interpretation) — ห้ามข้าม Description ไปสู่ Interpretation โดยตรง

⚠️ **IRON RULE — EVIDENCE-BASED INTERPRETATION**: ทุก interpretation ต้องอ้างกลับ specific visual elements — ห้ามใช้ impressionistic claims โดยไม่มีหลักฐานจาก artwork

⚠️ **IRON RULE — CULTURAL FRAMEWORK**: การวิเคราะห์งาน Thai/Lanna/Buddhist ด้วย Western framework ต้องมี explicit acknowledgment ของข้อจำกัด และต้องเสริมด้วย Thai/Buddhist analytical sources

⚠️ **IRON RULE — IMAGE VERIFICATION**: analysis ต้องระบุชัดว่าเห็น original หรือ reproduction — ถ้าเป็น reproduction ต้องระบุข้อจำกัด (scale, color accuracy, texture) ใน methodology

---

## Failure Modes Reference

ดู `references/failure_paths.md` สำหรับ 8 failure scenarios:
F1: No Image | F2: Method-Object Mismatch | F3: Description-Only | F4: Context Overload | F5: Subjective Overclaim | F6: Western Framework Imposition | F7: Missing Primary Source | F8: Comparative Imbalance

---

## Arts Research Failure Modes (เฉพาะ visual analysis)

| Code | Pattern | อาการ | Test |
|------|---------|-------|------|
| FM-B | Catalog Description | บรรยายผลงานโดยไม่วิเคราะห์ | หา interpretive moves |
| FM-D | Western Frame Imposition | ใช้กรอบตะวันตกกับงานไทยโดยไม่ reflect | framework ตรงบริบทไหม? |
| FM-A | Decorative Theory | cite Panofsky/Barthes แต่ไม่ได้ใช้จริง | ตัดชื่อทฤษฎีออก — argument ยังเดินไหม? |

ดูคำนิยามครบ: `../shared/cross_agent_quality_definitions.md`

---

## Modes (Updated)

| Mode | Use Case |
|------|----------|
| `formal` | Formal analysis เน้น visual elements (line, color, composition) |
| `iconographic` | Panofsky's 3 levels — สำหรับ representational art |
| `semiotic` | Sign system analysis — สำหรับ meaning production |
| `contextual` | Social/historical/cultural context |
| `comparative` | เปรียบเทียบ 2+ ผลงาน |
| `thai-buddhist` | Thai/Buddhist iconographic tradition เฉพาะ |
| `comprehensive` (default) | Combined multi-method |

---

## Integration กับ Skills อื่น

| ต้องการ | ใช้ |
|--------|-----|
| หา context ของงานที่วิเคราะห์ | arts-deep-research |
| เขียน analysis section | arts-paper-writer → section mode |
| ตรวจ analysis | arts-paper-reviewer → methodology-focus |
| cite ผลงาน | arts-citation-formatter → artwork type |

---

## Shared Resources

- `../shared/cross_agent_quality_definitions.md` — Analysis Levels (3 levels definition)
- `../shared/tci_compliance_guide.md` — Image caption และ figure requirements

---

## Version History

| Version | วันที่ | การเปลี่ยนแปลง |
|---------|-------|--------------|
| 2.0.0 | 2026-05-05 | เพิ่ม Iron Rules (4 rules), failure_paths reference, FM codes, thai-buddhist mode, skill integration table, shared resources, version history |
| 1.0.0 | — | Initial release |
