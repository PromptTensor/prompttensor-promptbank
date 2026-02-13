# PromptTensor Prompt Bank (v1.0.0)

A high-quality **English prompt bank** for LLM research and prompt-engineering experiments.  
Each prompt is labeled by **domain / subdomain / intent** and includes structured constraints for controllable outputs.

- **Publisher/Organization:** PromptTensor  
- **License:** CC-BY-4.0  
- **Language:** English (`en`)  
- **Size:** 7,040 prompts (after filtering + dedup)  
- **Generation window (dataset-level):** 2025-08-11 → 2026-02-04  
- **Primary release platform:** Hugging Face  

## TL;DR
This dataset contains **user prompts only** (not model outputs). It is designed for:
- Prompt analysis and benchmarking
- Studying instruction patterns across domains and intents
- Tooling (dedup, classification, constraint extraction, etc.)

## How the prompts were created
This dataset was created by **PromptTensor** and curated through a combination of:
- PromptTensor in-house tooling (e.g., Prompt Architect, AI Prompt Refiner)
- LLM-assisted ideation and controlled variation
- **PromptTensor team expertise and manual review**, including taxonomy alignment (domain/subdomain/intent) and constraint design to ensure consistency and research usability.


## What’s inside
- Multiple domains (e.g., academic_research, education, marketing, science_tech, product_reviews, customer_support, etc.)
- Intents:
  - `generation`
  - `summarization`
  - `translation`
  - `rewrite_paraphrase`
  - `planning`
  - `critique_review`
- Formats: JSONL, CSV, Parquet
- Supporting files: `taxonomy.yaml` + prompt-disjoint `splits.csv`

## Data files
- `prompts_public.jsonl` — main release file (1 JSON object per line)
- `prompts.csv` — flattened table view (constraints stored as JSON string)
- `prompts.parquet` — analytics-friendly format
- `taxonomy.yaml` — domains/subdomains/intents observed in this release
- `splits.csv` — train/dev/test split (prompt-disjoint)

## Schema (prompts_public.*)
Each row contains:

| Field | Type | Description |
|------|------|-------------|
| `prompt_id` | string | Global unique prompt identifier (e.g., `P005128`) |
| `prompt_text` | string | The prompt text (normalized whitespace). May include `<TEXT>` placeholder for rewrite/summarization/translation tasks |
| `language` | string | Always `en` |
| `domain` | string | Top-level category (e.g., `academic_research`) |
| `subdomain` | string | Subcategory (e.g., `citation_summaries`) |
| `intent` | string | Task intent (e.g., `critique_review`) |
| `difficulty` | string | 	Estimated difficulty from easy, intermediate, medium, hard, advanced |
| `output_style` | string | Expected response format (e.g., `memo`, `bullet_list`, `report`) |
| `length_target` | string | `short` / `medium` / `long` |
| `constraints` | list[string] | Explicit constraints to guide the output |
| `license` | string | Always `CC-BY-4.0` for this public release |
| `batch_id` | string | Run identifier extracted from internal IDs (e.g., `run_0051`) |

> Note: Per-row timestamps are intentionally omitted. Only a dataset-level generation window is provided.

## Train/dev/test splits
File: `splits.csv`

- Split rule: **prompt-disjoint** (`prompt_id` appears in only one split)
- Recommended default ratios: 80/10/10 (train/dev/test)
- Deterministic with a fixed seed

## Data quality & safety
The public release is filtered to remove:
- Prompts requesting personal data or secrets (PII/secrets)
- Prompts that look like requests for illegal or harmful step-by-step instructions
- Exact duplicates + near-duplicates (within domain/subdomain/intent)

Dedup includes:
- Exact duplicates: normalized text hashing
- Near-duplicates: token overlap + normalized similarity thresholds

## Intended use
- Research on prompt structures and controllable prompting
- Benchmarking prompt analytics tools
- Studying instruction diversity across domains

## Not intended for
- Collecting personal data or secrets
- Generating illegal instructions or harmful content

## Limitations
- Prompts were created with PromptTensor tooling and team expertise + LLM assistance, which may introduce stylistic bias.
- Coverage is broad but not exhaustive across all real-world tasks.
- Some prompts may remain semantically similar despite best-effort dedup.

## License
This dataset is released under **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Creative Commons Attribution 4.0 International (CC BY 4.0)

This dataset is licensed under the Creative Commons Attribution 4.0 International License.
You are free to share and adapt the material for any purpose, even commercially, under the
condition that you give appropriate credit, provide a link to the license, and indicate if changes were made.

License: https://creativecommons.org/licenses/by/4.0/

Attribution (Required):
If you use this dataset, please cite:
“PromptTensor Prompt Bank V1” — PromptTensor (2026). Licensed under CC BY 4.0. Source: https://prompttensor.com/datasets/prompttensor-promptbank-v1


## Citation
If you use this dataset, please cite:

> PromptTensor. PromptTensor Prompt Bank. v1.0.0, 2026. Canonical dataset page: https://prompttensor.com/datasets/prompttensor-promptbank-v1

BibTeX:
```bibtex
@dataset{prompttensor_promptbank_v1,
  title   = "PromptTensor Prompt Bank",
  author  = "PromptTensor",
  year    = "2026",
  version = "1.0.0",
  url     = "https://prompttensor.com/datasets/prompttensor-promptbank-v1",
  license = "CC-BY-4.0"
}
```

## Contact
For questions, feedback, or issue reporting: **datasets@prompttensor.com**
