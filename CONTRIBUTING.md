# Contributing

Thank you for your interest in improving this API documentation sample suite.

## Scope

This is a portfolio/documentation project. Contributions that improve clarity, accuracy, or structure are welcome.

## How to contribute

1. Fork the repository
2. Create a feature branch (`git checkout -b improve/error-catalog`)
3. Make your changes
4. Run local checks:
   ```bash
   pip install -r requirements.txt
   openapi-spec-validator openapi/acme-payments-api.yaml
   mkdocs build --strict
   ```
5. Commit with a clear message
6. Open a pull request

## Style guidelines

- Use second person ("you") in tutorials
- Keep sentences concise
- Include code examples for every API operation
- Follow the [Diátaxis](https://diataxis.fr/) content types (see [DESIGN.md](DESIGN.md))

## What we're not accepting

- Changes to the fictional company name or branding (unless fixing inconsistencies)
- Real API keys or credentials
- Generated content without editorial review

## Questions

Open an issue for discussion before large structural changes.
