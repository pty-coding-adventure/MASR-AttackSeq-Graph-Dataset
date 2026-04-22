## MASR AttackSeq-Graph Dataset (v0.2)

This repository releases an open-source dataset of annotated multimodal jailbreak attack sequences with graph representations.

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
