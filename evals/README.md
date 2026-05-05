---
title: "CAMT Arts Research Skills — Evaluation Suite v2.0"
description: "Test suite for all 7 skills in camt-arts-research-skills. Covers trigger accuracy, output quality, failure path coverage, and pipeline flow."
version: 1.0.0
updated: 2026-05-05
skills_tested:
  - arts-research-pipeline
  - arts-deep-research
  - arts-paper-writer
  - arts-paper-reviewer
  - arts-citation-formatter
  - practice-based-research
  - visual-analysis
---

# CAMT Arts Research Skills — Evaluation Suite v2.0

## โครงสร้าง

```
evals/
├── README.md                        ← ไฟล์นี้
├── trigger_accuracy/
│   ├── positive_cases.md            ← prompts ที่ควร trigger แต่ละ skill
│   ├── negative_cases.md            ← prompts ที่ไม่ควร trigger (false positive test)
│   └── edge_cases.md                ← กรณีกำกวม — skill เดียวหรือหลาย skill?
├── output_quality/
│   ├── iron_rules_checklist.md      ← ตรวจว่า Iron Rules ทุกข้อถูกใช้
│   ├── tci_compliance_cases.md      ← ตรวจ TCI format ครบ 7 requirements
│   └── bilingual_abstract_cases.md  ← ตรวจ alignment ของ Thai/English abstract
├── failure_paths/
│   ├── fm_detection_cases.md        ← ตรวจว่า FM-A ถึง FM-G ถูก detect
│   └── recovery_protocol_cases.md   ← ตรวจ recovery workflow ถูกต้อง
└── pipeline_flow/
    ├── handoff_schema_cases.md      ← ตรวจ inter-skill data transfer
    └── state_machine_cases.md       ← ตรวจ State Machine transitions
```

## วิธีใช้ Eval Suite

### Manual Eval (แนะนำสำหรับ v1)
1. เปิดไฟล์ test cases ในโฟลเดอร์ที่ต้องการ
2. คัดลอก **Input Prompt** ส่งให้ Claude
3. เทียบผลลัพธ์กับ **Expected Behavior** และ **Assertion Criteria**
4. บันทึก PASS / FAIL / PARTIAL ใน **Results Log** ท้ายไฟล์

### Automated Eval (ใช้ skill-creator)
```
/skill-creator run-eval --suite evals/ --skill arts-paper-writer
```

## Scoring

| Grade | เกณฑ์ |
|-------|--------|
| ✅ PASS | ตรงตาม assertion ทุกข้อ |
| ⚠️ PARTIAL | ตรง 70–99% ของ assertions |
| ❌ FAIL | ตรงต่ำกว่า 70% หรือละเมิด Iron Rule ใดๆ |

> ⚠️ หาก Iron Rule ถูกละเมิดแม้เพียงข้อเดียว → FAIL ทันที ไม่ว่า assertion อื่นจะผ่านหรือไม่

## ผลลัพธ์ที่คาดหวัง (Baseline)
- Trigger accuracy: ≥ 90% precision, ≥ 85% recall
- Output quality: ≥ 90% Iron Rules compliance per run
- Failure path detection: ≥ 85% FM detection rate
- Pipeline flow: 100% handoff schema completeness
