# OpenCollection YAML examples

Adapted from the AgentBoard skill and checked against Bruno's official fixtures.
These examples use a hypothetical local `GET /health` returning `{"ok": true}`.
Change the URL and assertions to the real API contract before running them.
Preserve additional fields in an existing collection.

```text
bruno/
  opencollection.yml
  environments/
    Local.yml
  health/
    folder.yml
    get-health.yml
```

## Collection: opencollection.yml

```yaml
opencollection: "1.0.0"
info:
  name: Example API
```

## Environment: environments/Local.yml

```yaml
name: Local
variables:
  - name: baseUrl
    value: http://localhost:3000
```

Use the project's secure runtime mechanism for credentials. Keep placeholders
empty in tracked files; do not copy actual environment values from another project.

## Folder: health/folder.yml

```yaml
info:
  name: Health
  type: folder
  seq: 1
request: {}
```

## Request: health/get-health.yml

```yaml
info:
  name: Check health
  type: http
  seq: 1
http:
  method: GET
  url: "{{baseUrl}}/health"
  auth:
    type: none
runtime:
  scripts:
    - type: tests
      code: |-
        test("returns 200", function () {
          expect(res.status).to.equal(200);
        });
        test("reports a healthy service", function () {
          expect(res.body).to.be.an("object");
          expect(res.body).to.have.property("ok", true);
        });
```

For authenticated requests, follow the existing collection's inherited auth or
use a bearer placeholder in `http.auth`:

```yaml
auth:
  type: bearer
  token: "{{token}}"
```

For JSON request bodies, add the appropriate content type and body under `http`:

```yaml
headers:
  - name: Content-Type
    value: application/json
body:
  type: json
  data: |-
    {"name": "Example"}
```

For a simple declarative assertion, add this under `runtime`:

```yaml
assertions:
  - expression: res.status
    operator: eq
    value: "200"
```

For a prerequisite request that returns an ID, add an `after-response` script to
`runtime.scripts` and refer to `{{itemId}}` in the dependent request. Validate the
setup response and ensure the ID belongs to the test's disposable data:

```yaml
- type: after-response
  code: |-
    if (res.status !== 201 || !res.body.id) {
      throw new Error("Item setup failed");
    }
    bru.setVar("itemId", res.body.id);
```
