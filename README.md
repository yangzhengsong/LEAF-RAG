# LEAF-RAG — Public Knowledge Base Sample

This repository releases a **public-source sample** of the knowledge base used in the
**LEAF-RAG** framework (submitted to *Computers and Electronics in Agriculture*).

LEAF-RAG is a retrieval-augmented generation (RAG) framework for **rice agronomy
question answering**, combining hierarchical evidence ranking with explicit
weather-conflict gating. The full experimental dataset and model artifacts are not
publicly released; this repository contains only a representative subset drawn from
**publicly accessible sources** to support reproducibility and review.

## Data Sources

All entries in `data/` are derived from **public, open-access knowledge sources**:

| File | Source | Entries |
|------|--------|---------|
| `data/irri_knowledge.jsonl` | IRRI Rice Knowledge Bank (http://www.knowledgebank.irri.org) | 206 |
| `data/rice_fertilization_cleaned.jsonl` | CGSpace / CGIAR open repository (https://cgspace.cgiar.org) | 104 |
| `data/cgspace_bulk_data.jsonl` | CGSpace / CGIAR open repository (https://cgspace.cgiar.org) | 152 |

Each entry retains its original public URL so that the source material can be verified
independently.

## Data Format

Every file is [JSON Lines](https://jsonlines.org/) (one JSON object per line).
The schema is:

```jsonc
{
  "id": "unique identifier",          // e.g. "irri_96874fee"
  "entity_name": "short title",       // entity / topic label
  "content": {
    "title": "document title",
    "text": "document body text"      // cleaned knowledge text
  },
  "url": "https://...",               // original public source URL
  // optional fields present in some sources:
  "category": "Management",           // topic category (IRRI)
  "source_org": "IRRI",               // originating organisation
  "lang": "en",                       // language code
  "triples": []                       // extracted knowledge-graph triples
}
```

## License

The sample data in this repository originates from third-party public sources
(IRRI Rice Knowledge Bank and CGSpace/CGIAR). Please refer to each source's own terms
for any reuse of the original content.

The data files are provided here solely for **research reproduction and review**
purposes. The LEAF-RAG code and full experimental datasets are **not** included in
this repository.
