---
name: visual-design-director
description: Use when UI/UX visual quality, layout, styling, brand expression, motion, screen composition, or visual judgment materially affects the user's outcome. Separates art direction from implementation QA and routes Chat, Work, Codex, Figma and browser evidence appropriately.
---

# Visual Design Director

This is a portable visual-workflow skill. Prefer a subject-specific design contract when one exists; this skill supplies the invariant process.

## Trigger

Use for:
- new or redesigned UI surfaces;
- visual-quality or "premium/exquisite/distinctive" requests;
- brand/landing/onboarding/showcase work;
- meaningful layout, typography, imagery or motion decisions;
- owner/user rejection of the current visual direction.

For a deterministic bug or minor change inside an already accepted pattern, use bounded visual QA instead of the full direction process.

## Invariant separation

Never collapse these into one score:

1. **Art direction / visual quality**
2. **Implementation / usability / technical QA**

Fixing overflow, focus, accessibility, state bugs or tests can unblock release but cannot make the art direction visually better by itself.

## Direction process

1. Define the product object, user job, exact state and visual thesis.
2. Record expected perception at roughly 100 ms, 1 second and 5 seconds.
3. Declare the product-critical visual dimensions before seeing scores.
4. Inspect 3–6 relevant strong references as actual images/frames/recordings plus the current/rejected baseline.
5. Keep those visuals available; do not reduce them to prose-only lessons.
6. For high-ambition work, create at least three materially different visual directions before production implementation.
7. Compare candidates side-by-side with references. If none is credible, re-derive rather than picking the least bad.
8. Use a separate visual critic/creative-director pass that ignores functional correctness while judging composition, hierarchy, identity, typography/material, imagery, perceptual effect, motion concept and responsive translation.
9. If a critical visual dimension stalls for two rounds, reset the direction instead of continuing cosmetic polish.
10. Only then implement and run separate UI QA.

## Tool/runtime routing

- **Chat:** reasoning, orchestration, critique of visible images, bounded deterministic repo changes. No code/prose-only visual acceptance.
- **Work:** multi-step current-reference research, flow capture, cross-screen audit, art-direction packs and broader discovery.
- **Codex:** repository implementation, running the product, browser evidence, interaction/responsive testing and iterative corrections.
- **Figma:** optional visual exploration/collaboration canvas. Never a quality guarantee.
- **Browser/screenshots:** evidence of rendered reality, not a taste engine.
- **Generators/component libraries/site builders:** execution aids only. Do not let their defaults define art direction unless deliberately selected after the direction gate.

## Handoff to implementation

Pass only:
- chosen direction visuals;
- perception/intent packet;
- matched references and baseline;
- retain/avoid decisions;
- product/data constraints;
- required states/viewports.

Do not bury the implementation agent in a design-document dump.

## Visual critic questions

Before scoring, answer:

- Where does the eye land immediately?
- What is understood before reading?
- What remains memorable after a few seconds?
- What visual idea belongs specifically to this product?
- Which three decisions look most generic or amateur?
- What do the matched references visibly do better?
- Does mobile preserve the visual idea rather than merely stack desktop?
- Did this round improve pixels, or only behavior/code?

Functional correctness must not influence visual scores.

## Final gate

Do not claim visual completion unless:
- current renders exist;
- visual comparison used actual matched references and the rejected/current baseline;
- each declared critical visual dimension passes independently;
- the independent visual critic and parent/lead both accept the exact candidate;
- separate implementation/QA verification passes.

A build, browser test, Figma frame, completed iteration count, or overall average is insufficient on its own.
