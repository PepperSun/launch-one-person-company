# OPC Action Map Skill Update Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Update `launch-one-person-company` so it asks unresolved questions through option UI and defaults to a concise action-map playbook before generating detailed execution files.

**Architecture:** Keep the existing skill folder and references. Move the interaction contract into `SKILL.md` and `references/intake.md`, move output behavior into `references/output-contract.md`, and update validation scenarios to catch old long-text behavior.

**Tech Stack:** Markdown skill documentation, Codex `request_user_input` option UI, `quick_validate.py`.

---

### Task 1: Define Popup Intake Rules

**Files:**
- Modify: `/Users/pepc/Documents/Hackthon-OPC/launch-one-person-company/SKILL.md`
- Modify: `/Users/pepc/Documents/Hackthon-OPC/launch-one-person-company/references/intake.md`
- Modify: `/Users/pepc/Documents/Hackthon-OPC/launch-one-person-company/references/decision-support.md`

- [x] Add an operating rule that all user-facing questions must use option UI when available.
- [x] State that if option UI is unavailable, the skill must pause and explain that option UI is required for unresolved questions.
- [x] Rewrite the intake confirmation format from markdown table prompts to option UI prompts with 2-3 choices and an automatic free-form Other path.
- [x] Keep every unresolved field user-confirmed before final generation.

### Task 2: Make Action Map the Default Output

**Files:**
- Modify: `/Users/pepc/Documents/Hackthon-OPC/launch-one-person-company/SKILL.md`
- Modify: `/Users/pepc/Documents/Hackthon-OPC/launch-one-person-company/references/output-contract.md`

- [x] Replace the default "required 12 files" generation behavior with a required `00-action-map.md` preview.
- [x] Define action IDs such as `A01`, `A02`, and `A03`.
- [x] Require each action to include node timing, what to do, where to do it, how to do it, done definition, blocked consequence, next step, risk level, and source links when needed.
- [x] Add a second-stage option UI prompt asking whether to generate execution files and which action IDs to expand.
- [x] Keep detailed files as optional execution-pack outputs selected by action ID.

### Task 3: Enforce Short Playbook Style

**Files:**
- Modify: `/Users/pepc/Documents/Hackthon-OPC/launch-one-person-company/SKILL.md`
- Modify: `/Users/pepc/Documents/Hackthon-OPC/launch-one-person-company/references/output-contract.md`
- Modify: `/Users/pepc/Documents/Hackthon-OPC/launch-one-person-company/references/validation-scenarios.md`

- [x] Require simple, direct language following the user's main language.
- [x] Forbid long explanatory prose in generated artifacts.
- [x] Update pass criteria to require popup-option intake, action-map-first output, second-stage execution selection, and playbook brevity.

### Task 4: Validate, Install, Commit

**Files:**
- Validate: `/Users/pepc/Documents/Hackthon-OPC/launch-one-person-company`
- Sync to: `/Users/pepc/.codex/skills/launch-one-person-company`

- [x] Run `python3 /Users/pepc/.codex/skills/.system/skill-creator/scripts/quick_validate.py /Users/pepc/Documents/Hackthon-OPC/launch-one-person-company`.
- [x] Run placeholder scan with `rg`.
- [x] Sync the skill to `/Users/pepc/.codex/skills/launch-one-person-company`.
- [x] Run `quick_validate.py` on the installed skill.
- [x] Confirm installed and project copies match with `diff -qr`.
- [x] Commit the changed tracked files and the plan.
