# Work From Home Policy Template Context

Status: Draft working notes for future skill creation.

Source reviewed:

- `resources/samples/pdf/[HR-018.1] Work From Home Policy.pdf`
- Rendered page images in `resources/extracted/images/work-from-home-policy/`
- Extracted text in `resources/extracted/text/HR-018.1-work-from-home-policy.txt`

Scope of this note:

- Describe only what is visible or inferable from the provided Work From Home Policy PDF template/sample.
- Do not treat these notes as final DOCX implementation rules until the editable DOCX template is available.

## Document Type

This is a formal company policy document for Oak Drive Ventures, Inc.

The document uses a repeatable policy format with:

- policy metadata at the top of every page;
- company logo at the top-right of every page;
- a thick horizontal divider below the header;
- numbered policy sections;
- plain body paragraphs;
- bullet lists;
- lettered sublists;
- a simple approval table;
- prepared by / approved by signature blocks.

## Page Setup

The PDF is a 4-page letter-size document.

Observed PDF properties:

- Page size: 612 x 792 points, equivalent to US Letter.
- Orientation: portrait.
- Pages: 4.
- Source title metadata suggests it was exported from `[HR-018.1] Work From Home Policy.docx`.

The visual layout appears to use standard business-document margins, with a wide text column and substantial whitespace at the bottom when content does not fill the page.

## Header Template

Every page repeats the same header.

Left side header fields:

- `Policy Title: Work From Home Policy`
- `Policy Number: HR-018.1`
- `Issuing Department: HR and Admin`
- `Supersedes: HR-018`
- `Effective Date: May 4, 2026`

Header styling:

- Labels are regular weight.
- The policy title value is bold.
- Header text appears black and left-aligned.
- The header uses compact line spacing.

Right side header:

- Oak Drive Ventures, Inc. logo is placed near the upper-right.
- Logo is small compared with page width.
- Logo is vertically aligned with the metadata block.

Divider:

- A thick black horizontal rule spans across most of the content width below the header.
- The rule separates the repeated metadata/logo header from the policy body.

Template implication:

- The editable DOCX should likely implement this as a repeated page header, not manually inserted at the top of each page.
- The policy metadata should become document variables/placeholders.

## Body Typography

The document appears to use a clean sans-serif font, likely similar to Arial or Helvetica.

Observed hierarchy:

- Main numbered headings are bold, black, and larger/heavier than body text.
- Subsection headings such as `3.1`, `3.2`, `3.3`, and `3.4` are also bold.
- Unnumbered subheadings such as `Guidelines and Conditions`, `Approval Process`, `Work Hours and Timekeeping`, `Availability and Responsiveness`, and `Operational Readiness and Connectivity` are bold.
- Body paragraphs are regular weight, black, and left-aligned.

Paragraph behavior:

- Body text is justified or near-justified in several areas.
- Paragraphs have visible spacing between blocks.
- No decorative color treatment appears in the body content.
- The template is conservative and policy-oriented rather than marketing-oriented.

## Section Structure

The policy follows this top-level structure:

- `1.0 Policy Objective`
- `2.0 Scope and Coverage`
- `3.0 Procedures and Guidelines`
- `4.0 Compliance and Accountability`
- `5.0 Related Policies`

Nested numbered sections under section 3:

- `3.1 Eligibility and Work Arrangements`
- `3.2 Work Standards and Work Expectations`
- `3.3 Roles and Responsibilities`
- `3.4 Approval, Review, and Revocation`

Template implication:

- The future DOCX template should support policy documents with required metadata and ordered sections.
- Section numbers should be content-driven or style-driven, but the final output must preserve this numbering pattern.

## Lists

The template uses two list styles.

Bullet lists:

- Solid black round bullets.
- Indented under the preceding paragraph.
- Wrapped lines align under the list text, not under the bullet.
- Used for examples, conditions, and requirement lists.

Lettered lists:

- Lowercase letters followed by periods, such as `a.`, `b.`, `c.`
- Used for procedural or compliance subpoints.
- Wrapped lines align with the lettered item text.

Template implication:

- The future skill should preserve real DOCX list styles instead of inserting plain text bullets whenever possible.

## Table Style

The document contains a centered approval table on page 2.

Table characteristics:

- 2 columns.
- Header row is bold.
- Visible black borders around all cells.
- No background shading.
- Table is narrower than the body text width and centered on the page.
- Column headings:
  - `Employee Level`
  - `Approving Authority`

Template implication:

- The DOCX template should include a reusable simple bordered table style for approval matrices.

## Signature Blocks

The final page includes two signature blocks near the lower portion of the content area.

Left block:

- Label: `Prepared by:`
- Signature image above the name.
- Name in bold: `Red F. Fernandez`
- Role/title below: `HR Business Partner`

Right block:

- Label: `Approved by:`
- Signature image above/near the name.
- Date appears near the signature: `April 30, 2026`
- Name in bold: `Charlene G. Mago`
- Role/title below: `Assistant Manager, Executive Office`

Template implication:

- Signature blocks should be placeholders, likely arranged in a two-column layout.
- The template may need fields for prepared-by name, prepared-by title, approved-by name, approved-by title, approval date, and signature images.

## Branding

Visible brand elements:

