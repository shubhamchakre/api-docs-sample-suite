# API Documentation Sample Suite

A personal portfolio project — an end-to-end API documentation suite for a fictional fintech product, **Acme Payments API**. This repository demonstrates how to design, structure, and publish developer documentation using docs-as-code practices.

> **Note:** Acme Payments is a fictional company. All endpoints, credentials, and data are for demonstration only. This project is independent of any employer and is published on my personal GitHub for portfolio purposes.

## What's included

| Artifact | Description |
|----------|-------------|
| [OpenAPI 3.1 spec](openapi/acme-payments-api.yaml) | Machine-readable API contract with schemas, examples, and error models |
| [Documentation site](docs/) | MkDocs Material site with tutorials, guides, and reference content |
| [Postman collection](postman/Acme-Payments-API.postman_collection.json) | Ready-to-import collection with example requests |
| [Error catalog](docs/reference/error-catalog.md) | Human-readable error codes with causes and remediation |
| [Changelog](docs/reference/changelog.md) | Version history following Keep a Changelog format |
| [Deprecation policy](docs/reference/deprecation-policy.md) | API lifecycle and sunset guidelines |
| [DESIGN.md](DESIGN.md) | Information architecture and documentation decisions |

## Quick start

### Prerequisites

- Python 3.10+
- pip

### Run the documentation site locally

```bash
git clone https://github.com/shubhamchakre/api-docs-sample-suite.git
cd api-docs-sample-suite
pip install -r requirements.txt
mkdocs serve
```

Open [http://127.0.0.1:8000](http://127.0.0.1:8000) in your browser.

### Build static site

```bash
mkdocs build
```

Output is written to the `site/` directory.

### Validate the OpenAPI spec

```bash
pip install openapi-spec-validator
openapi-spec-validator openapi/acme-payments-api.yaml
```

## Project structure

```
api-docs-sample-suite/
├── openapi/
│   └── acme-payments-api.yaml    # OpenAPI 3.1 specification
├── docs/
│   ├── getting-started/          # Onboarding and authentication
│   ├── tutorials/                # Task-oriented guides
│   ├── guides/                   # Conceptual documentation
│   └── reference/                # API reference, errors, changelog
├── postman/
│   └── Acme-Payments-API.postman_collection.json
├── mkdocs.yml                    # Site configuration
├── DESIGN.md                     # IA and design rationale
└── README.md
```

## Documentation highlights

### Tutorials

1. **[Create your first payment](docs/tutorials/first-payment.md)** — End-to-end walkthrough from API key to confirmed charge
2. **[Handle webhooks](docs/tutorials/handle-webhooks.md)** — Verify signatures and process async events
3. **[Process a refund](docs/tutorials/process-refund.md)** — Full and partial refund flows

### API surface (sample)

| Resource | Endpoints |
|----------|-----------|
| Payments | `POST /v1/payments`, `GET /v1/payments/{id}`, `GET /v1/payments`, `POST /v1/payments/{id}/cancel` |
| Refunds | `POST /v1/refunds`, `GET /v1/refunds/{id}` |
| Customers | `POST /v1/customers`, `GET /v1/customers/{id}` |
| Webhooks | `POST /v1/webhook-endpoints`, event types documented |

## Skills demonstrated

- **Information architecture** — Content types (tutorial, guide, reference) mapped to user journeys
- **API-first documentation** — OpenAPI spec as source of truth with curated narrative docs
- **Docs-as-code** — Markdown, version control, automated builds
- **Developer experience** — Postman collection, copy-paste examples, error remediation
- **API lifecycle** — Changelog, versioning, and deprecation policy

## Resume bullet

> Designed and published an open-source API documentation suite for a sample fintech product, including OpenAPI 3.1 specification, developer tutorials, error catalog, Postman collection, and automated docs-as-code publishing pipeline.

## Publish to personal GitHub

Use your **personal** GitHub account, not a work or organization account:

```bash
cd api-docs-sample-suite
git init
git add .
git commit -m "Add API documentation sample suite"
git remote add origin https://github.com/shubhamchakre/api-docs-sample-suite.git
git push -u origin main
```

If your global git email is a work address, set a personal identity for this repo only before committing:

```bash
git config user.name "Shubham Chakre"
git config user.email "shubhamshivrekha@gmail.com"
```

## License

MIT — feel free to fork and adapt for your own portfolio.

## Author

**Shubham Chakre** — Technical Writer  
GitHub: [github.com/shubhamchakre](https://github.com/shubhamchakre) · Email: [shubhamshivrekha@gmail.com](mailto:shubhamshivrekha@gmail.com)

Experience across Aerospace, Fintech, and Telecom domains.
