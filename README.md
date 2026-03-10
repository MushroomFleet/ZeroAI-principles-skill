# ZeroAI Principles Skill

A Claude skill for assessing codebases and implementation plans against the **ZeroAI methodology** — a software development philosophy built on 100% AI-assisted implementation, zero user data collection, and human involvement limited to direction and approval only.

Install the `.skill` file to give Claude the ability to audit any project and produce a structured `README_ZAI.md` compliance report with scored findings, prioritised recommendations, and concrete implementation steps.

---

## What is ZeroAI?

ZeroAI is a development methodology, not a framework or library. It defines a clear division between AI and human responsibility across a project:

- **AI** handles 100% of implementation — code, configuration, content, tests
- **Humans** hold direction (deciding *what* to build) and approval (deciding *whether it meets the standard*)

The systems produced under ZeroAI are **zero-data by design**: no user accounts, no server-side sessions, no behavioural telemetry. Everything the user needs lives on their own machine via `localStorage`, `IndexedDB`, or equivalent client-side storage.

---

## The Five Governing Principles

### P1 — AI is infrastructure, not a product feature
AI capabilities are implementation details, never selling points. No AI interaction surfaces are visible to end users — no chat boxes, no "Ask AI" buttons, no generative UI. The product is defined by what it does, not what technology powers it.

### P2 — The system must function without AI
Every feature must have a non-AI fallback path. If an LLM endpoint is unavailable, rate-limited, or deprecated, the system continues operating with no visible degradation. AI enhances; it is never load-bearing infrastructure.

### P3 — Users do not control AI
AI governance belongs to the operator, not the public. No public-facing interface allows users to influence AI behaviour. All AI prompts are operator-defined and hardcoded — never exposed to unauthenticated input.

### P4 — Zero Data: no user data enters AI systems
No login required. No accounts, server-side sessions, or behavioural tracking. All user state is stored client-side only and never transmitted to any server, AI endpoint, or third-party service. The backend, if it exists, holds only content and configuration — never user data.

### P5 — Humans hold direction and approval, not implementation
The human role is restricted to two functions: setting direction and approving outputs. All code, assets, and content are produced by AI under human direction. Iteration happens through directed revision, not manual patching.

---

## What the Skill Does

When triggered, the skill:

1. **Reads** the full ZeroAI grounding document from its bundled references
2. **Scores** the submitted codebase or plan across all five principles: `Compliant / Partial / Non-Compliant`
3. **Produces** a `README_ZAI.md` file containing:
   - An overall compliance rating and summary
   - Principle-by-principle findings
   - A compliance checklist
   - Prioritised recommendations (Non-Compliant issues first)
   - Implementation steps with working code for every fix

---

## Installation

1. Download `zeroai-principles.skill` from this repository
2. In Claude.ai, go to **Settings → Skills** and install the `.skill` file
3. The skill activates automatically when relevant trigger phrases are detected

---

## Usage

Submit any codebase, architecture document, GDD, or implementation plan and use any of the following trigger phrases:

- *"using ZeroAI principles"*
- *"ZeroAI assessment"*
- *"assess against ZeroAI"*
- *"check ZeroAI compliance"*
- *"zero data compliance check"*
- *"human-in-loop review"*

Claude will read the submission, score it, and write `README_ZAI.md` directly to the workspace.

---

## Skill Contents

```
zeroai-principles/
├── SKILL.md                              — trigger metadata + assessment workflow
└── references/
    └── ZeroAI-Principles-grounding.md   — full principles definition and compliance checklist
```

---

## Compliance Checklist

A feature is ZeroAI-compliant when it answers **yes** to all of the following:

- [ ] Does this feature work if all AI calls return an error?
- [ ] Is there no AI interaction surface visible to a public user?
- [ ] Does this feature require zero user account or login state?
- [ ] Does no client-side data flow to an AI or external endpoint?
- [ ] Was the implementation produced entirely by AI under human direction?
- [ ] If an AI dependency is unavoidable, is it isolated and documented?

---

## License

MIT

---

## 📚 Citation

### Academic Citation

If you use this codebase in your research or project, please cite:

```bibtex
@software{ZeroAI_principles_skill,
  title = {ZeroAI Principles Skill: Claude skill for assessing codebases and implementation plans against the ZeroAI methodology},
  author = {[Drift Johnson]},
  year = {2025},
  url = {https://github.com/MushroomFleet/ZeroAI-principles-skill},
  version = {1.0.0}
}
```

### Donate:

[![Ko-Fi](https://cdn.ko-fi.com/cdn/kofi3.png?v=3)](https://ko-fi.com/driftjohnson)
