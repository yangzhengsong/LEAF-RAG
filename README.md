# LEAF-RAG — Public Knowledge Base Sample

This repository releases a **public-source sample** of the knowledge base used in the
**LEAF-RAG** framework (submitted to *Computers and Electronics in Agriculture*).

LEAF-RAG is a retrieval-augmented generation (RAG) framework for **rice fertilization
question answering**, combining hierarchical evidence ranking with explicit
weather-conflict gating. This repository contains a representative subset drawn from
**publicly accessible knowledge sources**, to support reproducibility and review.

## Data Sources

The sample in `data/` is drawn from the public knowledge sources that feed the LEAF-RAG
knowledge base, matching the sources described in the manuscript:

| Source class | Organisation | Entries |
|--------------|--------------|---------|
| `reference_knowledge_bank` | International Rice Research Institute (IRRI) | 39 |
| `technical_bulletin` | China's Ministry of Agriculture and Rural Affairs and local agricultural authorities | 9 |
| `extension_manual` | China's Ministry of Agriculture and Rural Affairs | 2 |

Total: **50 public-source entries**. Each entry retains its original public URL
(`source_url`) so the source material can be verified independently.

## Data Format

`data/public_sources_admitted.jsonl` is [JSON Lines](https://jsonlines.org/) (one JSON
object per line). The schema is:

```jsonc
{
  "document_id": "PUB-xxxxxxxx",          // unique document identifier
  "title": "document title",
  "organization": "issuing organisation",  // e.g. Ministry of Agriculture...
  "source_class": "extension_manual",      // reference_knowledge_bank / technical_bulletin / extension_manual
  "region": "region tag",                  // e.g. 中国分区
  "publication_date": "2023-03-20",
  "source_url": "https://...",             // original public source URL
  "source_locator": "web page",
  "retrieved_at": "ISO 8601 timestamp",
  "content_sha256": "hash",
  "character_count": 8173,
  "quality_score": 100,
  "topics": ["fertilization", "water", ...],
  "content": "document body text",         // cleaned knowledge text
  "review_status": "unreviewed",
  "usage_boundary": "usage note"
}
```

## License

The sample data originates from third-party public sources (IRRI Rice Knowledge Bank and
public guidance issued by China's Ministry of Agriculture and Rural Affairs and local
agricultural authorities). Please refer to each source's own terms for any reuse of the
original content.

The data files are provided here solely for **research reproduction and review**
purposes. The LEAF-RAG code and the full experimental dataset are **not** included in
this repository.
