# Playwright Web Automation Framework

[![Playwright tests](https://github.com/DenIce44/playwright-web-automation-framework/actions/workflows/playwright.yml/badge.svg)](https://github.com/DenIce44/playwright-web-automation-framework/actions/workflows/playwright.yml)

A portfolio project by **Denys Ishchuk** demonstrating maintainable UI and API automation with Playwright and TypeScript. The framework turns test strategy into executable, cross-browser release evidence—not just a collection of scripts.

## What this project demonstrates

- Page Object Model with responsibility-focused methods
- Positive, negative, and state-transition UI scenarios
- API status, header, and response-body validation
- Data separated from test behavior
- Smoke tagging for fast feedback
- Chromium, Firefox, and WebKit coverage
- Parallel execution with CI retries
- HTML and JUnit reporting
- Traces, screenshots, and videos for failure triage
- GitHub Actions quality gates and retained evidence
- A documented, risk-based [test strategy](docs/TEST-STRATEGY.md)

## Test targets

- UI: [Playwright TodoMVC demo](https://demo.playwright.dev/todomvc)
- API: [JSONPlaceholder](https://jsonplaceholder.typicode.com)

These public demo services keep the project reproducible and free of employer code or confidential data.

## Project structure

```text
.
├── .github/workflows/       # Cross-browser CI pipeline
├── docs/                    # Test strategy and quality decisions
├── pages/                   # Page objects
├── test-data/               # Reusable test inputs
├── tests/
│   ├── api/                 # REST API scenarios
│   └── ui/                  # Browser scenarios
├── playwright.config.ts     # Execution, reporting, and evidence settings
└── tsconfig.json            # Strict TypeScript checks
```

## Run locally

Prerequisites: Node.js 20+ and npm.

```bash
npm ci
npx playwright install
npm test
```

Useful commands:

```bash
npm run test:smoke      # fastest critical-path signal
npm run test:api        # API suite only
npm run test:chromium   # one browser
npm run test:ui         # interactive Playwright UI
npm run report          # open the latest HTML report
```

## Configuration

The defaults run without secrets. Override targets through environment variables when needed:

```bash
BASE_URL=https://demo.playwright.dev/todomvc/ \
API_BASE_URL=https://jsonplaceholder.typicode.com \
npm test
```

See [.env.example](.env.example) for supported values. Never commit credentials or environment-specific secrets.

## Quality decisions

- Tests assert user-visible outcomes rather than implementation details where practical.
- Page objects encapsulate interactions; business assertions stay readable in specifications.
- Test data is deterministic and unique to each browser context.
- CI captures evidence only when useful, balancing debuggability and storage.
- The test strategy states both coverage and deliberate exclusions.

## Author

**Denys Ishchuk** — QA Engineer with four years of manual testing experience, test-strategy ownership, performance testing with Apache JMeter, team leadership, and growing automation expertise.

- [GitHub](https://github.com/DenIce44)
- [LinkedIn](https://www.linkedin.com/in/denys-i-273b3a247)

## Attribution

This repository began as a fork of Microsoft's `playwright-examples`. The portfolio framework, structure, documentation, and showcased scenarios have been redesigned for original demonstration purposes. Playwright is maintained by Microsoft and is used under its applicable license.

## License

MIT
