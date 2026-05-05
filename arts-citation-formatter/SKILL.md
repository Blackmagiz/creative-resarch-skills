---
name: arts-citation-formatter
description: คู่มือและ template การอ้างอิง (citation) สำหรับงานวิจัยทางศิลปะ ครอบคลุม APA 7, Chicago, MLA, TCI standards พร้อม template เฉพาะสำหรับ artwork, performance, film, archival material, exhibition catalog, oral interview ที่ generic citation guide ไม่ได้ครอบคลุม. Use when the user asks about "การอ้างอิง", "citation", "บรรณานุกรม", "reference list", "อ้างอิง APA/Chicago/MLA", "อ้างอิงผลงานศิลปะ", "citing artwork", "citing performance", "citing archival", "citing interview", or needs help formatting any kind of arts-specific reference. MUST trigger this skill whenever a user has questions about citation formatting, especially for non-standard arts sources.
license: MIT
metadata:
  author: CAMT Research Support Unit
  version: 1.0.0
  parent_skill: arts-research-pipeline
---

# Arts Citation Formatter

คู่มือการอ้างอิงสำหรับงานวิจัยทางศิลปะ — ครอบคลุมแหล่งที่ generic citation guide ไม่ได้พูดถึง (artworks, performances, archival, interviews, exhibitions)

## Trigger Keywords

ภาษาไทย: การอ้างอิง, citation, บรรณานุกรม, reference, รายการอ้างอิง, APA, Chicago, MLA, อ้างอิงงานศิลปะ, อ้างอิงเอกสาร, อ้างอิงสัมภาษณ์

English: citation, reference list, bibliography, APA, Chicago, MLA, cite artwork, cite performance, cite archival source

## Modes

| Mode | Use Case |
|------|----------|
| `format` (default) | format reference list ให้ตรงตามรูปแบบ |
| `single-source` | format แค่ 1 source |
| `convert` | แปลงรูปแบบ (e.g., APA → Chicago) |
| `verify` | ตรวจสอบความถูกต้องของ citations |
| `tci` | format ตามมาตรฐาน TCI Thai journals |

## Citation Style Quick Reference

### เลือก Style ตามสาขา

| Field | Recommended Style |
|-------|------------------|
| Art History | Chicago Notes-Bibliography หรือ Author-Date |
| Art Criticism | Chicago / MLA |
| Aesthetics & Philosophy | Chicago Author-Date / APA |
| Music & Musicology | Chicago / MLA |
| Performance Studies | MLA / Chicago |
| Design Research | APA 7 |
| Media Studies | APA 7 / MLA |
| Art Education | APA 7 |
| Archaeology | SAA (Society for American Archaeology) / Chicago |
| Thai journals | TCI standard (มักเป็น APA-modified ภาษาไทย) |

**คำแนะนำ**: ตรวจสอบ guideline ของวารสารเป้าหมายก่อนเสมอ

## Part 1: Standard Source Types

### Journal Article

**APA 7**:
```
Author, A. A., & Author, B. B. (Year). Title of article. Journal Name, 
Volume(Issue), Pages. https://doi.org/xxxxx
```

**Chicago Author-Date**:
```
Author, First Name, and First Name Author. Year. "Title of Article." 
Journal Name Volume (Issue): Pages. https://doi.org/xxxxx.
```

**MLA 9**:
```
Author, First Name, and First Name Author. "Title of Article." Journal 
Name, vol. X, no. Y, Year, pp. XX-XX.
```

**TCI (ภาษาไทย)**:
```
ชื่อผู้แต่ง. (ปี). ชื่อบทความ. ชื่อวารสาร, ปีที่(ฉบับที่), หน้าที่.
```

### Book

**APA 7**:
```
Author, A. A. (Year). Title of book. Publisher.
```

**Chicago Author-Date**:
```
Author, First Last. Year. Title of Book. Place: Publisher.
```

### Book Chapter

**APA 7**:
```
Author, A. A. (Year). Title of chapter. In E. E. Editor (Ed.), Title of 
book (pp. XX-XX). Publisher.
```

### Edited Volume

**Chicago**:
```
Editor, First Last, ed. Year. Title of Book. Place: Publisher.
```

## Part 2: Arts-Specific Sources

### A. Artwork (Original)

**Chicago Note** (most common in art history):
```
Artist Name, Title of Work, Year, medium, dimensions, location.
```

