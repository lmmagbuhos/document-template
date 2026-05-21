# Oak Drive Document Mapper Skill Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build the `oak-drive-document-mapper` Codex skill for converting Docling-extracted Oak Drive document text into master-template JSON.

**Architecture:** Scaffold one user-discoverable skill folder under `$CODEX_HOME/skills` or `~/.codex/skills`. Keep `SKILL.md` concise and move detailed standards into two reference files: one for the DOCX contract and one for business-format guidance.

**Tech Stack:** Codex skill files, Markdown references, generated `agents/openai.yaml`, `skill-creator` validation scripts.

---

### Task 1: Scaffold Skill Folder

**Files:**
- Create: `${CODEX_HOME:-$HOME/.codex}/skills/oak-drive-document-mapper/SKILL.md`
- Create: `${CODEX_HOME:-$HOME/.codex}/skills/oak-drive-document-mapper/references/`
- Create: `${CODEX_HOME:-$HOME/.codex}/skills/oak-drive-document-mapper/agents/openai.yaml`

- [ ] **Step 1: Run the skill initializer**

Run:

```bash
python3 /home/claude-team/.codex/skills/.system/skill-creator/scripts/init_skill.py oak-drive-document-mapper \
  --path "${CODEX_HOME:-$HOME/.codex}/skills" \
  --resources references \
  --interface display_name="Oak Drive Document Mapper" \
  --interface short_description="Map Docling text to branded Oak Drive JSON" \
  --interface default_prompt="Use $oak-drive-document-mapper to convert this Docling-extracted document text into Oak Drive master-template JSON."
```

Expected: the skill folder exists with `SKILL.md`, `references/`, and `agents/openai.yaml`.

### Task 2: Add Reference Files

**Files:**
- Create: `${CODEX_HOME:-$HOME/.codex}/skills/oak-drive-document-mapper/references/master-template-contract.md`
- Create: `${CODEX_HOME:-$HOME/.codex}/skills/oak-drive-document-mapper/references/business-format-standards.md`

- [ ] **Step 1: Write the master template contract**

Include the exact JSON keys from `resources/extracted/templates/master-file/structure.md`, the rule that all keys are mandatory, and the rule that unknown values are empty strings.

- [ ] **Step 2: Write condensed business standards**

Include document-type structures for policy, memo, SOP/procedure, advisory/announcement, and general fallback, plus concise editorial rules from the business-format research files.

### Task 3: Write SKILL.md

**Files:**
- Modify: `${CODEX_HOME:-$HOME/.codex}/skills/oak-drive-document-mapper/SKILL.md`

- [ ] **Step 1: Replace scaffolded content**

Write YAML frontmatter with only `name` and `description`.

- [ ] **Step 2: Add workflow**

Add a short procedure: inspect source, extract metadata, classify type, load references if needed, write `body_content`, validate JSON, output JSON only.

- [ ] **Step 3: Add validation checklist**

Require all master-template keys, no invented metadata, valid JSON escaping, and no Markdown fences.

### Task 4: Validate Skill

**Files:**
- Validate: `${CODEX_HOME:-$HOME/.codex}/skills/oak-drive-document-mapper`

- [ ] **Step 1: Run quick validation**

Run:

```bash
python3 /home/claude-team/.codex/skills/.system/skill-creator/scripts/quick_validate.py "${CODEX_HOME:-$HOME/.codex}/skills/oak-drive-document-mapper"
```

Expected: validation succeeds.

- [ ] **Step 2: Inspect key files**

Run:

```bash
find "${CODEX_HOME:-$HOME/.codex}/skills/oak-drive-document-mapper" -maxdepth 3 -type f | sort
```

Expected: only skill files and references needed for the workflow are present.
