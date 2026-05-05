---
name: arts-deep-research
description: ทบทวนวรรณกรรมและสืบค้นแหล่งข้อมูลเชิงลึกสำหรับงานวิจัยทางศิลปะ ครอบคลุมฐานข้อมูลศิลปะระดับสากลและไทย รวมถึง primary sources (ผลงานศิลปะ, การแสดง, จดหมายเหตุ, สัมภาษณ์). Use when the user asks for "ทบทวนวรรณกรรม", "literature review", "หาเอกสารอ้างอิง", "หาเปเปอร์เกี่ยวกับ", "งานวิจัยที่เกี่ยวข้อง", "research gap", "primary sources for art research", "หาแหล่งข้อมูลทางศิลปะ", or needs to find arts-specific scholarly sources for visual arts, design, music, performance, art history, archaeology, aesthetics, photography, or art education research. MUST trigger this skill whenever the user mentions any kind of literature search or reference gathering related to arts/creative research.
license: MIT
metadata:
  author: CAMT Research Support Unit
  version: 1.0.0
  parent_skill: arts-research-pipeline
---

# Arts Deep Research

ทบทวนวรรณกรรมเชิงลึกสำหรับงานวิจัยทางศิลปะ ออกแบบเฉพาะสำหรับสาขาวิชาที่ CAMT รับผิดชอบ

## Trigger Keywords

ภาษาไทย: ทบทวนวรรณกรรม, หาเอกสารอ้างอิง, literature review, หาเปเปอร์, งานวิจัยที่เกี่ยวข้อง, สืบค้นวรรณกรรม, research gap, แหล่งข้อมูลปฐมภูมิ, ค้นหางานวิจัย

English: literature review, scholarly search, find papers, primary sources, art bibliography, research gap analysis

## Modes

| Mode | Output |
|------|--------|
| `lit-review` (default) | Literature matrix + narrative review |
| `quick` | Top 10-15 sources สรุปสั้นๆ |
| `systematic` | PRISMA-style systematic review |
| `gap-analysis` | identify research gap เน้นช่องว่างวิจัย |
| `primary-source` | เน้น primary sources (artworks, archives) |
| `historiographic` | ทบทวน historiography ของหัวข้อ |

## Workflow 6 ขั้นตอน

### 1. Define Search Scope

ถาม user ให้ชัด:
- หัวข้อวิจัย และคำสำคัญ (Thai + English)
- สาขา/สาขาย่อย
- ขอบเขตเวลา (เช่น 2000-ปัจจุบัน)
- ขอบเขตภูมิศาสตร์ (โลก, เอเชีย, ไทย, ล้านนา)
- ภาษาที่รับ (Thai, English, อื่นๆ)
- ประเภทแหล่ง (peer-reviewed only, รวม books/catalogs/dissertations?)

### 2. Identify Databases (เลือกฐานข้อมูลตามสาขา)

ดูคู่มือใน `references/databases.md` (จะมี detailed list) หรือใช้ตารางย่อนี้:

**ฐานข้อมูลทั่วไปทางศิลปะ/มนุษยศาสตร์**:
- JSTOR Arts & Sciences I-XV
- Project MUSE
- Cambridge Core
- Oxford Academic / Oxford Art Online (Grove Art)
- Taylor & Francis
- SAGE Journals
- Art & Architecture Source (EBSCO)
- ArtBibliographies Modern (ProQuest)
- Avery Index to Architectural Periodicals

**สาขาเฉพาะ**:
- *ดนตรี*: RILM Abstracts of Music Literature, RIPM, JSTOR Music
- *ทัศนศิลป์/ออกแบบ*: BHA (Bibliography of the History of Art), Design and Applied Arts Index (DAAI)
- *การแสดง*: International Bibliography of Theatre & Dance
- *ภาพถ่าย*: Photographic Memory, History of Photography journal archives
- *โบราณคดี*: AATA Online, Web of Science (Archaeology category)
- *สื่อศิลปะ*: Leonardo Online, Rhizome.org archives
- *ศิลปศึกษา*: ERIC + JSTOR (สาขา education)

