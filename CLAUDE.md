# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

Trinity AI is **not a codebase** — it is a structured Markdown knowledge base that defines an "AI Operating System" for planning and executing content/marketing work (an agency operating system: research → strategy → planning → production → copy → knowledge management). There is no application code, no package manager, no build step, no linter, and no test suite. All content is Spanish-language Markdown documentation.

Because there's nothing to build or test, your job in this repo is almost always to **read, write, or restructure documentation** according to the rules below — not to write software.

## The one rule that overrides everything else

Every document carries a `status` field in its YAML front matter (`Planned`, `Draft`, `Review`, `Approved`, `Deprecated`, `Archived`). Per [00_Foundation/13_Documentation_Standards.md](00_Foundation/13_Documentation_Standards.md):

> Claude Code únicamente utilizará documentos con estado **Approved** como fuente oficial de conocimiento. Los documentos en estado Draft, Review o Planned nunca deberán utilizarse para tomar decisiones.

Concretely: before treating any document's content as authoritative (to answer a question, generate new content, or resolve a contradiction), check its front matter `status`. Almost everything in this repo is currently `Draft` — including `CORE.md` itself (v0.2.0, Draft) — so at this stage nothing should be treated as final/official; flag that when it matters. Never modify an `Approved` document directly — changes must re-enter the `Draft → Review → Approved` cycle (see [13_Governance/](13_Governance/)).

## Repository structure and read order

The system is organized as numbered modules, meant to be consulted in this order (most stable/foundational first):

| Module | Purpose |
|---|---|
| `CORE.md` | Entry point. Defines the operating flow every request should follow and which protocols/modules apply. Start here. |
| `00_Foundation/` | Identity, principles, and mandatory protocols (communication, behavior, thinking, decision-making, documentation standards). Everything else depends on this. |
| `01_Architecture/` | The system's technical blueprint — how modules relate, how information flows, agent interaction, memory architecture, request lifecycle. Documents structure only; doesn't itself execute anything. |
| `02_SOPs/` | Step-by-step operating procedures for recurring tasks (currently empty scaffolding). |
| `03_Agents/` | Specialized agent definitions — role, scope, tools, limits (currently empty scaffolding). |
| `04_Frameworks/` | Reusable methodologies for solving a class of problem (Content, Marketing, Decision, Automation, Research, Strategy — subfolders currently empty). |
| `05_Knowledge/` | Global reusable knowledge base (Marketing, Meta Ads, SEO, IA, Producción, Ventas, Content, Notion, Clientes — currently empty). |
| `06_Integrations/` | Documents connections to external tools (Notion, GitHub, Google Drive, Claude Code, Meta API, Canva) — currently empty. |
| `07_Automations/` | Documents automated processes; every automation must reference a SOP + Framework + Integration — currently empty. |
| `08_Clients/` | Per-client workspaces (`Ingresos Publicos`, `Lineas Rectas`, `Pampa`). Clients consume global knowledge but never modify it — they only add client-specific knowledge. |
| `09_Templates/` | Reusable document skeletons (`document_template.md`, `framework_template.md`, `sop_template.md`, `client_template.md`, `skill_template.md`). Use these when creating any new document of that type. |
| `10_Assets/`, `11_Examples/`, `12_Research/` | Supporting visual assets, reference implementations, and raw research — currently empty. |
| `13_Governance/` | Versioning, approval workflow, dependency and release rules for the documentation itself — currently empty (placeholder files only). |

Most module subtrees beyond `00_Foundation`, `01_Architecture`, and `CORE.md` are empty scaffolding — the project is early-stage ("🟡 En construcción" per `00_Foundation/PROYECT_CHAPTER.md`) and is deliberately building Foundation and Architecture before populating Knowledge/Automations.

## Document conventions

Every document must carry the front matter block and section structure defined in [00_Foundation/13_Documentation_Standards.md](00_Foundation/13_Documentation_Standards.md):

- **Front matter** (required): `id`, `title`, `module`, `version`, `status`, `owner`, `created`, `last_updated`, `reviewed_by`, `approved_by`, `next_review`, `dependencies`, `tags`.
- **Body sections** (minimum): Propósito, Objetivo, Desarrollo, Reglas (if applicable), Ejemplos (if applicable), Notas adicionales (optional).
- **Naming**: English, PascalCase-ish with underscores, no spaces, no special characters (e.g. `11_Communication_Guidelines.md`). Foundation/Architecture files are numerically prefixed.
- **Versioning**: semantic (`1.0.0`, `1.0.1` for fixes, `1.1.0` for compatible additions, `2.0.0` for breaking/structural changes).
- **Lifecycle**: `Planned → Draft → Review → Approved → Deprecated → Archived`. Never skip stages; never hand-edit an `Approved` doc.
- When creating a new document, start from the matching file in `09_Templates/` rather than writing structure from scratch.

## Operating principles to apply when doing work here

These come from `CORE.md` and `00_Foundation/14_AI_Behavior.md` and should shape how you approach any task in this repo, not just what you write about:

- **Reuse before creating**: search `00_Foundation`, `01_Architecture`, and any relevant `04_Frameworks`/`05_Knowledge` content before drafting something new. Don't duplicate knowledge across modules.
- **One responsibility per module**: don't mix client-specific knowledge into `05_Knowledge`, don't put process knowledge into `05_Knowledge` (that belongs in `02_SOPs`), etc.
- **Never invent information**: if context is missing (e.g., which client, which status a doc should have), ask rather than assume.
- **New documents start as `Draft`** and must go through Review before being treated as `Approved`/official.
- Responses/deliverables produced from this repo should stay in Spanish to match the existing corpus, unless the user asks otherwise.
