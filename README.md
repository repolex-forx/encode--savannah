# Repolex Knowledge Graph of encode/savannah

RDF knowledge graph data for [encode/savannah](https://github.com/encode/savannah), parsed by [repolex](https://repolex.ai).

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
rlex download encode/savannah
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 291e73d45559ec2fa93a7b92953333316c53c70d
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 291e73d45559ec2fa93a7b92953333316c53c70d
│           └── chunk-001.nq.gz
├── blob
│   ├── 0623a5daf95d1c92316ed90e9bb50ea94630cdd6.nq.gz
│   ├── 1ce089237c25fa0d060fa97bde814537ab2b7b73.nq.gz
│   ├── 28250110983712e4ca7788dc7e33ca8ff977af65.nq.gz
│   ├── 2c70eaaa5f167fd1b948c2ca0df662f3df1957ff.nq.gz
│   ├── 40d93f0d436443e55ca86bc9acdc5cc4282eeddc.nq.gz
│   ├── 41417c16b1a733fc7a65d3a0d87e55cd91ab975e.nq.gz
│   ├── 48ad100a0840819e1a1fd78563fcaf6226d78b7c.nq.gz
│   ├── 4e980ebde987371ea43e54f69617401e8261c08a.nq.gz
│   ├── 570f46f71f4df7b04c483c8bb3366690dc24448b.nq.gz
│   ├── 90c5c30f7b003358976d4c09c8d90d40a23b05e0.nq.gz
│   ├── 9e70e276915af6db05213a2c8ba75ead6603bc23.nq.gz
│   ├── a5f6b270a7c94d6904c3db2d8bc13b39ed39f2a2.nq.gz
│   ├── a90c02db52ce6039dec93fc7eaccfd73702e9c16.nq.gz
│   ├── afc54e114ef4be3e609c181e4e744450eab4bcda.nq.gz
│   ├── c1eec90c8d40715ae54d6aec2013a920f87467b8.nq.gz
│   ├── d3876dd05baba4b74f6d91b5ea8bc0837944ff61.nq.gz
│   └── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 291e73d45559ec2fa93a7b92953333316c53c70d.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 23 files
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

[encode/savannah](https://github.com/encode/savannah)

---
*Parsed on 2026-10-11 by [repolex](https://repolex.ai)*