**ฐานข้อมูลไทย**:
- TCI (Thai-Journal Citation Index) — tci-thaijo.org
- ThaiLIS / ThaiJO
- ห้องสมุดดิจิทัลของมหาวิทยาลัย: CMU CMUL, Chula, Silpakorn
- หอสมุดศิลปะ (Silpakorn Art Library)
- ศูนย์ข้อมูลทางศิลปวัฒนธรรม
- จดหมายเหตุแห่งชาติ (National Archives)

**คลังภาพ/ผลงาน (primary sources)**:
- Google Arts & Culture
- Europeana
- Wikimedia Commons (สำหรับ public domain)
- พิพิธภัณฑ์ออนไลน์: MoMA, Tate, Met, V&A, Rijksmuseum
- พิพิธภัณฑ์ไทย: หอศิลป์ มศก., MOCA, BACC, พิพิธภัณฑสถานแห่งชาติ
- IMSLP (สำหรับโน้ตเพลง public domain)

**Open Access ที่ต้องรู้**:
- DOAJ (Directory of Open Access Journals)
- arXiv (สำหรับ digital art / generative)
- HAL (French open archive)
- Semantic Scholar (สำหรับ verify references)

### 3. Construct Search Queries

**กลยุทธ์**:
- ใช้ Boolean: AND, OR, NOT, ใส่ "" สำหรับ exact phrase
- Truncation: artist* (ดักทั้ง artist, artists, artistic)
- ใช้คำพ้องและคำที่เกี่ยวข้อง (เช่น "thai painting" OR "painting in thailand" OR "siamese painting")
- ค้นทั้งภาษาอังกฤษและภาษาไทย แยกชุด query
- ค้นในชื่อศิลปิน/ผู้สร้างสรรค์ที่เป็น central figure
- ค้นใน citation network — เริ่มจาก seminal paper แล้ว forward/backward citation

**ตัวอย่าง search query สำหรับงานวิจัย "การออกแบบลายพิมพ์ผ้าล้านนาร่วมสมัย"**:
```
("Lanna" OR "northern Thai" OR "ล้านนา") AND ("textile design" OR "fabric pattern" OR "ลายผ้า") AND ("contemporary" OR "modern" OR "ร่วมสมัย")
```

### 4. Screen and Select

**Inclusion criteria** (ใส่อะไรเข้า review):
- Peer-reviewed, หรือเป็น authoritative source (พิพิธภัณฑ์, หอสมุด, university press)
- ตรงประเด็นวิจัย
- อยู่ในขอบเขตเวลาและภาษาที่กำหนด

