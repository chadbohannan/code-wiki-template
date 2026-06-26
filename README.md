# LLM-Maintained Engineering Wiki (Template)

Inspired by: Andrej karpathy's LLM-Wiki https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f

A starter template for a persistent, LLM-maintained knowledge base about a codebase — capturing system behavior, incident patterns, debugging knowledge, and operational wisdom. The LLM writes and maintains everything under `wiki/`; you curate the raw inputs in `sources/`, direct investigation, and ask questions. The full schema and operating rules live in [CLAUDE.md](CLAUDE.md), which the LLM reads as its standing contract.

## Starting a new wiki

1. Copy this directory to a new repo and open it with your LLM coding agent (e.g. Claude Code).
2. Work through the **Bootstrapping** checklist at the top of [CLAUDE.md](CLAUDE.md): replace the `{{PROJECT}}`, `{{PROJECT_DESC}}`, and `{{CODE_RAG_GLOB}}` placeholders (the project's committed identity), then delete that section.
3. Create `repos.txt` at the repo root from `repos.txt.example` (one absolute repo path per line) so the scripts know which clones to track. This holds machine-local paths and is gitignored; the `{{CODE_RAG_GLOB}}` from step 2 usually matches these repos' basenames.
4. Drop source documents (postmortems, design docs, Slack threads, log dumps) into `sources/`, then ask the agent to ingest them. `wiki/index.md` and `wiki/log.md` start empty and fill in as you go.

## Daily use

Talk to the agent in terms of the operations defined in CLAUDE.md: **ingest** a new source, **query** the wiki, **sync** against recent code changes, **lint** for health, or **enrich** a page from code. Helper scripts for bulk ingest, syncing repos, and linting are in `scripts/` — see [scripts/README.md](scripts/README.md).
