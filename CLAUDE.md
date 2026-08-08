# You're at the repo root — the vault is one level down

This repository holds **two** vaults. Nothing should be ingested or edited here at the root.

- **`starter/`** — the workshop kit. Two sources in `raw/`, empty `wiki/`. **Work here.**
- **`finished/`** — the completed reference. Same kit after one `/ingest`. Read-only.

## If someone asks you to ingest, query, or lint from this directory

They almost certainly meant to open `starter/`. Tell them, and offer to work in `starter/`
instead — do not create `raw/` or `wiki/` folders at the repo root, and do not ingest
`finished/` into anything.

Each subfolder has its own `CLAUDE.md` with the real contract. Read `starter/CLAUDE.md`
before doing any work in `starter/`.
