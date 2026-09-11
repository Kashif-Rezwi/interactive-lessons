# Learning OS

> A documentation-first, agent-governed operating system that turns technical source material into rigorously evaluated, interactive lessons.

**Learning OS** is the operating system; **Interactive Lessons** are the learner-facing artifacts it produces. This repository hosts both: the governance and knowledge system (`docs/`, `library/`, `templates/`, `records/`, `scripts/`, `.agents/`) and the generated interactive lessons (`content/`).

Learning OS is the documentation-first operating system for a future AI-native platform that turns technical source material into rigorous, beautiful, interactive learning experiences.

This repository is deliberately **not the application**. It is the durable source of truth that tells humans and AI coding agents what to build, why it matters, how work is performed, how quality is measured, and how lessons learned become reusable knowledge. No production implementation belongs here until the foundation documents explicitly authorize it.

The project began as the maintainer's personal pipeline for turning course notes into interactive study lessons, and is evolving toward a reusable agent skill and, eventually, a web application (roadmap Stages 3–4).

## Repository status

The repository is at **Stage 2 — reproducible workflow automation** on the [capability roadmap](docs/11-roadmap/roadmap.md): the documentation foundation (Stage 0) is complete, manual governed pilots (Stage 1) are substantially complete, and bounded automation is in progress under [ADR-0012](docs/adr/0012-autonomous-pipeline-orchestration.md).

What exists and works today:

- A governed **P0–P6 lesson-generation workflow** ([workflow](docs/03-workflows/lesson-generation-workflow.md)) that has produced 13 interactive lesson versions across 3 classes of an AIML-4 module, each with full lineage.
- An **autonomous agent skill** at [`.agents/skills/generate-lesson/SKILL.md`](.agents/skills/generate-lesson/SKILL.md) that executes the workflow end to end.
- **69 append-only evidence records** in `records/` — 12 generation runs, 13 evaluations, 11 learning plans, 11 experience specifications, 10 concept models, 6 curated memory items, 1 frozen benchmark — all cross-linked.
- **13 architecture decision records** in [`docs/adr/`](docs/adr/README.md), 7 versioned prompt cards in `library/prompts/`, an executable QA rubric, and a lesson-pattern catalog.
- Two dependency-free Python verification tools (see [Tooling](#tooling)).

## Start here

1. Read [the charter](docs/00-foundation/charter.md), [principles](docs/00-foundation/principles.md), and [glossary](docs/00-foundation/glossary.md).
2. Read [the repository map](docs/02-system/repository-map.md) and [system blueprint](docs/02-system/system-blueprint.md).
3. Follow [the agent protocol](docs/04-agents/coordination-protocol.md) and the role card relevant to your work.
4. Use the [quality loop](docs/03-workflows/quality-loop.md) for every generation or design decision.
5. Record decisions, evaluations, run evidence, and reusable lessons using [templates](templates/README.md).

## Repository contract

- Documentation precedes implementation; a proposed code change needs a linked decision, contract, and acceptance criteria.
- AI agents are first-class participants, but high-impact decisions remain reviewable by humans.
- Claims, scores, outputs, and decisions must be traceable to their evidence.
- Learning material lives in `content/`, where each course and module is navigated through a README and separates preserved inputs from generated outputs. The [content-package convention](docs/02-system/content-package-convention.md) is authoritative.
- The operating manual contains no learner-facing application code, APIs, or runtime configuration. The only executables are the repository-maintenance and verification tools in `scripts/`. Learner-facing files retained under `content/` are course material, not application implementation.

## The lesson pipeline

Every interactive lesson is produced by a governed transformation pipeline, not a single generation call:

```text
Source notebook (SHA-256 identity, SRC record)
  → P1 concept model (CM) → P2 learning plan (LP) → P3 experience spec (XS)
  → P4 single-file HTML candidate (versioned prompt card, zero external dependencies)
  → P5 six audits + adversarial gate (coverage, math, dependency order, interaction, accessibility, rendered output)
  → P6 evaluation record → human release judgment → curated memory
```

A stage may not consume an unapproved upstream artifact, and generation cannot self-certify release.

## Viewing the interactive lessons

Generated lessons are self-contained HTML files with no build step and no external dependencies. Open them directly in a browser — on macOS:

```bash
open content/aiml-4/module-02-math-statistics-for-ml/generated/linear-algebra-foundations-v10.html
```

The current reference candidate is `linear-algebra-foundations-v10.html`; module navigation and version history live in the [module README](content/aiml-4/module-02-math-statistics-for-ml/README.md). All generated lessons are `private-pilot-complete` under non-independent review — they are not public releases or efficacy claims.

## Tooling

Both tools are read-only, offline, and require only Python 3.8+ (standard library, no installs):

```bash
# Repository hygiene: links, provenance hashes, rubric weights, status vocabularies, naming, ADR index
python3 scripts/check-repo.py

# Mechanical verification of a generated HTML lesson candidate
python3 scripts/verify-candidate.py content/aiml-4/module-02-math-statistics-for-ml/generated/linear-algebra-foundations-v10.html
```

`check-repo.py` must exit 0 before any commit to governed surfaces (see [AGENTS.md](AGENTS.md) and [ADR-0008](docs/adr/0008-repository-checker-tooling.md)). There is no CI yet; quality gates run locally.

## Navigation

| Need | Read |
| --- | --- |
| Product intent and limits | [Product brief](docs/01-product/product-brief.md) |
| Future system boundaries and data lineage | [System blueprint](docs/02-system/system-blueprint.md) |
| End-to-end quality process | [Workflow architecture](docs/03-workflows/workflow-architecture.md) |
| Generating an interactive lesson from notes | [Lesson standard](docs/01-product/lesson-standard.md), [canvas engineering standard](docs/01-product/canvas-engineering-standard.md), and [lesson generation workflow](docs/03-workflows/lesson-generation-workflow.md) |
| Agent roles and handoffs | [Agent catalog](docs/04-agents/agent-catalog.md) |
| Prompt lifecycle | [Prompt architecture](docs/05-prompts/prompt-architecture.md) |
| Scoring and benchmarks | [Evaluation framework](docs/06-evaluation/evaluation-framework.md) |
| Long-term learning | [Memory architecture](docs/07-memory/memory-architecture.md) |
| Run provenance and observability | [Logging architecture](docs/08-observability/logging-architecture.md) |
| Repeatable operations | [Playbooks](docs/09-operations/playbooks.md) |
| Standards and releases | [Governance](docs/10-governance/README.md) |
| Cross-cutting pipeline audits | [Audits](docs/audit/README.md) |
| Risks, questions, and staged evolution | [Roadmap](docs/11-roadmap/README.md) |

## Maturity path

The repository progresses through explicit gates: documentation foundation, manually operated workflow, reproducible automation, developer tooling, product implementation, and platform governance. The authoritative sequence is in [the roadmap](docs/11-roadmap/roadmap.md).

## Contributing

Changes to governed surfaces follow the change protocol in [AGENTS.md](AGENTS.md): locate the applicable acceptance criteria, make the smallest authoritative document change, update cross-links, add an ADR for durable architectural choices, and run `python3 scripts/check-repo.py` before committing. Review requirements are defined by the [review policy](docs/10-governance/review-policy.md).

## License

No license has been selected yet. Until one is added, default copyright applies. Contact the maintainer for reuse questions.
