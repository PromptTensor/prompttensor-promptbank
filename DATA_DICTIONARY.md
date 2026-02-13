# DATA_DICTIONARY — PromptTensor Prompt Bank (v1.0.0)

This data dictionary describes the public release files:
- `prompts_public.jsonl` (canonical, JSONL)
- `prompts.csv` (flattened)
- `prompts.parquet` (analytics-friendly)

## Conventions
- **Language:** English only (`language = "en"`).
- **Placeholders:** Some prompts include the literal placeholder `<TEXT>` for tasks that require an input passage (e.g., rewrite/summarization/translation). The placeholder is part of the prompt text.
- **Per-row timestamps:** intentionally omitted. See dataset-level metadata: `generation_window_start` / `generation_window_end` in README/manifest.

---

## Fields (per prompt)

### `prompt_id`
- **Type:** string
- **Required:** yes
- **Example:** `P005128`
- **Description:** Global unique identifier for the prompt. Stable within this dataset version.

### `prompt_text`
- **Type:** string
- **Required:** yes
- **Example:** `Rewrite the following text: <TEXT>. ...`
- **Description:** The prompt text with normalized whitespace. May include `<TEXT>` placeholder for self-contained tasks.

### `language`
- **Type:** string
- **Required:** yes
- **Allowed values:** `en`
- **Example:** `en`
- **Description:** Prompt language (public release is English-only).

### `domain`
- **Type:** string
- **Required:** yes
- **Example:** `academic_research`
- **Description:** Top-level category. Values are listed in `taxonomy.yaml`.

### `subdomain`
- **Type:** string
- **Required:** yes
- **Example:** `citation_summaries`
- **Description:** Subcategory within a domain. Values are listed in `taxonomy.yaml`.

### `intent`
- **Type:** string
- **Required:** yes
- **Allowed values:** `generation`, `summarization`, `translation`, `rewrite_paraphrase`, `planning`, `critique_review`
- **Example:** `critique_review`
- **Description:** Task intent.

### `difficulty`
- **Type:** string
- **Required:** yes
- **Allowed values:** `easy`, `intermediate`, `medium`, `hard`, `advanced`
- **Example:** `hard`
- **Description:** Estimated difficulty label (heuristic / curation-based).

### `output_style`
- **Type:** string
- **Required:** yes
- **Allowed values (common):** `essay`, `bullet_list`, `email`, `table`, `dialogue`, `step_by_step`, `report`, `memo`
- **Example:** `memo`
- **Description:** Expected output format requested by the prompt.

### `length_target`
- **Type:** string
- **Required:** yes
- **Allowed values:** `short`, `medium`, `long`
- **Example:** `medium`
- **Description:** Target response length class.

### `constraints`
- **Type:** list[string]
- **Required:** yes (may be empty list)
- **Example:** `["under 350 words", "use headings", "avoid jargon"]`
- **Description:** Explicit constraints intended to control the output.

**CSV note:** in `prompts.csv`, `constraints` is stored as a JSON-encoded string (so it can round-trip back to a list).

### `license`
- **Type:** string
- **Required:** yes
- **Allowed values:** `CC-BY-4.0`
- **Example:** `CC-BY-4.0`
- **Description:** Public release license for each row.

### `batch_id`
- **Type:** string
- **Required:** yes
- **Example:** `run_0051`
- **Description:** Internal run identifier extracted from internal IDs. Useful for analysis/reproducibility (not personal/provenance data).

---

## Supporting files

### `taxonomy.yaml`
- Defines the allowed values for `domain`, `subdomain`, and `intent` for this release.

### `splits.csv`
- Contains prompt-disjoint train/dev/test assignment.
- **Columns:** `prompt_id`, `split`, `split_rule`
