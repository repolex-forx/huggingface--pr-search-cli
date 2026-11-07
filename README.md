# Repolex Knowledge Graph of huggingface/pr-search-cli

RDF knowledge graph data for [huggingface/pr-search-cli](https://github.com/huggingface/pr-search-cli), parsed by [repolex](https://repolex.ai).

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
rlex download huggingface/pr-search-cli
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 3906344cc874cc39f1a25562222fc2e669e9643d
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 3906344cc874cc39f1a25562222fc2e669e9643d
│           └── chunk-001.nq.gz
├── blob
│   ├── 0eb2460768a58faf2cad14285775744c771b288f.nq.gz
│   ├── 14e0772a5cf924b6db0ca892e8eaf4b8ef36d5e0.nq.gz
│   ├── 1a32d30050f379d9fdee3ef2ce35bd03ee74b657.nq.gz
│   ├── 25bdfbf7d3a0f24966599d739e77cca00e5da56c.nq.gz
│   ├── 3498c4fd2ac22726cbf162847db347fd1b97bd81.nq.gz
│   ├── 39bef791343f0dba59c2707d8f2bd1d77e33f0c0.nq.gz
│   ├── 3e95b719050df0be96da5d3a8bc40c769328777b.nq.gz
│   ├── 5e265eb7164c40aa0de72b76200b06653ee8ea00.nq.gz
│   ├── 6e8eceda51978d9d7c3c055fba25cb25cfc4de3e.nq.gz
│   ├── 6ed4560317d86f3ac2de6ed43b6b03040d70d493.nq.gz
│   ├── 71744ec350656cd94caf62e6c3be92c813e528fa.nq.gz
│   ├── 73da7172098b533b32624f5359e5db6b2a179c56.nq.gz
│   ├── b24dea19fa4899de2f8c2e714ed264d34ef12e05.nq.gz
│   ├── f189128a70a3fbb75b726948025cad9ccb49a046.nq.gz
│   └── f7c3d5d8964408324f1dbd528bffe660f8f1ccf7.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 3906344cc874cc39f1a25562222fc2e669e9643d.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 22 files
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

[huggingface/pr-search-cli](https://github.com/huggingface/pr-search-cli)

---
*Parsed on 2026-11-07 by [repolex](https://repolex.ai)*