**Example**:
```
Vincent van Gogh, *The Starry Night*, 1889, oil on canvas, 73.7 x 92.1 cm,
Museum of Modern Art, New York.

ถวัลย์ ดัชนี, *พระพุทธรูปทรงเครื่อง*, พ.ศ. 2540, สีน้ำมันบนผ้าใบ, 
200 x 150 ซม., พิพิธภัณฑ์ศิลปะถวัลย์ ดัชนี, เชียงราย.
```

**APA 7** (works of art):
```
Artist, A. (Year). Title of work [Medium]. Institution, City, Country.
URL (if applicable)
```

**Caption format under image** (most common):
```
Artist, *Title*, Year, medium, dimensions. Location/Collection.
[Photo credit if applicable]
```

### B. Artwork in Reproduction (e.g., from a book)

ต้อง cite ทั้งงานต้นฉบับ และ source ของ image:

```
Hokusai, *The Great Wave off Kanagawa*, c. 1830-32, woodblock print, 
25.7 x 37.9 cm, Metropolitan Museum of Art, New York. Reproduced in 
Roni Neuer, *Ukiyo-e: 250 Years of Japanese Art* (London: Mayflower 
Books, 1979), 124, fig. 89.
```

### C. Photographs

**Photographer different from artist depicted**:
```
Photographer, *Title of Photograph*, Year, gelatin silver print [or other],
dimensions, collection. Photo credit.
```

**Documentary photograph (ไม่ใช่ artistic)**:
```
Author/Photographer. (Year). [Description of photograph]. Archive/Source.
```

### D. Performance / Concert

**Live performance** (Chicago):
```
Performer Name. Title of Work, by Composer/Choreographer. Performed at 
Venue, City, Date.
```

**Example**:
```
Bangkok Symphony Orchestra. Symphony No. 9 in D Minor, op. 125, by 
Ludwig van Beethoven. Performed at Thailand Cultural Centre, Bangkok, 
March 15, 2025.

นาฏศิลปิน สวนสุนันทา. *รามเกียรติ์ ตอนหนุมานถวายแหวน*. แสดง ณ ศูนย์
วัฒนธรรมแห่งประเทศไทย, กรุงเทพฯ, 5 ธันวาคม 2566.
```

**Recorded performance**:
```
Performer Name. Title of Work, by Composer. Conducted by Conductor. 
Recorded Date. Label, year released. Format (CD, vinyl, streaming URL).
```

### E. Film / Video

**APA 7**:
```
Director, D. (Director). (Year). Title of film [Film]. Production Company.
URL (if streaming)
```

**Chicago Author-Date**:
```
Director, Director. Year. Title of Film. Place: Studio/Company.
```

**Example**:
```
Apichatpong Weerasethakul (director). (2010). Lung Boonmee raluek chat 
[Uncle Boonmee Who Can Recall His Past Lives] [Film]. Kick the Machine 
Films.

อภิชาติพงศ์ วีระเศรษฐกุล (ผู้กำกับ). (2553). *ลุงบุญมีระลึกชาติ* [ภาพยนตร์]. 
Kick the Machine Films.
```

### F. Music Recording

**Chicago Author-Date**:
```
Performer/Composer. Year. "Title of Track." Track number on Album Name. 
Label, year released. Format.
```

**Example**:
```
Mozart, Wolfgang Amadeus. 1996. "Eine kleine Nachtmusik, K. 525." Track 1
on Mozart: The Best 50. Naxos, 1996. CD.

ลานนาคำหล้า. 2541. "เพลินจิต." Track 3 on อัลบั้มอักษรล้านนา. ค่ายเพลงล้านนา.
```

### G. Music Score

**Chicago Bibliography**:
```
Composer, First Last. Title of Work. Edited by First Last. Place: 
Publisher, Year.
```

### H. Exhibition Catalog

**Chicago**:
```
Editor/Curator, First Last, ed. Title of Exhibition. Exhibition catalog. 
Place: Museum/Publisher, Year.
```

**Example**:
```
Poshyananda, Apinan, ed. Modernity and Beyond: Themes in Southeast Asian 
Art. Exhibition catalog. Singapore: Singapore Art Museum, 1996.
```

### I. Catalog Essay (essay within exhibition catalog)

```
Author, First Last. "Title of Essay." In Title of Exhibition, edited by 
First Last, page range. Exhibition catalog. Place: Museum/Publisher, Year.
```

### J. Museum Wall Text / Object Label

