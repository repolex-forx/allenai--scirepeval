# Repolex Knowledge Graph of allenai/scirepeval

RDF knowledge graph data for [allenai/scirepeval](https://github.com/allenai/scirepeval), parsed by [repolex](https://repolex.ai).

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
rlex download allenai/scirepeval
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── e04594e6401cb68fb4ddf6daa801fb219cccc0bb
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── e04594e6401cb68fb4ddf6daa801fb219cccc0bb
│           └── chunk-001.nq.gz
├── blob
│   ├── 00257965f564cce85e6e792599097194155d0a62.nq.gz
│   ├── 07984454d7aa73617f850459432faa73d5de331d.nq.gz
│   ├── 0a1120de70583d2832d0b3c540450fe0f415f1f2.nq.gz
│   ├── 0d0757812baa7200f2918ac5f0b07c7c9793117f.nq.gz
│   ├── 107af2c417979c2e63d3da17263e76ae8e88ea41.nq.gz
│   ├── 143777210e22b25d2f896522d340beb9990b80dc.nq.gz
│   ├── 14f27f81e92e04830826a883920956ffef7e32f3.nq.gz
│   ├── 261eeb9e9f8b2b4b0d119366dda99c6fd7d35c64.nq.gz
│   ├── 26e7d5e58841fe46da1f6923a86d0cf0e06621cd.nq.gz
│   ├── 2f4b01a7ec833a047c26d9d4ff3f3cc3e95a56e6.nq.gz
│   ├── 324efb19c8a3461952c2f829c333ba382b70adf3.nq.gz
│   ├── 3f4b859d5e3d4604a7e1758ef5f3f1bfc2b259b6.nq.gz
│   ├── 5bd94e198e5128a314bb57fa226d3ed2b000ba90.nq.gz
│   ├── 5d5817ea58c5a65037bc59b8518f40e1668f889d.nq.gz
│   ├── 60086cd913ca6e3be7dfa8935917412ce0afbb97.nq.gz
│   ├── 6133e10219a86898c5cdcb8dc89d22ef1e7f30b8.nq.gz
│   ├── 6188e8bcbd1426f07bc9a6aa8657f500cf7eef27.nq.gz
│   ├── 6297bc0b9ceece9e416e143d311633224b067ba2.nq.gz
│   ├── 670e4045ef87b937262c283518ba861962147744.nq.gz
│   ├── 68bc17f9ff2104a9d7b6777058bb4c343ca72609.nq.gz
│   ├── 69568952cd92852ec4af5c5b219a58be5e7e18ea.nq.gz
│   ├── 762e6374d200546b792fe9972cf8a234c072763e.nq.gz
│   ├── 79b957ce5f0118275e17ba2db425cce437f9d8b9.nq.gz
│   ├── 81a68e11ea2bd8a770acd9914d2d044722c27b7c.nq.gz
│   ├── 902b85b58b51d037085015a1a01a8bd16af30caa.nq.gz
│   ├── ad438303e3df04a123896b98c70cc1d9ae13a163.nq.gz
│   ├── b32c6fd08791fd7d09cd9725d0bde57cc6f146c7.nq.gz
│   ├── bbb20e6a137c902872bc8d4ca383c7ef27f3777c.nq.gz
│   ├── bf7361cc39bfc77a3ba535318ea31d35dee9667e.nq.gz
│   ├── c11ea9e26dd5659a079cf2a9b6b3b28b496461da.nq.gz
│   ├── c2909bd4d3badca9c888ec76a6f85d655da00df4.nq.gz
│   ├── caaabe6767cd6d388ba35fffaf83766ef9f24888.nq.gz
│   ├── d7b7f62ee2f7198f6ee4cfe3dab3bfc72845d747.nq.gz
│   ├── dd90dee55a344bdcd3894cc1fbd2c8710fb8edf8.nq.gz
│   ├── df744643123f90f549b8a92167bded759c02619a.nq.gz
│   ├── e40a1031c7a21404c2dfa45430fdac0941ce5ffa.nq.gz
│   ├── ef765309a55e159246f82e12c9b0d507ea49041b.nq.gz
│   ├── f75e9d59c4606a12cb8ad3b7a5da3a4b85bcbaae.nq.gz
│   └── ffa0f68c887aaf8f014bd8a045f81aaa7eab4517.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── e04594e6401cb68fb4ddf6daa801fb219cccc0bb.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 47 files
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

[allenai/scirepeval](https://github.com/allenai/scirepeval)

---
*Parsed on 2026-11-07 by [repolex](https://repolex.ai)*
