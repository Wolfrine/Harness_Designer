# Harness Designer

A minimal, domain-agnostic seed harness that progressively learns an objective and evolves the AI working environment around it.

The user should not need to know how to design an agent harness. They describe what they are trying to accomplish; the seed discovers the subject, starts useful work, observes recurring patterns and progressively places durable improvements into the right harness primitive.

## What happens after cloning

1. A new agent session reads `AGENTS.md`.
2. If the repo is still uninitialized, the bootstrap skill asks a few adaptive, high-information questions about the objective and current situation.
3. The agent records only the minimum useful subject model and creates the smallest harness needed to begin.
4. Real work starts.
5. As work continues, durable patterns can become knowledge, instructions, skills, hooks, evaluations, tools, specialist agents, loops or state.
6. Harness changes are reviewed for value, duplication and staleness instead of accumulating forever.

```text
objective
   ↓
discovery
   ↓
minimum viable harness
   ↓
real work
   ↓
observe friction / repetition / discoveries
   ↓
classify → test → promote / revise / retire
   ↓
more specialized working environment
```

## Core principle

**The seed is not the finished harness. It is the machinery that helps a harness become appropriate to its subject.**

Do not preload dozens of generic skills or rules. Specialization should be earned through the objective and actual work.

## Repository structure

```text
AGENTS.md                  Agent entrypoint and minimal operating contract
.harness/
  manifest.yaml            Current harness identity and maturity
  objective.md             Evolving statement of objective and constraints
  architecture.md          Placement rules for harness primitives
  evolution/README.md      Candidate → active → retired lifecycle
skills/
  bootstrap/               First-run subject discovery
  harness-designer/        Converts durable patterns into harness structure
  harness-review/          Consolidates and prunes the harness
hooks/
  session-start.md         Portable start-of-session lifecycle contract
  session-end.md           Portable end-of-session lifecycle contract
templates/                 Lightweight templates for new primitives
```

## Harness primitives

| Need discovered during work | Prefer |
|---|---|
| Stable fact/reference material | Knowledge/docs |
| Stable behavioral principle | Instruction |
| Reusable procedure | Skill |
| Something that must deterministically happen | Hook |
| Objective quality criterion | Evaluation |
| External capability | Tool/connector |
| Independent specialist reasoning | Agent |
| Repeated or autonomous process | Loop |
| Mutable current position | State |
| One-off context | Keep in the conversation |

The smallest adequate primitive wins.

## First use

Clone the repository, open it with an agent that can read/write the workspace, and state what you want to work on. The seed should guide discovery from there rather than making you configure an AI architecture first.

## v0.1 philosophy

This version is intentionally small and runtime-neutral. The lifecycle hooks are contracts rather than platform-specific configuration. A future adapter can map them into Codex, Claude Code, Cursor or another runtime when native hook behavior is useful.

The project should evolve from evidence gathered through real usage, including comparison against mature harnesses and feedback from people starting new subjects from this seed.
