# FactoryMind — RAG Knowledge System Case Study

**Live demo:** https://demo.farshidghaffari.net

FactoryMind is a source-bound Retrieval-Augmented Generation (RAG) knowledge system designed to turn large document collections into multilingual, citation-grounded answers with inspectable evidence.

This repository is a **public case study only**. The production source code, prompts, retrieval implementation, infrastructure secrets, licensed fonts, databases, and source PDFs are intentionally private.

## Demo snapshot

The current public demo uses a licensed training corpus of:

- 7 diving manuals
- 666 pages
- 598 indexed page-level chunks
- English source material
- Multilingual questions and answers, including Persian
- Exact source-page citations and excerpt inspection
- Public excerpt-only source policy — original PDFs are not exposed for download

The demo is an independent technology demonstration and is not the official IANTD website.

## What the system demonstrates

### Grounded answers
Answers are generated only from retrieved source evidence. If the corpus does not support a claim, the system is designed to abstain or lower confidence rather than invent an answer.

### Cross-document retrieval
FactoryMind can synthesize evidence across multiple manuals and pages instead of treating each document as an isolated chat attachment.

### Multilingual retrieval
A user can ask in one language while the source corpus is in another. The system performs multilingual query handling and returns the answer in the user's language while preserving the original source references.

### Inspectable citations
Each answer can expose the supporting source title, edition, page, section, retrieval reason, and a limited excerpt used as evidence.

### Privacy-aware source access
The public demo exposes only evidence excerpts. Full source PDFs are not served as public downloadable files.

### Production deployment
The public demo runs as a containerized service with:
- FastAPI application layer
- PostgreSQL + pgvector
- hybrid retrieval
- OpenAI embeddings and answer generation
- Docker Compose
- HTTPS reverse proxy
- production rate limits and health checks
- security headers and restricted public endpoints

## Product direction

The same engine can support multiple isolated knowledge libraries, for example:

- technical manuals
- internal SOPs
- training libraries
- engineering documentation
- regulated study/reference collections
- private company knowledge bases

The longer-term architecture is:

```text
Account
└── Library
    ├── Documents
    ├── Members
    ├── Permissions
    ├── Retrieval policy
    └── Usage limits
```

## Public demo UX

The demo uses a dossier-inspired black-and-white interface:
- sharp rectangular layout
- evidence highlighted in yellow
- excerpt-only document preview
- red "CLASSIFIED" stamp as visual demo styling
- Persian RTL support
- source-language text preserved in LTR

The "CLASSIFIED" treatment is purely visual styling and does not imply actual document classification.

## Architecture overview

See [ARCHITECTURE.md](ARCHITECTURE.md) for a deliberately high-level system diagram that does not disclose implementation details.

## Security and disclosure boundaries

See [SECURITY.md](SECURITY.md) and [PUBLIC_DISCLOSURE.md](PUBLIC_DISCLOSURE.md).

## What is intentionally not published

This repository does **not** contain:

- application source code
- proprietary prompts
- retrieval/ranking implementation
- query decomposition logic
- database schema or production data
- Docker production configuration
- API keys or environment files
- original training PDFs
- licensed font files
- deployment credentials
- private operational runbooks

## Status

**Production demo:** online  
**Current milestone:** public release candidate  
**Next:** mobile responsive polish, launch packaging, and multi-library platform work

---

Built by **Farshid Ghaffari** as a production RAG / knowledge-systems case study.
