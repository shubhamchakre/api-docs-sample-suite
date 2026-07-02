# Documentation Design Decisions

This document explains the information architecture, audience analysis, and tooling choices behind the Acme Payments API documentation suite — a **personal portfolio project** published at [github.com/shubhamchakre/api-docs-sample-suite](https://github.com/shubhamchakre/api-docs-sample-suite).

## Problem statement

Developers integrating a payments API need more than endpoint lists. They need:

1. A fast path to a working integration (first successful API call)
2. Trust in error handling and edge cases
3. Confidence that the API won't break without warning

This project models how to deliver all three in a maintainable, docs-as-code workflow.

## Audience

| Persona | Goal | Primary content |
|---------|------|-----------------|
| **Backend engineer** | Integrate payments in 1–2 sprints | Tutorials, OpenAPI reference, Postman |
| **Tech lead** | Evaluate API design and lifecycle | Guides, changelog, deprecation policy |
| **Support engineer** | Resolve integration failures | Error catalog, webhook event reference |

## Information architecture

Content follows the [Diátaxis](https://diataxis.fr/) framework:

```
docs/
├── getting-started/     → Learning-oriented (onboarding)
├── tutorials/           → Learning-oriented (task walkthroughs)
├── guides/              → Understanding-oriented (concepts)
└── reference/           → Information-oriented (lookup)
```

### Why this split?

- **Getting started** answers "How do I authenticate and make my first call?" in under 10 minutes.
- **Tutorials** are linear, outcome-driven ("Create a payment", "Handle a webhook"). They assume the reader follows steps in order.
- **Guides** explain *why* — idempotency, webhook security, test vs. live mode — without step-by-step instructions.
- **Reference** is optimized for lookup: error codes, changelog, deprecation policy, and API endpoint details.

## API design (fictional)

The Acme Payments API is intentionally realistic for fintech:

- RESTful resources with consistent naming (`/v1/payments`, `/v1/refunds`)
- Idempotency keys on mutating requests
- Cursor-based pagination
- Structured error responses with machine-readable `code` and human-readable `message`
- Webhook events with signature verification
- Test and live mode separation via API key prefix (`sk_test_` / `sk_live_`)

## OpenAPI as source of truth

The OpenAPI 3.1 spec (`openapi/acme-payments-api.yaml`) defines:

- All endpoints, parameters, request/response schemas
- Reusable components (`Payment`, `Refund`, `Error`, `Pagination`)
- Example payloads for documentation generators and Postman

Narrative docs (tutorials, guides) supplement the spec with context the spec cannot capture: business rules, recommended flows, and troubleshooting.

## Tooling choices

| Tool | Role | Rationale |
|------|------|-----------|
| **MkDocs Material** | Static site generator | Fast builds, excellent search, professional defaults |
| **Markdown** | Authoring format | Universal, diff-friendly, no proprietary lock-in |
| **OpenAPI 3.1** | API contract | Industry standard; tooling ecosystem (validators, codegen, Postman) |
| **GitHub Actions** | CI | Validate spec and build docs on every push |

### Alternatives considered

- **Docusaurus** — Strong for product docs with React components; heavier setup for a writer-led portfolio piece.
- **Redoc-only** — Great for reference, weak for tutorials and conceptual content.
- **DITA/Oxygen** — Excellent for regulated industries; less common in API doc portfolios. Structured authoring concepts are reflected in the IA, not the tooling.

## Error documentation strategy

Errors are documented in two places:

1. **OpenAPI spec** — `Error` schema and per-endpoint error responses
2. **Error catalog** — Markdown table with `code`, HTTP status, cause, and remediation

The catalog is the support-friendly view; the spec is the machine-readable view.

## Versioning and lifecycle

- URL versioning: `/v1/`
- Changelog follows [Keep a Changelog](https://keepachangelog.com/)
- Deprecation policy defines minimum notice period (6 months) and communication channels

## Future enhancements

- Redoc or Swagger UI embedded in reference pages (generated from OpenAPI)
- Vale linting for style consistency
- Link checker in CI
- Multi-language code samples (Python, Node.js, cURL)
