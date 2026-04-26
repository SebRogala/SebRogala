# Hi, I'm Seb 👋

**AI Native Product Engineer** · 12 years in software · Based in Rzeszów, Poland

I build production software by directing AI, while developing the personal infrastructure that makes that workflow repeatable. Since early 2026, zero lines by hand — across every stack I ship in. I don't read the generated code either; verification is structural (per-chunk review agents + heavy-review with up to 5 parallel reviewer agents). Human-in-the-loop is at outcome verification, not code review.

## What I'm building

**🎯 [ProfitOfExile](https://github.com/SebRogala/ProfitOfExile)** — Real-time profit analysis for Path of Exile lab farming. Built for myself and friends; a content-creator friend featured it on his YouTube channel, community adoption followed. No monetization intent.
Live at [profitofexile.top](https://profitofexile.top) · ~72k source LOC across Go / SvelteKit / Tauri (Rust) — built across stacks I had no prior expertise in. Active Discord support channel where I triage user reports via log analysis and fold recurring issues into known-issues docs.

**📚 Education CRM** *(client project, in production)*
Multi-tenant SaaS for a Polish education client — 4,190 tests (2,674 unit / 459 integration / 699 functional / 201 smoke / 157 E2E), PHPStan level 8, full audit in ~7 min — PHP 8.4 / Symfony 7.4. CQRS, event-driven architecture, GDPR compliance. In daily production use for the client's lead-management operations. Client reports the built-in SMS + email automation alone has freed hours of staff time each week vs their prior manual workflow.

**🏗️ Pipeforge** *(proprietary, two repos: plugin + MCP backend, demo available on request)*
Personal AI development infrastructure — Claude Code orchestration plugin + self-authored PostgreSQL MCP backend. Initially built from a personal need to coordinate work across multiple machines and parallel worktrees on client projects. 31 commands, 28 skills, 20 agents; multi-agent parallel execution with dependency resolution. 64 MCP tools across 31 tables backing cross-session state. Team collaboration patterns architected in from day one (seed-derived per-project agents updated from team-contributed MCP knowledge; cursor-based codemap synthesis safe for concurrent runs). Currently single-user (no team-context yet), not an architectural limit; ~1 week of docs/onboarding from team-shareable.

**⏱️ [Pomodoro Timer](https://pomodoro.softsolution.pro)** — Vue 3 / Vuetify 3 / PWA cooking-and-productivity timer. Built for myself when no existing pomodoro kept its screen on through cooking sessions. Wake-lock, overtime tracking past zero, multi-step sequences, EN/PL i18n; auto-update deferred while a timer is running. Same "personal need → shipped tool" pattern as ProfitOfExile.

## How I work

- **Requirements first** — talk to users, understand the real problem, break it down into clear plans
- **AI as the delivery mechanism** — Claude Code + Pipeforge pipelines, multi-agent orchestration
- **Critical thinking on AI output** — caught AI silently summarising 491 lines into 122 during a migration; built fidelity-auditor to catch the class of bug before anyone ships it
- **Context engineering** — designing the information environment agents operate in, not just the prompts
- **Structural enforcement over prose rules** — e.g., hook-level `cd` blocking to stop sub-agents drifting out of their worktree into main before running docker commands. Prose instructions drift; hooks don't.
- **Pipeline observability** — detected an Opus 4.7 regression through baseline comparison across 8+ runs (~2× wall-clock, ~2.3× tokens vs 4.6 on identical pipeline shapes); root-caused to sub-agents round-tripping MCP results through disk

## Open source & community

- [**anthropics/claude-code#6354** (comment)](https://github.com/anthropics/claude-code/issues/6354#issuecomment-3849990217) — public bug-report comment on Anthropic's claude-code tracker isolating the compact-vs-clear hook-output asymmetry. Working SessionStart repro config, 2-row results table, proposed mechanism fix.
- [anthropics/claude-code#26423](https://github.com/anthropics/claude-code/issues/26423) — detailed bug report on `PreToolUse` hook `systemMessage` not surfacing to the assistant after a block. Closed as "not planned" but captures a real UX gap in hook-driven self-correction.

## Speaking

- **rg-dev Meetup (Aug 2026, scheduled)** — AI-native workflow: phases, orchestration, shipping with directed agents
- Xebia Internal Conference (Nov 2023) — *GitHub Actions & Continuous Delivery on Shared Hosting*

## Reach me

- 📧 sebrogala@gmail.com
- 💼 [linkedin.com/in/seb-rogala](https://linkedin.com/in/seb-rogala)
- 🌱 Running a small vineyard — 50 plants, 11 varieties — building systems that create the right conditions for growth
