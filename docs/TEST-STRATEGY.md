# Test strategy

## Objective

Provide fast, maintainable evidence that critical TodoMVC behavior and representative REST API contracts remain usable across supported browsers.

## Coverage model

| Layer | Coverage | Purpose |
| --- | --- | --- |
| UI smoke | Create a task | Fast signal that the main journey works |
| UI functional | Complete, filter, and clear tasks | Validate state transitions and user-visible behavior |
| UI negative | Reject whitespace-only tasks | Exercise an important input boundary |
| API positive | Read and create posts | Validate status, headers, and response contracts |
| API negative | Request an unknown resource | Validate expected failure behavior |

## Risk priorities

1. A user cannot create or retain a task.
2. Filtering shows incorrect task state.
3. Removing completed work also removes active work.
4. API status codes or core identifiers break their expected contract.
5. Browser-specific behavior causes inconsistent results.

## Execution

- Pull requests run the full suite on Chromium, Firefox, and WebKit.
- `@smoke` scenarios provide a quick local confidence check.
- CI retries failures twice and records a trace on the first retry.
- Screenshots and videos are retained only for failures to support triage without excessive artifacts.

## Out of scope

The public demo applications do not represent a controlled production system. Security, accessibility, visual regression, load testing, and destructive API persistence are intentionally outside this sample's current scope.

## Exit criteria

- All critical-path tests pass on all configured browsers.
- No focused tests (`test.only`) enter CI.
- Failure artifacts are available for any unsuccessful CI run.
- Changes to behavior include corresponding test and strategy updates.
