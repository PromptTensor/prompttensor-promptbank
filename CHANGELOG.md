# CHANGELOG — PromptTensor Prompt Bank

All notable changes to this dataset will be documented in this file.

The format is inspired by Keep a Changelog, but adapted for datasets.

---

## v1.0.1 — 2026-02-16
### Added
- Initial public release of **PromptTensor Prompt Bank** with **7,040** English prompts.
- Labels: `domain`, `subdomain`, `intent`, plus structured `constraints`.
- Output files: `prompts_public.jsonl`, `prompts.csv`, `prompts.parquet`, `taxonomy.yaml`, `splits.csv`

### Data hygiene
- Removed prompts requesting personal data / secrets (PII/secrets).
- Removed prompts that appear to request illegal or harmful step-by-step instructions.
- Performed exact + near-duplicate removal (best-effort).

### Notes
- Per-row timestamps (`collected_at`) are intentionally omitted in the public release.
- Dataset-level generation window: **2025-08-11 → 2026-02-04**.