**Exclusion criteria**:
- บทความ trade/popular ที่ไม่ใช่ academic (ยกเว้นเป็น primary source)
- งานที่ถูก retract
- Predatory journals (ตรวจกับ Beall's list หรือ DOAJ)

**สำหรับ primary sources ทางศิลปะ**:
- ระบุ provenance (ที่มา) ให้ชัด
- ตรวจ authenticity ถ้าเป็นงานเก่า
- บันทึก current location และ accession number

### 5. Build Literature Matrix

สร้างตารางสรุปแบบนี้ (export เป็น .xlsx ได้ — เรียก `xlsx` skill ถ้ามี):

| # | Author(s) | Year | Title | Journal/Publisher | Method | Key Findings | Theoretical Frame | Relevance |
|---|-----------|------|-------|-------------------|--------|--------------|-------------------|-----------|

สำหรับ primary sources ใช้คอลัมน์ต่างกัน:

| # | Artist/Creator | Title of Work | Year | Medium | Dimensions | Location | Significance |
|---|----------------|---------------|------|--------|-----------|----------|--------------|

### 6. Synthesize: Narrative Review + Gap Identification

**Output structure**:

```markdown
## Literature Review

### 1. Theoretical Foundations
[ใครคือนักทฤษฎีหลัก, มี framework อะไรบ้าง, evolution ของแนวคิด]

### 2. Empirical/Practice Studies
[งานวิจัย/งานสร้างสรรค์ที่เกี่ยวข้องโดยตรง — จัดกลุ่มตามแนวทาง ไม่ใช่ตามผู้เขียน]

### 3. Methodological Approaches
[วิธีวิจัยที่งานก่อนหน้าใช้ — ข้อดีข้อจำกัด]

### 4. Cultural/Contextual Studies
[งานที่ศึกษาบริบทวัฒนธรรม — สำคัญมากสำหรับงานศิลปะไทย/อาเซียน]

### 5. Research Gap
[ระบุชัดว่าช่องว่างอยู่ตรงไหน 1-3 ข้อ และงานคุณจะปิดช่องว่างนั้นอย่างไร]
```

## หลักการสำคัญ

### Critical reading checklist (ตรวจทุกบทความที่อ่าน):
1. RQ ของผู้เขียนคืออะไร?
2. Method/method ใช้ — เหมาะสมไหม?
3. Theoretical frame — มาจากใคร, เหมาะกับบริบทไหม?
4. ข้อสรุป — มีหลักฐานพอไหม?
5. ข้อจำกัดที่ผู้เขียนยอมรับ + ที่ไม่ยอมรับ
6. มีอคติอะไร (theoretical, cultural, methodological)?
7. งานนี้สนับสนุน, ขัดแย้ง, หรือเสริม RQ ของเราอย่างไร?

### บริบทไทย/ล้านนา/อาเซียน

**ปัญหา**: literature ทางศิลปะเอเชียตะวันออกเฉียงใต้ในวารสารระดับโลกยังจำกัด ต้องผสาน:
- งานวิชาการระดับโลก (theoretical/comparative)
- งานวิชาการในภูมิภาค (regional knowledge)
- งานวิชาการไทย (deep contextual knowledge)
- Primary sources ในภาษาไทย/ภาษาท้องถิ่น

ห้ามใช้แค่งานต่างประเทศ — ขาดบริบท
ห้ามใช้แค่งานไทย — ขาด theoretical depth

### การจัดการ References

แนะนำให้ใช้:
- Zotero (ฟรี, รองรับภาษาไทย, plugin Word/Google Docs)
- Mendeley
- EndNote (ถ้า ม.มีให้)

Output bibliography ตามรูปแบบที่ `arts-citation-formatter` skill กำหนด

## ⚠️ ข้อควรระวังเรื่อง AI Hallucination

AI มีแนวโน้มสูงที่จะ:
- **สร้างชื่อบทความปลอม** ที่ดู plausible แต่ไม่มีอยู่จริง
- **สร้างผู้เขียนปลอม** หรือสลับชื่อ
- **สร้างปีและวารสารปลอม**
- **สร้าง DOI ปลอม**
- **อ้าง quote ปลอม** จากนักวิชาการชื่อดัง

**กฎเหล็ก**: ทุก reference ที่ AI suggest **ต้องตรวจสอบจริง**ใน Google Scholar / JSTOR / TCI ก่อนใช้
ถ้าตรวจไม่เจอ → ถือว่าไม่มีจริง อย่าใช้
ถ้า AI ให้ DOI → ตรวจที่ doi.org/[doi] ต้องเปิดได้จริง

## Integration with Pipeline

Output ของ skill นี้ป้อนต่อให้:
- Stage 3 ของ `arts-research-pipeline` (เป็นข้อมูลตั้งต้นการวิเคราะห์)
- `arts-paper-writer` (ใช้สร้างส่วน Literature Review ในบทความ)

## References

ดูเอกสารเพิ่มเติมใน `references/`:
- `databases.md` — รายละเอียดฐานข้อมูล + วิธีเข้าถึงผ่าน CMU library
- `search_strategies.md` — เทคนิคการ search เฉพาะแต่ละสาขา
- `verifying_sources.md` — วิธีตรวจสอบ AI-generated references
