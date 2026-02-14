# PromptTensor Prompt Bank (v1.0.0)

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.18642964.svg)](https://doi.org/10.5281/zenodo.18642964)

A high-quality **English prompt bank** for LLM research and prompt-engineering experiments.  
Each prompt is labeled by **domain / subdomain / intent** and includes structured constraints for controllable outputs.

- **Publisher/Organization:** PromptTensor  
- **License:** CC-BY-4.0  
- **Language:** English (`en`)  
- **Size:** 7,040 prompts (after filtering + dedup)  
- **Generation window (dataset-level):** 2025-08-11 → 2026-02-04  
- **Primary release platform:** Hugging Face  

## Links
- **Hugging Face (primary):** https://huggingface.co/datasets/PromptTensor/prompttensor-promptbank
- **Canonical page (recommended backlink):** https://prompttensor.com/datasets/prompttensor-promptbank-v1
- **Zenodo (all versions / concept DOI):** https://doi.org/10.5281/zenodo.18642963
- **Zenodo (v1.0.0 / version DOI):** https://doi.org/10.5281/zenodo.18642964

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
- Intents: `generation`, `summarization`, `translation`, `rewrite_paraphrase`, `planning`, `critique_review`
- Formats: JSONL, Parquet (optional CSV)
- Supporting file: `taxonomy.yaml`

## Data files
- `data/prompts_public.jsonl` — main release file (1 JSON object per line)
- `data/prompts.parquet` — analytics-friendly format
- `data/prompts.csv` — optional flattened table view (constraints stored as JSON string)
- `data/taxonomy.yaml` — domains/subdomains/intents observed in this release

## Schema (prompts_public.*)
Each row contains:

| Field | Type | Description |
|------|------|-------------|
| `prompt_id` | string | Global unique prompt identifier (e.g., `P005128`) |
| `prompt_text` | string | Normalized prompt text. May include `<TEXT>` placeholder for rewrite/summarization/translation tasks |
| `language` | string | Always `en` |
| `domain` | string | Top-level category (e.g., `academic_research`) |
| `subdomain` | string | Subcategory (e.g., `citation_summaries`) |
| `intent` | string | Task intent (e.g., `critique_review`) |
| `difficulty` | string | Estimated difficulty: `easy`, `intermediate`, `medium`, `hard`, `advanced` |
| `output_style` | string | Expected response format (e.g., `memo`, `bullet_list`, `report`) |
| `length_target` | string | `short` / `medium` / `long` |
| `constraints` | list[string] | Explicit constraints to guide the output |
| `license` | string | Always `CC-BY-4.0` for this public release |
| `batch_id` | string | Run identifier extracted from internal IDs (e.g., `run_0051`) |

> Note: Per-row timestamps are intentionally omitted. Only a dataset-level generation window is provided.

## Data quality & safety
The public release is filtered to remove:
- Prompts requesting personal data or secrets (PII/secrets)
- Prompts that look like requests for illegal or harmful step-by-step instructions
- Exact duplicates + near-duplicates (within domain/subdomain/intent)

## License
This dataset is released under **Creative Commons Attribution 4.0 International (CC BY 4.0)**.  
License text and link: https://creativecommons.org/licenses/by/4.0/

## Citation
**Recommended (cite v1.0.0 / version DOI):** https://doi.org/10.5281/zenodo.18642964  
**All versions (concept DOI):** https://doi.org/10.5281/zenodo.18642963  
**Canonical page:** https://prompttensor.com/datasets/prompttensor-promptbank-v1

Suggested citation (v1.0.0):
> PromptTensor. *PromptTensor Prompt Bank* (v1.0.0). 2026. DOI: 10.5281/zenodo.18642964. Canonical page: https://prompttensor.com/datasets/prompttensor-promptbank-v1

BibTeX (v1.0.0 / version DOI):
```bibtex
@dataset{prompttensor_promptbank_v1_0_0,
  title   = {PromptTensor Prompt Bank},
  author  = {PromptTensor},
  year    = {2026},
  version = {1.0.0},
  doi     = {10.5281/zenodo.18642964},
  url     = {https://prompttensor.com/datasets/prompttensor-promptbank-v1},
  license = {CC-BY-4.0}
}
```

BibTeX (all versions / concept DOI):
```bibtex
@dataset{prompttensor_promptbank_concept,
  title   = {PromptTensor Prompt Bank},
  author  = {PromptTensor},
  year    = {2026},
  doi     = {10.5281/zenodo.18642963},
  url     = {https://prompttensor.com/datasets/prompttensor-promptbank-v1},
  license = {CC-BY-4.0}
}
```

## Contact
For questions, feedback, or issue reporting: **datasets@prompttensor.com**
