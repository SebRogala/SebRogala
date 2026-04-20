# Hi, I'm Seb 👋

**AI Native Product Engineer** · 12 years in software · Based in Rzeszów, Poland

I build production software by directing AI — not writing code. The engineering judgment comes from a decade of commercial work; the velocity comes from AI-native workflows.

## What I'm building

**🎯 [ProfitOfExile](https://github.com/SebRogala/ProfitOfExile)** — Real-time profit analysis platform for Path of Exile lab farming
Live at [profitofexile.top](https://profitofexile.top) · 150+ installs · 100k+ LOC · Go / SvelteKit / Tauri (Rust) — built across stacks I had no prior expertise in

**🏗️ Pipeforge** *(proprietary, demo available on request)*
AI workflow orchestration plugin for Claude Code — 30+ commands, 25+ skills, 20 agents, multi-agent parallel execution with dependency resolution

**🗄️ pipeforge-mcp** *(proprietary)*
PostgreSQL-backed MCP server powering Pipeforge — 60+ tools, 30+ tables, multi-user auth, persistent state across sessions and worktrees. Deployed to production.

**📚 Education CRM** *(client project, in production)*
Multi-tenant SaaS for Polish education businesses — 3,700+ tests, PHPStan level 8 on 1,200+ files — PHP 8.4 / Symfony 7.4

## How I work

- **Requirements first** — I talk to users, understand the real problem, break it down into clear plans
- **AI as the delivery mechanism** — Claude Code + Pipeforge pipelines, multi-agent orchestration
- **Critical thinking on AI output** — discovered AI silently summarized 491 lines into 122 during a migration; built a fidelity-auditor to catch it before anyone else shipped that bug
- **Context engineering** — designing the information environment agents operate in, not just the prompts

## Open source

- [veiset/poe-vendor-string#364](https://github.com/veiset/poe-vendor-string/pull/364) — feature PR adding prefix/suffix indicators and grouping to the Maps page of a well-known Path of Exile community tool. Introduced the first tests in the repo (9 tests / 2 suites), a RePoE data-fetch pipeline, and drift-detection coverage. Maintainer validated the need (planning to add the field upstream) and agreen on the frontend — will invite me back to finish it once the upstream data model is in place.
- [obra/superpowers#520](https://github.com/obra/superpowers/pull/520) — proposed smart question batching with ASCII mockup previews for the brainstorming skill in Jesse Vincent's Claude Code plugin framework. Empirically tested (6→3 AskUserQuestion calls). Closed after v5 took a different approach (browser-based visual companion).
- [anthropics/claude-code#26423](https://github.com/anthropics/claude-code/issues/26423) — detailed bug report on `PreToolUse` hook `systemMessage` not surfacing to the assistant after a block. Closed as "not planned" but captures a real UX gap in hook-driven self-correction.

## Speaking

- **rg-dev Meetup (future, planned for Aug 2026)** — *AI Migration Audit: When AI Summarizes Instead of Migrates*
- Xebia Internal Conference (Nov 2023) — *GitHub Actions & Continuous Delivery on Shared Hosting*

## Reach me

- 📧 sebrogala@gmail.com
- 💼 [linkedin.com/in/seb-rogala](https://linkedin.com/in/seb-rogala)
- 🌱 Running a small vineyard — 70 plants, 11 varieties — building systems that create the right conditions for growth
