# Sebastian Rogala

AI-native product engineer building production software through directed agents, MCP-backed context, and structural verification.

I work at the layer between product intent and AI implementation: discovery, specs, agent orchestration, review loops, audit gates, and outcome verification.

For the elevator pitch and current availability: [sebrogala.dev](https://sebrogala.dev).

## Proof Points

### ProfitOfExile

[Repository](https://github.com/SebRogala/ProfitOfExile) | [Live app](https://profitofexile.top)

Publicly readable real-time profit analysis for Path of Exile lab farming.

- Single Go backend (server + collector) feeding two clients: SvelteKit web (zero-install) and Rust/Tauri desktop with OCR + in-game overlays — one source of truth, two delivery surfaces
- ~52k source LOC across Go, SvelteKit, Tauri/Rust (excluding tests, generated assets, lockfiles), with TimescaleDB + Mercure SSE
- Web continuously deployed; desktop overlay reached usable release in ~2 weeks (v0.1.0 on 2026-03-31 → v0.6.x on 2026-04-13)
- Active Discord support channel for user reports and log-based triage
- Started as a personal tool for myself and friends, then picked up by users after creator coverage

### Pipeforge

Proprietary AI development infrastructure; walkthrough available at [sebrogala.dev/pipeforge](https://sebrogala.dev/pipeforge) and KB excerpts at [sebrogala.dev/kb](https://sebrogala.dev/kb).

Pipeforge is my Claude Code orchestration plugin plus a PostgreSQL MCP backend I built.

- 31 commands, 28 skills, 20 agents, 11 pipeline templates
- 64 MCP tools / 31 Postgres tables backing pipeline state, routes, discoveries, findings, metrics, and source-cited knowledge
- **Two orchestration patterns from different context-window eras:** `/pipe` (orchestrator clears, MCP holds state, sub-agents do work — built for the compact-prone 200k era) and `/deliver` (orchestrator keeps full context, dispatches from there — viable once 1M removed compact pressure). Configurable `context_window_size` drives chunk sizing independently of pattern.
- Sub-agent dispatch is provider-agnostic: chunk workers run as Claude or Codex; orchestrator stays on Claude, Codex preferred for execution chunks
- Per-chunk review, heavy-review (up to 5 parallel reviewer agents), fidelity-auditor, test/audit gates, hook-level enforcement, and human outcome verification
- Queryable KB with ~42 entries capturing decisions, rationale, rejected alternatives, source-file citations, and relationships

### Education CRM

Client project in production; proprietary and anonymized.

Multi-tenant course-management and lead-operations system for a Polish education client.

- 4,190 tests: 2,674 unit, 459 integration, 699 functional, 201 smoke, 157 E2E
- PHPStan level 8; full audit suite runs in ~7 minutes
- Automates lead-management, SMS/email workflows, and operational coordination that previously required manual work
- CQRS, event-driven architecture, multi-tenant ready for additional clients
- PHP 8.4, Symfony 7.4 LTS, PostgreSQL 16, Redis 7, Playwright

## Workflow Architecture

### Context Engineering

Prompt engineering is phrasing. Context engineering is infrastructure: what reaches the prompt, which store owns truth, which agent sees what, how long each artifact lives, and what happens when an input is absent.

Pipeforge uses:

- MCP + Postgres for generated state, findings, cursors, metrics, and KB entries
- Git files for authored intent: plans, ADRs, command specs, and agent definitions
- Sub-agent isolation for expensive exploration, implementation, review, and synthesis
- Phase boundaries so work can survive `/clear`, compaction, and session restarts
- Source-cited knowledge entries so decisions point back to implementation files

### Verification Layers

Self-verification can prove that an agent did what it chose to do. It cannot reliably prove that the task scope was not silently narrowed.

Pipeforge separates correctness from coverage:

- Implementation agents produce scoped chunks
- Per-chunk review checks each implementation slice
- Heavy-review runs adversarial reviewers at merge boundaries
- Fidelity-auditor checks structural moves/splits/extracts for missing or summarized content
- 4-corner adversarial audit (task ↔ plan ↔ diff ↔ ADR) at structural boundaries
- ai-logic-and-framing-auditor checks reasoning quality, not just output correctness
- Test/audit gates require evidence before completion
- Human outcome verification checks final behavior against product intent

### Observability

AI model upgrades can change behavior without warning. Pipeforge tracks enough pipeline metadata to compare model behavior across similar task shapes.

Example: Opus 4.7 regression detected across 8+ runs:

- ~2× wall-clock vs Opus 4.6
- ~2.3× token usage
- Root-caused to repeated disk round-tripping of MCP results and stricter literal adherence to written command specs
- Two revertible spec fixes shipped (config-honoured deferred mode + DRY-extracted per-phase metrics capture)

### Fidelity Audit Origin

Fidelity-auditor was built after I caught AI silently summarizing 491 lines of behavioral specs into 122 during a migration. The output looked clean; the diff matched the surface intent; but ~75% of the behavioral detail had been compressed away. Auditor now runs at every structural move/split/extract boundary, comparing source vs target line-counts and content fingerprints before allowing completion.

## Public Notes And Reports

- [anthropics/claude-code#6354 comment](https://github.com/anthropics/claude-code/issues/6354#issuecomment-3849990217) — reproducible `/clear` vs `/compact` hook-output asymmetry on Anthropic's public tracker, with repro config, results table, and suggested mechanism.
- [anthropics/claude-code#26423](https://github.com/anthropics/claude-code/issues/26423) — detailed bug report on `PreToolUse` hook `systemMessage` not surfacing after a block.
- [veiset/poe-vendor-string PRs](https://github.com/veiset/poe-vendor-string/pulls?q=is%3Apr+author%3ASebRogala) — merged PRs in Path of Exile community tool; introduced first unit tests to the repo.

## Speaking

- rg-dev Meetup, 2026-05-27 (scheduled) — AI-native workflow / migration audit talk
- Xebia Internal Conference, Nov 2023 — *GitHub Actions & Continuous Delivery on Shared Hosting*

## Contact

- Email: sebrogala@gmail.com
- LinkedIn: [linkedin.com/in/seb-rogala](https://linkedin.com/in/seb-rogala)
- Site: [sebrogala.dev](https://sebrogala.dev)