ปกติไม่ cite ใน formal academic — ถ้าจำเป็น:
```
Museum/Institution. "Title of Object" wall text. Exhibition Title, Date 
visited. City.
```

### K. Interview (Personal/Field)

**Chicago Author-Date**:
```
Interviewee, First Last. Year. Interview by Interviewer Name. Date. 
Location. Format (e.g., audio recording in possession of author).
```

**Example**:
```
จันทร์ทิพย์ จันทร์มี. 2566. สัมภาษณ์โดย กันยา รักไทย. 15 มีนาคม. 
หมู่บ้านม้ง บ้านขุนช่างเคี่ยน, เชียงใหม่. บันทึกเสียงในความครอบครองของผู้สัมภาษณ์.
```

**APA 7**: Personal interviews ไม่ใส่ใน reference list — cite in-text only:
```
(J. T. Smith, personal communication, March 15, 2025)
```

### L. Published Interview

```
Interviewee, First Last. "Title of Interview." Interview by First Last. 
Publication Name Volume, no. Issue (Year): Pages.
```

### M. Archival Source

**Chicago** (preferred for archives):
```
[Document description], [date], [collection name and identifier], 
[archive name], [city, country].
```

**Example**:
```
Letter from King Chulalongkorn to Phraya Phaibun, March 12, 1907, 
ร.5 บ.6/24, หอจดหมายเหตุแห่งชาติ, กรุงเทพมหานคร.

Field notebook of Henri Mouhot, vol. 3, p. 45, MS 3208, Société de 
Géographie, Bibliothèque nationale de France, Paris.
```

### N. Manuscript / Old Book

```
[Author]. [Title]. [Date or estimated]. [MS number/identifier]. 
[Repository], [City].
```

**Example**:
```
[ไม่ปรากฏชื่อ]. *จารึกใบลานเรื่องอานิสงส์ตักบาตรเทโว*. ราว พ.ศ. 2370.
หจช.ลพ. 12/3. หอสมุดแห่งชาติ เฉลิมพระเกียรติฯ ลำพูน.
```

### O. Digital/Online Artwork

```
Artist Name, *Title*, Year, medium/format, URL (accessed Date).
```

**Example**:
```
Refik Anadol, *Machine Hallucinations*, 2019, AI-generated video, 
https://refikanadol.com/works/machine-hallucinations (accessed April 12, 2026).
```

### P. NFT / Blockchain Art

```
Artist Name, *Title*, Year, NFT (medium description), Token ID: xxx, 
Platform (e.g., OpenSea, Foundation), URL.
```

### Q. Performance Documentation (Video)

```
Artist/Choreographer. *Title of Performance*. Year (premiered). Performance
recorded at Venue, City, Date. Video documentation, duration. URL or 
collection.
```

### R. Score / Choreographic Notation

```
Composer/Choreographer. *Title of Work*. Year. Notation type (e.g., 
Labanotation, full score). Place: Publisher, Year of edition.
```

### S. Software / Code (สำหรับ generative art, digital design)

**APA 7**:
```
Author, A. A. (Year). Title of software (Version) [Computer software]. 
Publisher. URL
```

### T. Social Media / Online Post

