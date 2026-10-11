# Repolex Knowledge Graph of psf/project-funding-wg

RDF knowledge graph data for [psf/project-funding-wg](https://github.com/psf/project-funding-wg), parsed by [repolex](https://repolex.ai).

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
rlex download psf/project-funding-wg
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 9c21a8c901376395330ce493d7923b79379ab666
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 9c21a8c901376395330ce493d7923b79379ab666
│           └── chunk-001.nq.gz
├── blob
│   ├── 7bd85a7363073962e41fbf0b7bb8ac298f632609.nq.gz
│   ├── aa7a3ad0c209cf76ad36ae80be0a8e3dc747ce25.nq.gz
│   ├── ad901d53334780892f6afd3a2414c135675104c3.nq.gz
│   └── b5edae63914ad5d13b32367b8bd8d0ee172a1520.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 9c21a8c901376395330ce493d7923b79379ab666.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 12 files
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

[psf/project-funding-wg](https://github.com/psf/project-funding-wg)

---
*Parsed on 2026-10-11 by [repolex](https://repolex.ai)*
