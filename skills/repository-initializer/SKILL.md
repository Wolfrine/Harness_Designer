---
name: repository-initializer
description: Safely initialize Harness Designer into a new or existing subject repository while preserving the subject repository as the sole Git project and treating Harness Designer only as temporary shaping material.
---

# Repository Initializer

Use this skill before subject bootstrap when Harness Designer is being applied to another repository or when repository ownership is not yet established.

## Goal

Establish the correct project repository first, then import only the minimum Harness Designer foundation without replacing project identity or history.

## 1. Determine initialization mode

Classify the workspace into one of these modes:

### Existing subject repository

The user already has a repository locally or provides an existing repository/remote. That repository owns the project.

### New subject repository

The subject is new and no project repository exists yet. Establish the intended project repository before importing the harness. Harness Designer itself should not silently become the project's upstream repository.

### Already initialized subject repository

A `.harness/manifest.yaml` and subject-specific harness already exist. Do not reinstall the seed; continue evolving the existing harness.

If repository ownership cannot be safely inferred, ask one focused question before changing Git metadata.

## 2. Establish source and target

Treat these as separate roles:

- **Target:** the subject repository that owns `.git`, origin/remotes, history and future project commits.
- **Source:** Harness Designer, used only to supply shaping logic and minimum seed files.

A temporary Harness Designer clone may be used as the source, including when the user started by cloning Harness Designer first. Its `.git` directory and remotes must never be copied into the target.

## 3. Preserve existing repository identity

For an existing subject repository:

1. Verify the Git root and current origin/remotes.
2. Preserve `.git`, remote configuration and history.
3. Preserve existing README, license and project-specific files. Merge harness guidance rather than overwriting project identity documents unnecessarily.
4. Do not create a nested Git repository inside the subject repository.
5. Do not rewrite history or repoint origin to Harness Designer.

If the target repository needs to be cloned, clone/fetch the target first and verify that its origin is the intended subject remote before importing harness files.

## 4. Import the minimum foundation

Bring in only the seed components needed to begin:

- `AGENTS.md` or an integrated equivalent;
- `.harness/` foundation;
- core bootstrap/harness-design/review skills;
- repository initializer while initialization remains relevant;
- lifecycle hook contracts;
- lightweight templates that are actually useful.

Do not copy Harness Designer's `.git` directory. Do not copy repository-identity files merely because they exist in the seed.

When file names collide with subject files, preserve the subject content and integrate only the necessary harness behavior.

## 5. Initialize subject state conservatively

Set the concise subject identity when known.

If the user has not yet provided enough objective context, keep:

```yaml
stage: bootstrap
objective_status: uninitialized
```

or the closest existing bootstrap state. Knowing the subject name is not sufficient reason to invent or prematurely finalize its objective.

## 6. Validate before finishing

Verify at minimum:

- there is exactly one intended project Git root;
- the target origin/remotes still point to the subject repository;
- existing history remains reachable;
- the subject README/license and existing project files remain intact unless intentionally edited;
- no Harness Designer `.git` directory is inside the target;
- no temporary Harness Designer clone remains inside the project after setup;
- `.harness/manifest.yaml` names the subject appropriately;
- objective state reflects only what is actually known;
- `git status` shows only intended initialization changes.

Use repository-native validation commands when available, for example `git rev-parse --show-toplevel`, `git remote -v`, `git log -1` and `git status`.

## 7. Cleanup and mutation policy

Remove temporary Harness Designer material after the minimum foundation has been imported and validated.

By default, leave initialization changes **uncommitted and unpushed** so the user can inspect them. Commit or push only when explicitly requested.

## Success condition

Initialization is successful when Harness Designer has disappeared as a repository identity and what remains is unmistakably the user's subject repository with a minimal harness foundation ready for bootstrap and future evolution.
