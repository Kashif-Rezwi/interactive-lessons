# ADR-0014: Rename the learner-artifact brand from Interactive Notes to Interactive Lessons

**Status:** Accepted  
**Date:** 2026-09-11  
**Owner:** Repository maintainer (Human Accountable Owner)  
**Decision scope:** Living documentation, content-package navigation labels, agent skill triggers, candidate verification tooling, and repository hosting identity (GitHub repository name); all future governed interactive lesson candidates  
**Supersedes / superseded by:** none

## Context and problem

The learner-facing artifacts produced by the governed P0–P6 workflow were branded **Interactive Notes** (lesson standard colophon: "Built with ♥ using Interactive Notes"; GitHub repository `interactive-notes`). The name understates what the artifacts are: they are *lessons* — sequenced, assessed, interactive teaching units derived from a class source — not passive notes. The owner, who uses the system to convert course material into study lessons, decided the artifact family and repository identity should say so directly.

The rename conflicts with a preservation constraint: twelve of the thirteen existing generated artifacts carry the Interactive Notes colophon, and their SHA-256 identities are recorded in run ledgers and evaluations. The repository's invariants (traceability, reversible learning, append-only records) prohibit rewriting those bytes or the historical records that mention the old brand. A repository-wide inventory found the brand string in 26 Markdown/Python files plus 12 generated artifacts, of which 19 record files, 2 accepted ADRs, and all 13 artifacts are historical surfaces.

## Decision

1. The learner-facing artifact brand is **Interactive Lessons**. The system name **Learning OS** is unchanged.
2. Living surfaces adopt the new brand: the lesson standard (title and §1.1 colophon definition), the lesson generation workflow title, the workflows index, module-package navigation labels, the repository README, agent skill triggers, and the GitHub repository (`interactive-notes` → `interactive-lessons`, with the git remote URL updated accordingly).
3. Historical surfaces are preserved byte-for-byte: all `records/` entries, accepted ADRs, and all existing generated artifacts keep their original bytes, recorded hashes, and the Interactive Notes colophon they were generated with.
4. `scripts/verify-candidate.py` accepts both colophon brands ("Interactive Lessons" and "Interactive Notes") so preserved historical artifacts continue to pass verification and new candidates comply with the amended standard.
5. File and directory names inside the repository are unchanged; the `<note-slug>-v<N>` filename convention refers to the source note, not the brand.

## Decision drivers

- Accuracy: the artifacts are lessons (outcomes, sequence, assessment, feedback), and the brand should not misdescribe them.
- Traceability invariant: recorded artifact hashes and run ledgers must remain valid; a brand change must not falsify history.
- Repository identity coherence: the GitHub repository name, the artifact colophon, and the entry-point README should tell one story.

## Considered options

| Option | Benefits | Costs/risks | Why selected or rejected |
| --- | --- | --- | --- |
| A. Rewrite brand strings everywhere, including records and generated artifacts | Visually uniform history | Falsifies provenance: recorded SHA-256 identities break; violates append-only records and the byte-for-byte preservation precedent (v1) | Rejected |
| B. Rename only future-facing surfaces; preserve historical bytes and records; verifier accepts both brands (chosen) | History stays true; new artifacts carry the accurate brand; checker and verifier keep passing | Two brands coexist in the repository permanently (historical vs current) | Selected |
| C. Keep the Interactive Notes brand | Zero change | Name continues to misdescribe the artifacts; repository identity stays misaligned with what the pipeline produces | Rejected |

## Consequences

- **Positive:** The artifact name now matches its pedagogy (a lesson, not a note). The GitHub repository name, README identity line, and lesson colophon tell one consistent story. Historical evidence remains valid and verifiable.
- **Negative:** Two colophon brands coexist: pre-2026-09-11 artifacts read "Interactive Notes", newer ones "Interactive Lessons". The verifier permanently carries both accepted phrases unless historical artifacts are superseded by governed rebuilds.
- **Operational:** The GitHub repository rename updates the remote URL (GitHub redirects the old URL); the local clone directory is renamed to match. No file paths inside the repository change, so no internal links are affected.
- **Reversibility:** Reversible for future artifacts by superseding this ADR; the historical preservation clause is not reversible — bytes and records must not be retroactively rewritten regardless of brand direction.

## Evidence and validation

- `python3 scripts/check-repo.py` exits 0 after the rename edits: all relative links resolve, the ADR index includes ADR-0014, and the 16 provenance-covered content files retain their recorded hashes (no artifact bytes were modified).
- `python3 scripts/verify-candidate.py` passes on the reference candidate CAN-2026-0009 (`linear-algebra-foundations-v10.html`), which carries the pre-rename colophon — demonstrating backward compatibility of the amended phrase list.
- GitHub repository metadata verified via `gh`: repository renamed to `interactive-lessons`; description updated to the new brand.

## Rollback or migration plan

Supersede this ADR; restore the former colophon definition in the lesson standard; revert the renamed living surfaces; rename the GitHub repository back. Historical artifacts and records are not part of any rollback — they stay as generated regardless of brand direction.

## Review evidence

Reviewed and accepted by the repository maintainer (Human Accountable Owner) on 2026-09-11 under the Stage 1 solo-maintainer path (see review policy, Status accuracy). Scope inspected: this ADR, the lesson standard colophon clause, the module package README, the agent skill triggers, the verifier colophon check, and repository-wide grep evidence classifying every brand occurrence as historical or living. Decision: accept. Limitation: non-independent self-review recorded per policy.

## Review trigger/date

Review at the Stage 1 calibration review or 2026-11-04, whichever comes first.

