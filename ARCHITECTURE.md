# Architecture Overview

FactoryMind is designed as a source-bound RAG knowledge system with a strict separation between public interaction, retrieval infrastructure, and private source material.

```text
User
  ↓
HTTPS / Reverse Proxy
  ↓
FactoryMind Web UI + API
  ↓
Query handling
  ↓
Hybrid retrieval
  ├── semantic vector search
  └── lexical / metadata retrieval
  ↓
Evidence selection
  ↓
Grounded answer generation
  ↓
Answer + citations + excerpt viewer

Private data plane
  ├── PostgreSQL
  ├── pgvector
  ├── indexed document metadata
  └── source files used for ingestion
```

## Design principles

### Source-bound generation
The answer layer is constrained to retrieved source evidence rather than unconstrained web-style generation.

### Evidence-first UX
A response is not treated as complete until the user can inspect the cited source excerpt.

### Multilingual interface
Question language, source language, and answer language can differ.

### Private source boundary
Public users can inspect limited excerpts used as evidence, but full source files are not exposed by the public application.

### Corpus isolation
The product direction supports multiple libraries with isolated retrieval scopes, permissions, policies, and usage limits.

## Current production stack

At a high level, the public demo uses:

- FastAPI
- PostgreSQL
- pgvector
- OpenAI embeddings
- OpenAI answer generation
- Docker Compose
- Caddy / HTTPS
- server-side rate limiting
- production health/readiness checks

Implementation details that would materially expose the proprietary retrieval strategy, prompts, production configuration, or deployment secrets are intentionally excluded from this repository.
