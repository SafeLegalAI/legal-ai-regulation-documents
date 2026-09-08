---
license: cc-by-4.0
pretty_name: "SafeLegalAI Legal AI Regulation Documents (versioned)"
language:
  - en
multilinguality:
  - monolingual
annotations_creators:
  - expert-generated
language_creators:
  - found
source_datasets:
  - original
size_categories:
  - n<1K
tags:
  - legal
  - law
  - regulation
  - court-rules
  - standing-orders
  - ethics-opinions
  - practice-directions
  - ai-governance
  - generative-ai
  - courts
  - ai-regulation
  - ai-safety
  - safelegalai
configs:
  - config_name: documents
    default: true
    data_files:
      - split: train
        path: data/documents.jsonl
  - config_name: versions
    data_files:
      - split: train
        path: data/versions.jsonl
---

# SafeLegalAI Legal AI Regulation Documents (versioned)

**Which official texts govern AI in legal practice, what do they require, and how have they changed?**

515 documents · 560 versions tracked · 17 jurisdictions · last checked 2026-09-06 · synced from [safelegalai.com](https://safelegalai.com) on 2026-09-08.

Every court rule, practice direction, standing order, ethics opinion, statute, regulation, policy, consultation and guidance document on AI in legal practice that we have verified — one row per document, with who issued it, whom it binds, what it requires, its effective date, and every revision as a version entry with a change note. This is the granular layer beneath the country map.

This is a mirror. The canonical, always-current version lives at **[safelegalai.com/regulation/documents](https://safelegalai.com/regulation/documents)**, where every record has a permanent page, a citation block and its last-checked date; the JSON served there ([/regulation/documents.json](https://safelegalai.com/regulation/documents.json)) is the source of this repository. Each row's `url` field points to its record page. The same files are mirrored on GitHub at [github.com/SafeLegalAI/legal-ai-regulation-documents](https://github.com/SafeLegalAI/legal-ai-regulation-documents) (issues welcome there).

## Tables

| config | rows | what a row is | files |
|---|---|---|---|
| `documents` | 515 | one row per official document, version history nested | [`data/documents.jsonl`](data/documents.jsonl) · [`csv/documents.csv`](csv/documents.csv) |
| `versions` | 560 | long format — one row per document version with its date, source URL, archive URL and change note | [`data/versions.jsonl`](data/versions.jsonl) · [`csv/versions.csv`](csv/versions.csv) |

## Fields

| field | meaning |
|---|---|
| `title` · `body` · `bodyShort` · `jurisdiction` · `region` · `country` | the issuing body and where it applies |
| `type` | guidance · practice-direction · court-rule · standing-order · ethics-opinion · statute · regulation · policy · consultation · report · judgment-guidance |
| `status` | in-force · proposed · consultation · superseded · withdrawn |
| `appliesTo` | lawyers · barristers · judges · court-staff · litigants · parties · providers · firms · all |
| `requirements` | disclosure · certification · verification · prohibition · confidentiality · competence · supervision · record-keeping · consent · permissive · risk-classification |
| `categories` | taxonomy ids shared with the regulation map |
| `versions` | `[{version, date, url, archiveUrl, changes}]`, newest first |
| `summary` · `keyProvisions` | what the document requires, in 40–60 words and 3–7 statements |
| `relatedIncidents` · `article` | slugs into the incident dataset and the analysis article |
| `sources` · `lastVerified` · `verified` | provenance and check date |

Dates are `YYYY-MM-DD`. Optional fields are absent (JSONL) or empty (CSV) when unknown — nothing is guessed. In the CSV, arrays of scalars are joined with `; ` and nested objects are JSON strings.

## Method

We record findings made by courts and regulators; we do not make them. Every record links a primary source (judgment, order, regulator notice, official document or vendor page) and carries the date it was last re-opened against that source. Unverified records are flagged `unverified`, never silently included. Inclusion criteria, the correction process and the ownership/funding disclosure are published at [safelegalai.com/editorial-standards](https://safelegalai.com/editorial-standards); every content run is logged at [safelegalai.com/changelog](https://safelegalai.com/changelog).

## Use

```python
from datasets import load_dataset
ds = load_dataset("safelegalaidata/legal-ai-regulation-documents", "documents")
```

## Uses

**Suited to:** counting and comparing what the record shows (by court, jurisdiction, date, actor, outcome, status); building watch-lists and alerts from the `url` and last-checked fields; grounding retrieval or summarisation on cited primary documents; teaching and library guides that need a dated, sourced list.

**Not suited to:** ranking products, people or courts; inferring prevalence beyond what a court or regulator has itself stated; any use that treats a coding column as a finding of fact or law. Where a row names a person or organisation it does so as they appear in a public document; anyone named may request a correction or right of reply at https://safelegalai.com/report.

## Cite

> SafeLegalAI (published by Cognesio LLP), "Legal AI Regulation Documents (versioned)", safelegalai.com, accessed 2026-09-08. https://safelegalai.com/regulation/documents — data: CC BY 4.0.

```bibtex
@dataset{safelegalai_legal_ai_regulation_documents_2026_09_08,
  title        = {Legal AI Regulation Documents (versioned)},
  author       = {{SafeLegalAI (Cognesio LLP)}},
  year         = {2026},
  url          = {https://safelegalai.com/regulation/documents},
  note         = {Mirror: https://huggingface.co/datasets/safelegalaidata/legal-ai-regulation-documents. Data CC BY 4.0. Last checked 2026-09-06.}
}
```

Cite the primary source as the authority and this dataset as the structured record that surfaced it. Corrections and right of reply: [safelegalai.com/report](https://safelegalai.com/report).

## Licence

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Attribution: **SafeLegalAI (safelegalai.com), published by Cognesio LLP** with a link to https://safelegalai.com/regulation/documents. Primary sources keep their own licences and copyright.

## Disclaimer and notices

**Provided "as is", without warranty of any kind** — the CC BY 4.0 licence excludes all warranties and limits liability (section 5), and those exclusions apply to this dataset. **Not legal advice**; no lawyer–client relationship arises from using it. Cognesio LLP is not a law firm. SafeLegalAI records findings made by courts, regulators and vendors' own published pages; it makes no findings of its own, and the linked official documents are the record. Editorial classifications (status labels, requirement codes, "documented yes/no/not disclosed") are opinions about documents, expressed in good faith; the document prevails. Where a row names a person or organisation, it does so as they appear in a public court document, official publication or their own published material — a fair and accurate report published in good faith and in the public interest; anyone named may reply or request a correction at https://safelegalai.com/report. Product, company, court and regulator names and marks belong to their owners and identify the product or body referred to; no affiliation or endorsement is implied. Full terms, notice-and-takedown and governing law (England and Wales): https://safelegalai.com/disclaimer.

## Related datasets

- [Legal AI Incident Tracker](https://huggingface.co/datasets/safelegalaidata/legal-ai-incidents) — canonical page https://safelegalai.com/tracker
- [Legal AI Regulation Map](https://huggingface.co/datasets/safelegalaidata/legal-ai-regulation-map) — canonical page https://safelegalai.com/regulation
- [Legal Tech Tools — governance facts](https://huggingface.co/datasets/safelegalaidata/legal-ai-tools) — canonical page https://safelegalai.com/tools
- [All datasets and what is in preparation](https://safelegalai.com/datasets)

## Manifest

```json
{
  "dataset": "SafeLegalAI Legal AI Regulation Documents (versioned)",
  "canonical": "https://safelegalai.com/regulation/documents",
  "source": "https://safelegalai.com/regulation/documents.json",
  "catalogue": "https://safelegalai.com/datasets",
  "publisher": "Cognesio LLP",
  "license": "CC BY 4.0",
  "licenseUrl": "https://creativecommons.org/licenses/by/4.0/",
  "lastChecked": "2026-09-06",
  "synced": "2026-09-08",
  "notice": "Provided as is, without warranty; not legal advice. SafeLegalAI records findings made by courts, regulators and vendors' own pages; the linked official documents are the record. Names and marks belong to their owners. Terms: https://safelegalai.com/disclaimer",
  "tables": {
    "documents": 515,
    "versions": 560
  },
  "contentSha256": "b0c2ea5ed709fbf322046e05fbd51d68b0c760fc5ac5487b999403de7ae7432b"
}
```
