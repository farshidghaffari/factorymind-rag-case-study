# Security Notes

This repository documents only the public case-study surface of FactoryMind.

## Public demo safeguards

The production demo is configured around the following boundaries:

- no public access to original PDF files
- excerpt-only source inspection
- no public database access
- no public search/debug endpoint in production
- no public API keys or environment configuration
- no exposed application stack traces
- health/readiness endpoints return limited information
- server-side request limits
- constrained concurrent answer generation
- HTTPS-only public access
- security headers including frame protection and content-type protections

## Infrastructure posture

The current deployment uses:

- non-root SSH administration
- SSH key authentication
- password login disabled
- root SSH login disabled
- non-default SSH port
- UFW firewall
- Fail2ban
- Dockerized application services
- PostgreSQL isolated from the public internet
- secrets stored only on the server

## Deliberately private material

The following are not published:

- production source code
- prompts
- retrieval/reranking logic
- multi-query decomposition logic
- environment files
- credentials
- database dumps
- deployment configuration
- source PDFs
- licensed fonts

## Reporting

For a security concern related to the public demo, use the contact information on:

https://farshidghaffari.net/contact
