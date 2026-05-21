# Oak Drive Document Mapper Skill Design

## Purpose

Create a Codex skill that converts raw Docling-extracted text from Oak Drive Ventures documents into a flat JSON object that maps directly to the company's branded master DOCX template.

The master template is the stable branded paper shell. The skill's job is to extract metadata, classify the document type, professionally rewrite the body, and emit template-native JSON keys.

## Source Artifacts

- Master template: `resources/templates/docx/MASTER_FILE.docx`
- Extracted template map: `resources/extracted/templates/master-file/structure.md`
- Business format references:
  - `resources/samples/pdf/exa-business-format-deep.md`
  - `resources/samples/pdf/firecrawl-business-format-deep.md`
  - `resources/samples/pdf/perplexity-business-format-deep.md`
  - `resources/samples/pdf/tavily-business-format-deep.md`

## Output Contract

The skill must always output a valid JSON object only. It must not include Markdown fences, comments, explanations, or summary text.

The JSON keys must match the actual DOCX handlebars:

```json
{
  "document_title": "",
  "document_number": "",
  "department": "",
  "supersedes": "",
  "effective_date": "",
  "body_content": "",
  "prepared_by_name": "",
  "prepared_by_role": "",
  "approved_by_name": "",
  "approved_by_role": "",
  "approval_date": ""
}
```

All keys are mandatory. Unknown or missing source values must be emitted as empty strings, not invented placeholders.

## Document-Type Router

The skill must classify the raw Docling input before writing `body_content`.

Supported v1 document types:

- Policy
- Memo / internal memorandum
- SOP / procedure
- Advisory / announcement
- General corporate document fallback

Classification should use source clues such as title, header labels, section names, language patterns, and signatory blocks. If the type is ambiguous, choose the closest business format and preserve source meaning.

## Body Structures

`body_content` is the adaptive part of the JSON. It must be professionally edited and structured according to document type.

Policy:

```text
1.0 Objective / Purpose
2.0 Scope and Coverage
3.0 Policy Guidelines
4.0 Roles and Responsibilities
5.0 Compliance and Accountability
```

Memo:

```text
1.0 Purpose / Bottom Line
2.0 Background
3.0 Key Details
4.0 Required Action / Next Steps
5.0 Closing Notes
```

SOP / Procedure:

```text
1.0 Objective
2.0 Scope
3.0 Procedure
4.0 Roles and Responsibilities
5.0 Records, Exceptions, and Compliance
```

Advisory / Announcement:

```text
1.0 Purpose
2.0 Summary
3.0 Details
4.0 Impacted Parties
5.0 Effective Date / Next Steps
```

General corporate document:

```text
1.0 Purpose
2.0 Scope or Audience
3.0 Main Content
4.0 Responsibilities or Action Items
5.0 Compliance / Follow-Up
```

## Editorial Rules

The skill must act as an executive editor:

- Preserve the source document's meaning and obligations.
- Repair Docling extraction artifacts, including broken words, erratic line breaks, repeated headers or footers, and stray symbols.
- Use institutional, professional language.
- Keep policies in third person and rule-based voice.
- Use BLUF-style directness for memos and announcements.
- Use ordered steps for SOP procedures.
- Use bullet points (`•`) for grouped unordered items.
- Use lettered or numbered lists for ordered items.
- Separate major sections and paragraphs with double line breaks (`\n\n`).
- Avoid legal or compliance details not present in the source.
- Avoid adding names, dates, policy numbers, departments, or approvals that are not present in the source.

## Extraction Rules

The skill must extract these fields from the source when available:

- `document_title`: clean document title
- `document_number`: formal document or policy number
- `department`: issuing department or originating unit
- `supersedes`: replaced document reference, or `""`
- `effective_date`: effective or activation date
- `prepared_by_name`: prepared-by signatory name
- `prepared_by_role`: prepared-by job title
- `approved_by_name`: approved-by signatory name
- `approved_by_role`: approved-by job title
- `approval_date`: approval or sign-off date

If a label is present but the value is blank, preserve it as `""`. If multiple candidate values exist, prefer the value closest to the document-control header or final approval block.

## Skill Contents

Recommended skill name: `oak-drive-document-mapper`.

Recommended location: `$CODEX_HOME/skills`, falling back to `~/.codex/skills` if `CODEX_HOME` is unset.

Recommended contents:

- `SKILL.md`: concise workflow, routing rules, output contract, and validation checklist.
- `references/business-format-standards.md`: condensed standards from the four business-format research files.
- `references/master-template-contract.md`: template tags, JSON schema, and notes from `MASTER_FILE.docx`.
- `agents/openai.yaml`: generated UI metadata.

No script is required for v1 because the task is primarily editorial transformation. A validation script can be added later if the workflow expands into automated JSON validation or DOCX rendering.

## Validation

Before considering the skill ready:

- Run the skill validator on the skill folder.
- Confirm frontmatter has only `name` and `description`.
- Confirm all required JSON keys appear in the skill instructions.
- Confirm the skill says to output JSON only.
- Confirm missing source values become empty strings.
- Confirm the skill distinguishes policy, memo, SOP, advisory, and fallback body structures.

## Implementation Decision

Create the skill in the user-discoverable Codex skills path by default: `$CODEX_HOME/skills`, falling back to `~/.codex/skills` when `CODEX_HOME` is unset. Use a repo-local skill only if the user explicitly requests it before implementation.
