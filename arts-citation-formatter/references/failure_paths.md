---
name: failure_paths
purpose: 8 failure scenarios ใน arts-citation-formatter + recovery strategies
parent_skill: arts-citation-formatter
version: 1.0.0
---

# Failure Paths — Arts Citation Formatter

| # | ชื่อ | Trigger | ผลกระทบ | Recovery |
|---|-----|---------|---------|---------|
| F1 | Source Type Unknown | ไม่แน่ใจว่า source เป็น journal article, book chapter, หรือ edited volume | format ผิด | ถาม 3 คำถาม: มี editor ไหม? เป็นส่วนหนึ่งของหนังสือที่ใหญ่กว่าไหม? มี DOI ของ journal ไหม? |
| F2 | Incomplete Bibliographic Info | ขาด author, year, page, publisher หรือ DOI | citation ไม่สมบูรณ์ | ระบุสิ่งที่ขาด → แนะนำวิธีหา → ใช้ placeholder ถ้าจำเป็น |
| F3 | AI-Generated Reference | reference ที่ไม่ exist จริง | academic misconduct | ตรวจทุก reference ด้วย database จริงก่อน format |
| F4 | Non-Standard Arts Sources | exhibition catalog, artist statement, oral interview, performance | ไม่มีใน standard guide | ใช้ arts-specific citation template |
| F5 | Thai-Language Source | ชื่อภาษาไทย, publisher ไทย, วารสาร TCI | transliteration ผิด / format ผิด | ใช้ TCI citation standard + romanization ที่สอดคล้อง |
| F6 | Mixed Format in One Document | references ผสม APA + Chicago + MLA | ไม่ consistent | เลือก style เดียว → convert ทั้งหมดใหม่ |
| F7 | Website / Social Media | URL เปลี่ยน / ไม่มีวันที่ / ไม่มีผู้แต่ง | citation ไม่น่าเชื่อถือ | ใช้ Wayback Machine URL + access date + note instability |
| F8 | Multiple Editions / Translations | ไม่แน่ใจว่าใช้ edition ไหน, แปลจากภาษาอะไร | citation อาจ mislead | ระบุ edition + translator + original publication info |

---

## Detailed Recovery: F4 — Non-Standard Arts Sources

### Exhibition Catalog
```
APA 7:
Editor(s) (Ed(s).). (Year). Title of catalog. Publisher.

หรือ chapter ใน catalog:
Author. (Year). Title of essay. In Editor (Ed.), Title of catalog (pp. xx-xx). Publisher.

Chicago 17 (notes):
Author, "Essay Title," in Catalog Title, ed. Editor Name (City: Publisher, Year), pages.
```

### Artist Statement (Published)
```
APA 7:
Artist, A. (Year). Title of statement [Artist statement]. Publisher/Journal.

Chicago 17:
Artist Name. "Title of Statement." Artist statement. Publication details.
```

### Artist Statement (Unpublished / Website)
```
APA 7:
Artist, A. (Year, Month Day). Title of statement [Artist statement]. Retrieved from URL

Note: ระบุ "Artist statement" ใน brackets เสมอ
```

### Performance / Live Event
```
APA 7:
Choreographer/Director, A. (Year, Month Day). Title of work [Performance]. Venue, City.

Chicago 17:
Choreographer/Director Name. Title of Work. Performance. Venue, City, Date.
```

### Oral Interview / Oral History
```
APA 7:
Interviewee, A. (Year, Month Day). [Interview by B. Interviewer] [Interview transcript/recording]. 
Repository if archived, or "Personal collection of B. Interviewer."

Note: ถ้าเป็น conducted โดยผู้วิจัยเอง:
Name of person interviewed. Interview by [your name]. [Location or medium]. Date.
```

### Archival Material
```
APA 7:
Author (if known). (Date). Title of document [Type of document]. Collection Name, Archive Name, Location.

Chicago 17:
Author (if known), "Document Title," Date, Collection Name, Box/Folder, Archive Name, Location.
```

---

## Detailed Recovery: F5 — Thai-Language Source (TCI Format)

### วารสารภาษาไทย (TCI)
```
รูปแบบ TCI:
ชื่อผู้แต่ง. (ปี). ชื่อบทความ. ชื่อวารสาร, ปีที่(ฉบับที่), หน้า.

ตัวอย่าง:
สมชาย ใจดี. (2566). การวิเคราะห์ลวดลายผ้าซิ่นล้านนา. วารสารวิจิตรศิลป์, 14(2), 45-67.

ถ้าต้องการใน APA ภาษาอังกฤษ (romanize):
Jaidi, S. [สมชาย ใจดี]. (2023). [Analysis of Lanna textile patterns] 
[การวิเคราะห์ลวดลายผ้าซิ่นล้านนา]. Wichit Silp Journal [วารสารวิจิตรศิลป์], 14(2), 45-67.
```

### หนังสือภาษาไทย
```
TCI:
ผู้แต่ง. (ปี). ชื่อหนังสือ (ครั้งที่พิมพ์ ถ้าไม่ใช่ครั้งแรก). สำนักพิมพ์.

APA (romanized):
Author (Thai name romanized) [Thai name]. (Year). [English translation of title] [Thai title] 
(Xth ed.). Publisher (Thai name romanized) [Thai publisher name].
```

### Romanization ภาษาไทย
ใช้ระบบ: **Royal Thai General System of Transcription (RTGST)** 
แหล่งอ้างอิง: http://www.royin.go.th/th/romanization/

ข้อยกเว้น: ชื่อที่มีการสะกดแบบที่เจ้าของชื่อใช้เอง (เช่น Chiang Mai ไม่ใช่ Chiang Mhai)
