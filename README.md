## MASR AttackSeq-Graph Dataset v0.2 release (V0, ungated baseline)
This repository releases an open-source dataset of annotated multimodal jailbreak attack sequences with graph representations.

## Dataset versions and thesis usage

- V0 (this release, legacy/ungated, ≥500 sequences): released as the open-source benchmark dataset for the project deliverable.
  It aggregates multiple runs; therefore, the `model` field may contain mixed naming variants (e.g., GPT4o and GPT4o-mini),
  and some samples may exhibit cross-scenario template leakage.

- V1-clean (quality-gated subset): used for thesis main results to reduce cross-scenario leakage and improve evaluation reliability.
  Main thesis conclusions are reported on V1-clean with bootstrap confidence intervals, using ASR(M1) as the primary metric and
  ISR@0.7 as a complementary induction metric. V1-clean is not included in this public release (available in supporting documents / upon request).
  
### Contents (in the release .zip)
- `sequences.jsonl`: one sample per line (JSON).
- `manifest.csv`: sample index and basic statistics.
- `images/`: one image per sample.

### Schema (core fields)
Each JSONL record includes:
- `schema_version`, `sample_id`, `timestamp`, `method`, `model`, `scenario`
- `attack_graph`: list of turns (`turn_id`, `state`, and optional attributes such as `thought`, `text_query`, `response`, `actual_toxicity`, `judge_reason`, `is_jailbroken`, `grounding`, `sd_prompt`, ...)
- `image_relpath`, `image_sha256` (if provided)
- `extra` (optional forward-compatible fields)

### Graph representation
Directed sequential chain over turns: nodes are turns; edges are `(t -> t+1)`.

### Download
Download `MASR-AttackSeq-Graph-Dataset_v0.2.zip` from GitHub Releases.

### Integrity check
```bash
sha256sum -c MASR-AttackSeq-Graph-Dataset_v0.2.zip.sha256
