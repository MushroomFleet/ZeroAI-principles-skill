# ZeroAI Principles — Grounding Document

> A methodology for software development built on 100% AI-assisted implementation, with humans holding the loop at the level of direction and planning approval only.

---

## Overview

ZeroAI is a development philosophy, not a framework or library. It defines how AI and human intelligence are divided across a software project — AI does the building, humans decide what gets built and whether it meets the standard. The system produced is zero-data by design: no user accounts, no server-side session tracking, no behavioural telemetry. Everything the user needs lives on their own machine.

This document captures the five governing rules that define ZeroAI-compliant software. Any project claiming to follow this methodology must be able to defend each feature against these rules.

---

## The Five Governing Principles

---

### Principle 1 — AI is infrastructure, not a product feature

AI capabilities are implementation details, not selling points.

A ZeroAI system does not advertise, surface, or expose its AI components to end users. There are no chat interfaces, no "Ask AI" buttons, no generative content surfaces in the public-facing product. AI runs beneath the experience — improving quality, accelerating generation, or performing classification — but the user interacts only with the result, never the mechanism.

This keeps the product defined by what it *does for the user*, not by what technology it uses.

**In practice:**
- No AI interaction surfaces are visible to public users
- AI output is rendered as normal product content, not labelled as AI-generated
- The presence or absence of AI is irrelevant to the user's mental model of the product

---

### Principle 2 — The system must function without AI

AI is used where it adds quality. It is never load-bearing infrastructure.

Every feature in a ZeroAI system must have a non-AI fallback path. If an LLM endpoint is unavailable, rate-limited, deprecated, or simply too expensive to call, the system continues operating. The user sees no degradation. AI enhances the experience; it does not define it.

This principle protects the system from vendor lock-in, API instability, and cost unpredictability. It also forces cleaner architecture — AI logic is isolated, not woven through core functionality.

**In practice:**
- Every AI-dependent function has a documented fallback implementation
- AI calls are wrapped so failures are caught and handled gracefully
- Core data, layout, and navigation never depend on a successful AI response

**Exception handling:** Where a feature genuinely cannot be reasonably implemented without AI, this dependency must be explicitly documented, justified by technical necessity, and isolated so it can be replaced independently of the surrounding system.

---

### Principle 3 — Users do not control AI

AI governance belongs to the system operator, not the public.

No public-facing interface exposes an AI interaction surface. Visitors do not prompt, instruct, or steer AI systems. All AI configuration, triggering, and evaluation is done by the operator or developer — either in the admin layer or hardcoded as part of the build process.

This prevents prompt injection, misuse, unexpected costs, and the reputational risk of generative content appearing under the product's name without review.

**In practice:**
- No input field, button, or control gives public users influence over AI behaviour
- AI features triggered by user actions (e.g. search, filtering) are governed by fixed, operator-defined prompts
- Admin-only AI surfaces are access-controlled and never exposed to unauthenticated requests

---

### Principle 4 — Zero Data: no user data enters AI systems

The system collects nothing. Nothing can be misused.

ZeroAI products require no user login. There are no accounts, no server-side sessions, no behavioural tracking, no persistent identity. Any preferences or state the user generates are stored client-side — in `localStorage`, `IndexedDB`, or equivalent browser-native storage — and never transmitted to any server, AI endpoint, or third-party service.

This is the Zero Data principle: the product operates fully without collecting, storing, or relying on user data.

**In practice:**
- No sign-in is required for any public-facing feature
- All personalisation and preference state lives in client-side storage only
- Client-side data is never sent to AI or LLM endpoints
- No analytics, session recording, or fingerprinting of user behaviour
- The backend, if one exists, holds only content and configuration — never user data

**Why this matters beyond privacy:** Zero Data eliminates an entire category of architectural complexity. There is no auth system to secure, no database of user records to protect, no GDPR compliance burden for personal data, and no risk of user data appearing in AI training pipelines.

---

### Principle 5 — Humans hold direction and approval, not implementation

The human is in the loop for *what gets built* and *whether it is acceptable*, not for *how it is built*.

In ZeroAI development, AI handles 100% of implementation — writing code, generating assets, drafting content, producing tests. The human role is restricted to two functions: setting direction (deciding what to build and why) and approving outputs (deciding whether the result meets the standard). Humans do not write code, manually edit files, or contribute implementation details.

This is a deliberate discipline. Mixing human and AI implementation introduces inconsistency, breaks the AI's ability to reason about the full codebase, and undermines the speed advantage the methodology provides.

**In practice:**
- All code, configuration, and content is produced by AI
- Human input takes the form of natural language direction, review feedback, and go/no-go decisions
- Planning documents (architecture, feature specs, principles like this one) are the primary human artefact
- Iteration happens through directed AI revision, not manual patching

---

## Summary Table

| Principle | Rule | Human responsibility |
|---|---|---|
| 1 — AI is infrastructure | AI is invisible to users | Approve what surfaces are exposed |
| 2 — Fallback-first | System works without AI | Define acceptable degradation |
| 3 — Operator governs AI | No public AI controls | Set and review all AI prompts |
| 4 — Zero Data | No user data collected or transmitted | Define what counts as user data |
| 5 — Human in the loop | Humans direct, AI implements | All planning and approval decisions |

---

## Compliance Checklist

A feature is ZeroAI-compliant when it can answer **yes** to all of the following:

- [ ] Does this feature work if all AI calls return an error?
- [ ] Is there no AI interaction surface visible to a public user?
- [ ] Does this feature require zero user account or login state?
- [ ] Does no client-side data flow to an AI or external endpoint?
- [ ] Was the implementation produced entirely by AI under human direction?
- [ ] If an AI dependency is unavoidable, is it isolated and documented?

---

## On the Role of This Document

This document is itself a ZeroAI artefact — produced by AI, shaped by human direction, approved by a human before use. It is the planning layer, not the product. The product is what gets built when these principles are held consistently across every decision.

ZeroAI is not about making AI do less. It is about knowing precisely what AI should and should not touch — and being disciplined enough to hold that line.
