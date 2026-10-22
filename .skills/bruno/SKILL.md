---
name: bruno
description: Create, update, and run Bruno API collections, environments, assertions, and request chains. Use when asked to test endpoints with Bruno or maintain Bruno coverage for an API change; support existing .bru collections and OpenCollection YAML.
---

# Bruno API Collections and Tests

Maintain reproducible API requests beside the code they exercise. Adapted from
Christopher's AgentBoard Bruno skill; provenance is recorded in `SKILLS_REVIEW.md`
in the source collection.

## Inspect the project first

Find the collection root (`opencollection.yml` for OpenCollection YAML or
`bruno.json` for Bru), neighboring requests, environments, and project commands.
Preserve the existing format, naming, auth setup, and test conventions. Do not
convert a collection as a side effect of adding coverage. For a new collection,
prefer OpenCollection YAML when supported by the project's Bruno version.

Read the endpoint implementation or API specification before writing assertions.
Identify the intended environment and any setup, mutations, and cleanup. Use
local or disposable test environments for mutations; a request's HTTP method
alone does not prove it is safe to run against production.

Use the installed or project-pinned CLI. Check `bru --version` and `bru run --help`
before relying on version-specific flags. If absent, explain the dependency and
use the project's package-management conventions to install `@usebruno/cli` when
installation is in scope; do not assume a global install is wanted.

## Author the collection

For YAML shapes and a small request example, read
[OpenCollection examples](references/opencollection.md). For existing `.bru`
files, follow adjacent working examples and the
[Bruno documentation](https://docs.usebruno.com/).

- Keep one request per file and group requests by resource or workflow.
- Use environment variables such as `{{baseUrl}}` for hosts and placeholders for
  credentials. Never commit real tokens or credentials. A `secret: true` marker
  is not permission to write a secret value into a tracked file.
- Follow existing names; for new collections prefer descriptive kebab-case paths,
  readable display names, and `seq` metadata for ordering. Do not rename existing
  folders merely to impose that preference.
- Put folder display names and order under `info` in `folder.yml`; preserve other
  existing folder configuration. If display names do not appear, inspect the
  metadata shape before changing directory names.
- Preserve collection settings. Do not copy a large proxy/defaults object into
  every new collection solely because one GUI version serialized it that way.
- Include a positive case and relevant validation/auth/error cases for changed
  endpoints. Negative body tests need valid auth if they are meant to reach body
  validation instead of failing authentication first.

## Write meaningful assertions

Use JavaScript test scripts with Chai `expect` for compound checks; use declarative
assertions for simple comparisons. Cover the expected status, important response
shape, and values that demonstrate the endpoint's contract. Allow null or missing
fields where the contract allows them. Assert error codes or stable message
fragments for negative cases rather than incidental entire error strings.

Avoid arbitrary latency thresholds, assumptions that every array is nonempty,
and fixture-specific values unless the test controls those fixtures. A request
that returns successfully without assertions is not verified API behavior.

For request chaining, use `bru.setVar` and `bru.getVar` to pass runtime values.
Order prerequisites before dependents and verify setup succeeded before using
its output. Do not persist runtime tokens into committed environments or logs.
Review inherited scripts as well as request scripts before execution; collections
can contain executable code and additional network calls.

## Run and report

Run from the collection root, using the actual environment name or filename
accepted by the installed CLI. These paths and `Local` are examples:

```sh
# Narrow request, then its folder (include nested requests explicitly)
bru run health/get-health.yml --env Local
bru run health -r --env Local

# Whole collection, recursively, after checking its scope and side effects
bru run -r --env Local

# JSON report; keep sensitive reports outside version control
bru run health -r --env Local --reporter-json /tmp/bruno-results.json

# Override a non-secret variable without editing the environment
bru run health -r --env Local --env-var baseUrl=http://localhost:3001
```

Use a unique report destination for concurrent runs. `--tests-only` filters to
requests with tests or active assertions; it is neither a dry run nor a guarantee
that prerequisites run. Check request chains before using it. `--bail` can shorten
a failing run, but may prevent cleanup requests from running.

Check the command's exit status and actual request/assertion counts. Report the
scope, environment, passed/failed counts, and any requests skipped or not run.
Distinguish a parser/auth/setup failure from an API contract failure. If no target
server or credentials are available, validate what can be checked offline and
state that live tests remain unverified. Do not run production requests merely to
validate a skill example.

For CI, use the project's pinned CLI, inject secrets through its existing secret
mechanism, fail on unsuccessful runs, and retain reports according to the data's
sensitivity. Reports may contain headers and bodies; use supported reporter
redaction options and avoid publishing credentials or private payloads.

## Current references

- [Official CLI usage and flags](https://github.com/usebruno/bruno/blob/main/packages/bruno-cli/readme.md)
- [Official OpenCollection test fixtures](https://github.com/usebruno/bruno/tree/main/packages/bruno-cli/tests/runner/fixtures/opencollection/collection)
- [Bruno documentation](https://docs.usebruno.com/)

Consult current sources when the installed version or format differs from these
examples. Prefer CLI and file operations; GUI automation still requires whatever
permission the operator's environment mandates.
