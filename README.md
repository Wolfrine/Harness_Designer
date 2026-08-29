# Harness Designer

A minimal, domain-agnostic seed harness that progressively learns an objective and evolves the AI working environment around it.

The user should not need to know how to design an agent harness. They describe what they are trying to accomplish; the seed discovers the subject, starts useful work, observes recurring patterns and progressively places durable improvements into the right harness primitive.

## Core principle

**Harness Designer is a shaping source, not the finished project repository.**

The subject repository owns its Git identity, remote, history and project files. Harness Designer contributes the minimum foundation and then gets out of the way.

```text
subject repository
      +
Harness Designer seed
      ↓
safe initialization
      ↓
subject-specific minimum harness
      ↓
real work
      ↓
observe friction / repetition / discoveries
      ↓
classify → test → promote / revise / retire
      ↓
more specialized working environment
```

## Initialization modes

### Existing subject repository — recommended

If the project already exists:

1. Open or clone the **subject repository**.
2. Give the agent access to Harness Designer as a temporary source, or tell it to fetch/clone Harness Designer temporarily.
3. The repository initializer preserves the subject `.git`, origin, history, README, license and existing project files.
4. It imports only the minimum harness foundation.
5. It validates the resulting repository and removes temporary Harness Designer material.
6. Initialization changes remain uncommitted and unpushed unless explicitly requested otherwise.

### Started from a Harness Designer clone

This is also supported. If the user later identifies a different repository as the actual subject, the agent must treat the Harness Designer clone as temporary shaping material and establish the subject repository as the sole project Git repository before continuing.

Harness Designer's `.git` directory, remote and history must not become the subject repository's identity.

### New subject with no repository yet

Establish the intended subject repository first, then import the minimum seed. Do not silently make `Wolfrine/Harness_Designer` the new project's upstream repository.

## Subject bootstrap

After repository identity is correct:

1. A new agent session reads `AGENTS.md`.
2. The bootstrap skill asks a few adaptive, high-information questions about the objective and current situation.
3. The agent records only the minimum useful subject model and creates the smallest harness needed to begin.
4. Real work starts.
5. As work continues, durable patterns can become knowledge, instructions, skills, hooks, evaluations, tools, specialist agents, loops or state.
6. Harness changes are reviewed for value, duplication and staleness instead of accumulating forever.

The subject can be known while the objective remains in bootstrap. Do not invent objective details merely to complete setup.

## Repository structure

```text
AGENTS.md                  Agent entrypoint and minimal operating contract
.harness/
  manifest.yaml            Current harness identity and maturity
  objective.md             Evolving statement of objective and constraints
  architecture.md          Placement and repository-identity rules
  evolution/README.md      Candidate → active → retired lifecycle
skills/
  repository-initializer/  Safely shapes the actual subject repository
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

## Philosophy

The seed should stay small. Do not preload dozens of generic skills or rules. Specialization should be earned through the objective and actual work.

Lifecycle hooks are contracts rather than platform-specific configuration. Adapters can map them into Codex, Claude Code, Cursor or another runtime when native hook behavior is useful.

The project should evolve from evidence gathered through real usage, including comparison against mature harnesses and feedback from people starting new subjects from this seed.
