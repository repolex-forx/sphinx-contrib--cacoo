# Repolex Knowledge Graph of sphinx-contrib/cacoo

RDF knowledge graph data for [sphinx-contrib/cacoo](https://github.com/sphinx-contrib/cacoo), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download sphinx-contrib/cacoo
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 0821dbe96967de4c6ec16ea811163c50c7b437f6
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 0821dbe96967de4c6ec16ea811163c50c7b437f6
│           └── chunk-001.nq.gz
├── blob
│   ├── 2eba9160d403563d8b100534a4d950281de057e6.nq.gz
│   ├── 300e100e3a1ba7b735f0ebc80bda2b42d78a8922.nq.gz
│   ├── 62d66630bb71f20525127abe9cb6e9144b73c6e1.nq.gz
│   ├── 8e7e2bc0d26ebc39199523caf9850ff62f3d650a.nq.gz
│   ├── 9d4c00f9d6bc03866900ac20aadabf203cd22756.nq.gz
│   ├── b5a7dc29ef0f7f3593b1c61cfc5dfe8a17d3918c.nq.gz
│   ├── bfdbe9ac05d69ac822cc31a082bef4a3b183e2e3.nq.gz
│   └── c2eb7df7818cd20a944d362e5ada1b73193cba4d.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 0821dbe96967de4c6ec16ea811163c50c7b437f6.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 14 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[sphinx-contrib/cacoo](https://github.com/sphinx-contrib/cacoo)

---
*Parsed on 2026-11-06 by [repolex](https://repolex.ai)*