ถ้าเป็น primary source (เช่น artist's Instagram):
```
Artist Name [@handle]. (Date). Caption [Image/Video]. Platform. URL
```

## Part 3: Thai-Language Citations

### Conventions ที่ต้องรู้

1. **Author name order** — ในภาษาไทยใส่ "ชื่อ นามสกุล" ไม่กลับ
2. **Date** — ใช้ พ.ศ. หรือ ค.ศ. ตามที่วารสารกำหนด ระบุชัดเสมอ
3. **In-text** ภาษาไทย: (ผู้แต่ง, ปี, หน้า) เช่น (สมชาย ใจดี, 2565, น. 45)
4. **Bibliography** เรียงตาม "ชื่อ" ภาษาไทย (ก-ฮ) แล้วตามด้วยภาษาอังกฤษ (A-Z)

### TCI Standard Format

ตรวจสอบ guideline ของวารสารแต่ละแห่ง — ปรับตาม APA 7 modified

```
ผู้แต่ง. (พ.ศ.). ชื่อบทความ. ชื่อวารสาร, ปีที่(ฉบับที่), เลขหน้า.
```

ตัวอย่าง:
```
สาคร เลิศคุณวุฒิ. (2563). จิตรกรรมฝาผนังล้านนา: การศึกษาเชิงเปรียบเทียบ
ระหว่างสำนักล้านนากับสุโขทัย. วารสารวิชาการศิลปะ, 12(2), 45-67.
```

### Romanization

ถ้าวารสารต้องการ romanization ของชื่อไทย:
- ใช้ Royal Thai General System of Transcription (RTGS) — ราชบัณฑิตยสถาน
- หรือระบบที่ผู้แต่งเลือกใช้ (consistent ตลอด paper)

## Part 4: In-text Citations

### APA 7
- (Author, Year)
- (Author, Year, p. xx) for direct quote
- Author (Year) found that... — narrative
- 2 authors: (Author & Author, Year)
- 3+ authors: (Author et al., Year)

### Chicago Author-Date
- (Author Year, page)
- เช่น (Smith 2020, 45)

### Chicago Notes-Bibliography
- ใช้ footnote/endnote
- First citation: full
- Subsequent: short form

```
First note: ¹John Smith, *Art and Society* (London: Routledge, 2020), 45.
Subsequent: ²Smith, *Art and Society*, 67.
```

### MLA 9
- (Author Page) — no comma, no year
- เช่น (Smith 45)

## Part 5: Special Considerations

### A. Citing AI-Generated Content

**APA 7** (when using AI as tool):
```
OpenAI. (2026). ChatGPT (GPT-4 Turbo) [Large language model]. 
https://openai.com
```

In-text: "ChatGPT generated the following code..." (OpenAI, 2026)

**Best practice for arts research**:
- Disclose AI assistance in dedicated section
- Don't cite AI as authoritative source
- Verify all factual claims independently

### B. Citing Translations

**APA 7**:
```
Author, A. A. (Year). Title (T. Translator, Trans.). Publisher. 
(Original work published Year)
```

### C. Multiple Works by Same Author

**APA 7**: เรียงตามปี (เก่า → ใหม่)
- 2020a, 2020b เมื่อปีเดียวกัน

**Chicago**: เรียงตามปีเช่นกัน

### D. Anonymous / Unknown Author

**Chicago**: ใช้ title แทน
**APA 7**: ใช้ "Anonymous" ถ้าระบุชัด หรือใช้ title

### E. Multiple Editions

ระบุ edition ใน citation:
```
Smith, J. Title of Book. 2nd ed. Publisher, Year.
```

ใช้ 1st edition เฉพาะถ้า historical importance

### F. Reprint

```
Original Author. (Year of original). Title. (Year of reprint Reprint ed.). 
Publisher.
```

## Part 6: Tools & Workflow

### Reference Managers

แนะนำ:

**Zotero** (ฟรี, รองรับภาษาไทย):
- Plugin Word + Google Docs
- Browser connector
- Group libraries สำหรับ collaboration
- Export ทุก format

**Mendeley** (ฟรี, ของ Elsevier):
- PDF annotation
- Cloud sync

**EndNote** (เสียเงิน, มหาวิทยาลัยมักให้):
- Powerful แต่ steep learning curve
- มาตรฐานที่หลาย publishers ใช้

**Citavi**: เน้น German-speaking academia แต่ใช้ได้ทั่วไป

### Workflow Tips

1. **เก็บ citation ทันที**ที่อ่าน — อย่ารอท้ายงาน
2. **ตรวจสอบทุก reference** ก่อนใช้ (verify existence!)
3. **เก็บ PDF** พร้อม citation
4. **Tag ด้วย keyword** สำหรับ retrieval
5. **Backup** library — cloud + local

## Part 7: Verification Checklist

ก่อน submit ใช้ checklist นี้:

- [ ] ทุก in-text citation มี matching entry ใน reference list
- [ ] ทุก reference list entry ถูก cited อย่างน้อย 1 ครั้งใน text
- [ ] รูปแบบสม่ำเสมอตลอด paper
- [ ] ชื่อผู้แต่ง spelling ถูก (ตรวจ vs original)
- [ ] ปี ตรงกับต้นฉบับ
- [ ] หมายเลขหน้าถูก (สำหรับ direct quotes)
- [ ] DOI หรือ URL ใช้งานได้จริง
- [ ] รูปภาพมี proper attribution + permission
- [ ] Archival sources มี complete identifier
- [ ] Translations ระบุผู้แปล
- [ ] Special characters (สระบาลี, อักษรพิเศษ) แสดงถูกต้อง

## Part 8: Common Errors

🚫 **Inconsistent style** — APA mixed with Chicago
🚫 **Missing page numbers** — สำหรับ direct quotes
🚫 **Wrong italics** — book titles italic, article titles in quotes (Chicago/MLA)
🚫 **Date format inconsistent** — เลือก Buddhist หรือ Common Era แล้วใช้ตลอด
🚫 **Missing translator** — จำเป็นเสมอ
🚫 **Generic image credit** — "Wikipedia" ไม่พอ — ระบุ original source
🚫 **Forgotten archival ID** — ไม่มี collection number → ตามไม่ได้
🚫 **AI-hallucinated DOIs** — ตรวจที่ doi.org/xxx ก่อนใช้

## Part 9: Sample Reference Lists

### APA 7 Sample

```
References

Apinan Poshyananda. (1992). Modern art in Thailand: Nineteenth and 
   twentieth centuries. Oxford University Press.

Borgdorff, H. (2012). The conflict of the faculties: Perspectives on 
   artistic research and academia. Leiden University Press.

McGill, F. (2005). The Kingdom of Siam: The art of central Thailand, 
   1350-1800. Asian Art Museum.

ศักดิ์ชัย สายสิงห์. (2564). ศิลปะอยุธยา: งานช่างหลวงแห่งแผ่นดิน. 
   อมรินทร์พริ้นติ้งแอนด์พับลิชชิ่ง.
```

### Chicago Author-Date Sample

```
References

Apinan Poshyananda. 1992. Modern Art in Thailand: Nineteenth and 
   Twentieth Centuries. Oxford: Oxford University Press.

Borgdorff, Henk. 2012. The Conflict of the Faculties: Perspectives on 
   Artistic Research and Academia. Leiden: Leiden University Press.

McGill, Forrest. 2005. The Kingdom of Siam: The Art of Central Thailand, 
   1350-1800. San Francisco: Asian Art Museum.

ศักดิ์ชัย สายสิงห์. 2564. *ศิลปะอยุธยา: งานช่างหลวงแห่งแผ่นดิน*. 
   กรุงเทพฯ: อมรินทร์พริ้นติ้งแอนด์พับลิชชิ่ง.
```

## Part 10: Quick Lookup Tables

### Italic vs Quotation Marks

| Source Type | Format |
|------------|--------|
| Book | *Italic* |
| Journal name | *Italic* |
| Article title | "Quotation marks" |
| Artwork title | *Italic* |
| Performance/Play title | *Italic* |
| Song title | "Quotation marks" |
| Album title | *Italic* |
| Film title | *Italic* |
| Exhibition title | *Italic* |
| Episode title | "Quotation marks" |
| Web page title | "Quotation marks" |
| Website name | *Italic* |

### When to Use sic, ibid., et al.

- **sic** (in [brackets sic]) — quote มี error ที่ original
- **ibid.** — same source as previous note (Chicago notes only — APA & Chicago Author-Date avoid)
- **et al.** — APA: 3+ authors first citation; Chicago: 4+ authors

## Workflow Integration

```
1. ขณะเขียน paper → จด reference เป็น draft 
   (รูปแบบไม่สมบูรณ์ก็ได้ แต่ครบ info)
2. ใช้ reference manager track ทุก source
3. ก่อน final draft → run citation through arts-citation-formatter:
   - ระบุ style ที่ต้องการ
   - ตรวจ source type
   - format ตาม template ที่ตรงกับสาขา
4. Verify checklist (Part 7)
5. ตรวจครั้งสุดท้ายโดย human eye
```

## References

**Citation Manuals**:
- *Publication Manual of the American Psychological Association*. 7th ed. APA, 2020.
- *The Chicago Manual of Style*. 17th ed. University of Chicago Press, 2017.
- *MLA Handbook*. 9th ed. Modern Language Association, 2021.
- *AAA Style Guide* (American Anthropological Association)
- *SAA Style Guide* (Society for American Archaeology)

**Online**:
- Purdue OWL: https://owl.purdue.edu/
- Citation Style Language: citationstyles.org
- Zotero Style Repository: zotero.org/styles

**Thai standards**:
- TCI Guidelines: https://tci-thaijo.org/
- คู่มือการเขียนวิทยานิพนธ์ บัณฑิตวิทยาลัย ม.เชียงใหม่

ดู `references/` สำหรับ extended templates และ examples
