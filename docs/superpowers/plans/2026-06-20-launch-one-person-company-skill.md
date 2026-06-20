# launch-one-person-company Skill Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build the `launch-one-person-company` Codex skill in this repository, with a concise `SKILL.md` and reference templates for generating OPC launch readiness packs.

**Architecture:** Use a workflow-oriented skill with `SKILL.md` as the entrypoint and one-level `references/` files for intake, archetypes, decision support, output contract, U.S. external SOPs, tool substitutes, social account operations, risk classification, and validation scenarios. Do not add automation scripts in the first version.

**Tech Stack:** Markdown skill instructions, YAML skill frontmatter, `skill-creator` initialization and validation scripts.

---

### Task 1: Initialize Skill Folder

**Files:**
- Create: `launch-one-person-company/SKILL.md`
- Create: `launch-one-person-company/agents/openai.yaml`
- Create: `launch-one-person-company/references/`

- [ ] **Step 1: Run `init_skill.py`**

```bash
python3 /Users/pepc/.codex/skills/.system/skill-creator/scripts/init_skill.py launch-one-person-company \
  --path /Users/pepc/Documents/Hackthon-OPC \
  --resources references \
  --interface display_name="Launch One-Person Company" \
  --interface short_description="Plan an OPC launch readiness pack" \
  --interface default_prompt="Use $launch-one-person-company to turn my one-person company idea into a launch readiness pack."
```

Expected: `launch-one-person-company/` exists with `SKILL.md`, `agents/openai.yaml`, and `references/`.

### Task 2: Write Skill Entrypoint

**Files:**
- Modify: `launch-one-person-company/SKILL.md`

- [ ] **Step 1: Replace template with final skill instructions**

`SKILL.md` must include:

- YAML frontmatter with only `name` and `description`.
- Trigger description covering OPC, one-person company, solo founder, solopreneur, AI/software/productized service/consulting/digital product launch requests.
- A guided workflow from intake to launch-pack generation.
- Mandatory official-source research rules for U.S. external SOPs.
- Local blocking rules for high-risk uncertainty.
- Reference loading rules.
- Output location and language behavior.

### Task 3: Add Reference Templates

**Files:**
- Create: `launch-one-person-company/references/intake.md`
- Create: `launch-one-person-company/references/archetypes.md`
- Create: `launch-one-person-company/references/decision-support.md`
- Create: `launch-one-person-company/references/output-contract.md`
- Create: `launch-one-person-company/references/us-external-sop.md`
- Create: `launch-one-person-company/references/tool-substitutes.md`
- Create: `launch-one-person-company/references/social-account-ops.md`
- Create: `launch-one-person-company/references/risk-classification.md`
- Create: `launch-one-person-company/references/validation-scenarios.md`

- [ ] **Step 1: Write each reference file**

Each reference must be concise, self-contained, and directly linked from `SKILL.md`. No reference should require nested resource loading.

### Task 4: Validate Skill

**Files:**
- Validate: `launch-one-person-company/`

- [ ] **Step 1: Run official validator**

```bash
python3 /Users/pepc/.codex/skills/.system/skill-creator/scripts/quick_validate.py /Users/pepc/Documents/Hackthon-OPC/launch-one-person-company
```

Expected: validation passes.

- [ ] **Step 2: Run content checks**

```bash
rg -n "TODO|TBD|FIXME|PLACEHOLDER|\\?\\?" /Users/pepc/Documents/Hackthon-OPC/launch-one-person-company
```

Expected: no matches.

```bash
find /Users/pepc/Documents/Hackthon-OPC/launch-one-person-company -maxdepth 3 -type f | sort
```

Expected: `SKILL.md`, `agents/openai.yaml`, and all nine reference files exist.

### Task 5: Commit

**Files:**
- Stage: `launch-one-person-company/`
- Stage: `docs/superpowers/plans/2026-06-20-launch-one-person-company-skill.md`

- [ ] **Step 1: Review git diff**

```bash
git diff -- launch-one-person-company docs/superpowers/plans/2026-06-20-launch-one-person-company-skill.md
```

Expected: only the planned skill and plan files changed.

- [ ] **Step 2: Commit implementation**

```bash
git add launch-one-person-company docs/superpowers/plans/2026-06-20-launch-one-person-company-skill.md
git commit -m "Add launch one-person company skill"
```

Expected: commit succeeds on branch `codex/create-opc-skill`.