- Oak Drive Ventures, Inc. logo in the header.
- The logo includes a tree-like mark and warm brown/orange wordmark.
- The document itself does not use colored headings, tinted rules, watermarks, or decorative page elements.
- Branding is restrained and mostly expressed through the logo and formal layout consistency.

Template implication:

- The output skill should preserve the logo placement and business-policy layout rather than inventing extra brand decoration.

## Content Placeholders To Consider

Likely metadata placeholders:

- `policy_title`
- `policy_number`
- `issuing_department`
- `supersedes`
- `effective_date`

Likely body placeholders:

- `policy_objective`
- `scope_and_coverage`
- `procedures_and_guidelines`
- `compliance_and_accountability`
- `related_policies`

Likely approval/signature placeholders:

- `prepared_by_name`
- `prepared_by_title`
- `prepared_by_signature`
- `approved_by_name`
- `approved_by_title`
- `approved_by_signature`
- `approval_date`

## Open Questions For DOCX Finalization

- Should the future DOCX template be a strict policy-only template, or a more general formal-document template?
- Should every generated policy always include sections 1.0 through 5.0?
- Should policy metadata appear in a true DOCX header on every page?
- Should signatures be manually supplied images, typed names only, or optional placeholders?
- Should the skill generate DOCX only, or DOCX plus exported PDF?
- Should the agent be allowed to condense or split content to avoid awkward page breaks?

## Proposed DOCX Template Creation Method

Goal:

- Create an editable DOCX template that visually matches the provided Work From Home Policy PDF as closely as possible.
- Use the DOCX template later as the stable branded layout for generated policy documents.

Important constraint:

- A PDF sample is useful for visual reconstruction, but it is not the same as the original editable DOCX.
- The highest-fidelity path is to obtain the original DOCX that produced the PDF.
- If the original DOCX is unavailable, recreate the template manually and verify it by exporting the recreated DOCX to PDF, then comparing that output against the provided PDF.

Recommended path:

1. Use the original DOCX if it can be provided.
2. If only the PDF is available, reconstruct the DOCX template from the rendered PDF pages.
3. Insert actual brand assets, starting with the Oak Drive logo in `resources/brand/logos/`.
4. Export the reconstructed DOCX to PDF.
5. Compare the generated PDF against the sample PDF page by page.
6. Tune margins, header size, logo size, typography, paragraph spacing, table width, and signature layout until the visual match is acceptable.

Template implementation choices:

- Use US Letter portrait page setup.
- Use a true repeated DOCX header for the policy metadata, logo, and horizontal divider.
- Use structured placeholders for policy metadata.
- Use Word paragraph styles for headings, body text, bullets, lettered lists, table text, and signature text.
- Use a reusable bordered table style for approval matrices.
- Use a two-column signature block near the end of the document.

Likely placeholder syntax:

- Use double braces for text placeholders, such as `{{ policy_title }}`.
- Use explicit image placeholders for signatures if needed, such as `{{ prepared_by_signature }}`.
- Keep placeholders human-readable so the DOCX remains understandable when opened manually.

Initial template placeholders:

- `{{ policy_title }}`
- `{{ policy_number }}`
- `{{ issuing_department }}`
- `{{ supersedes }}`
- `{{ effective_date }}`
- `{{ policy_objective }}`
- `{{ scope_and_coverage }}`
- `{{ procedures_and_guidelines }}`
- `{{ compliance_and_accountability }}`
- `{{ related_policies }}`
- `{{ prepared_by_name }}`
- `{{ prepared_by_title }}`
- `{{ prepared_by_signature }}`
- `{{ approved_by_name }}`
- `{{ approved_by_title }}`
- `{{ approved_by_signature }}`
- `{{ approval_date }}`

Similarity verification:

- Render the recreated DOCX to PDF.
- Render both PDFs to page images.
- Compare each corresponding page visually.
- Use measurable checks where possible:
  - page count;
  - page size;
  - header logo position;
  - header metadata position;
  - horizontal rule position and thickness;
  - body left/right margins;
  - heading and paragraph spacing;
  - table position and dimensions;
  - signature block position.

Expected fidelity:

- With the original DOCX, fidelity should be near exact because the template can be edited directly.
- With PDF-only reconstruction, a very close match is achievable, but exact 100% similarity may require several render/compare/tune passes because Word/PDF export engines can differ in font metrics, line wrapping, and pagination.

## Current Template Draft

Generated DOCX:

- `resources/templates/docx/oak-drive-policy-template.docx`

Generator script:

- `scripts/build_policy_docx_template.py`

Generated supporting asset:

- `resources/brand/logos/oak-drive-logo-trimmed.png`

The current DOCX draft implements:

- US Letter portrait page setup.
- Narrow business-document margins.
- Repeating header with policy metadata placeholders.
- Oak Drive logo placed in the top-right header area.
- Thick black horizontal divider below the header.
- Arial-based body typography.
- Bold heading styles matching the policy sample's conservative black-text hierarchy.
- Placeholder body sections.
- Centered bordered approval table.
- Two-column prepared-by / approved-by signature block.

Current limitation:

- The environment can generate and inspect the DOCX package, but it does not currently have LibreOffice or Microsoft Word available to render the DOCX back to PDF for visual comparison.
- Visual tuning should continue after opening the DOCX in Word or another DOCX renderer and comparing it against the sample PDF.
