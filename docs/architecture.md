# WeldVireo — proposed AWS architecture

WeldVireo uses AWS to read inspection documents, organise traceable quality records and keep every project’s evidence secure.

## Request flow

1. Inspection reports
2. Amazon S3
3. Textract
4. Bedrock
5. Inspector review
6. DynamoDB
7. Project dossier

## Services

### Amazon Textract

**Role:** Read inspection reports

Extracts weld IDs, results, defect descriptions, tables and signatures from scanned and digital inspection reports.

### Amazon Bedrock

**Role:** Classify defects and summarise

Classifies recorded defect descriptions into standard categories, links them to welds and drafts weekly quality summaries for inspectors to edit.

### Amazon S3

**Role:** Archive inspection evidence

Keeps original reports, films metadata and dossiers encrypted and versioned for the life of the asset.

### Amazon DynamoDB

**Role:** Hold welds, findings and tasks

Stores welds, welders, procedures, findings, repairs and sign-offs for fast traceability queries.

### AWS Lambda

**Role:** Process reports and build dossiers

Orchestrates extraction and classification, updates trends and generates project dossiers on request.

## Principles

- **Inspectors decide** — Acceptance remains with qualified inspectors.
- **Traceable to source** — Every finding links to its report page.
- **Lifetime records** — Evidence is kept for the life of the asset.

## Safeguards

- **Qualified inspectors decide** — Classifications are suggestions until a qualified inspector confirms them; acceptance stays with them.
- **Records, not testing** — WeldVireo organises inspection records; it does not perform NDT or assess structural integrity.
- **Source-linked** — Every finding links back to its original report.
- **Project confidentiality** — Encrypted, access-controlled and separated per client and project.

## MVP scope

For one project or system, we digitise inspection reports, classify recorded defects for inspector review, and deliver defect trend reports and a draft dossier.

- Inspection report upload
- Extraction and defect classification
- Inspector review queue
- Quality trend report
- Draft project dossier
