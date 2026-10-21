---
name: jev
description: Use Jev through executor.sh for typed classification, scoring, routing, and resumable batch judgments. Use when invoking Jev or building a workflow around its decisions; discover Executor tools and connected accounts instead of using local API keys.
---

# Jev through Executor

Use [Executor](https://executor.sh) as the connection and execution layer for
[TypeSafe's Jev](https://docs.typesafe.ai/introduction). Credentials stay in
Executor's managed connection. Do not read local key files, load
`TYPESAFE_API_KEY`, invoke saved-key helpers, or request credentials in chat.

## Discover the connection

Use the host's Executor MCP tools; their prefixes may differ between agents.
The following names and objects describe Executor tool calls, not shell commands.

1. Read `skills({app: "executor", name: "executor"})` for current host guidance.
2. Call `search({query: "jev"})` to discover the current tool paths and connected
   accounts. Read any Jev app skills returned by `skills({app: <discovered-slug>})`.
3. Call `describe({paths: [<evaluate-path>, <list-models-path>]})` before building
   arguments. The observed paths are `tools.jev.evaluate` and
   `tools.jev.listModels`, but the live schema is authoritative. Select the account
   returned by discovery; never embed a personal account ID in this skill or code
   intended for others. Ask which account to use if the intended one is ambiguous.
4. If Executor is unavailable, report that its connection must be enabled in the
   agent. If Jev or its account is missing, follow Executor's current catalog and
   secure connection workflow. Discover and describe the setup tools before using
   them; give the operator the returned connection link to complete authentication.
   Do not invent a login URL or silently switch to direct API credentials.

Use `listModels` with the discovered account and `input: {}` when checking access
or choosing a model. A successful discovery alone does not prove authentication
works. If a call pauses for approval or input, surface the request and resume that
same operation using the returned continuation. Do not rerun it as a new request.

## Design questions

Read the [live documentation index](https://docs.typesafe.ai/llms.txt) and the
relevant primitive or cookbook before designing a new workflow. For product work,
use the [building guide](https://docs.typesafe.ai/concepts/how-to-build-with-system-one.md).
The optional official `typesafe-ai` skill can supply conceptual guidance, but its
local authentication instructions do not override this skill's Executor transport.
Do not assume features in the direct API are exposed by the Executor connector.

Keep deterministic rules in code. Give each judgment relevant state, clear
instructions, and concrete criteria. Put independent questions about the same
state in one evaluation. Preserve the returned probabilities and confidence for
thresholds and review; typed answers are not guarantees of correctness.

## Evaluate

After discovering the path and account, call Executor's `call` tool with the
following shape. Replace `ACCOUNT_FROM_DISCOVERY` with the selected account and
use the actual discovered path. This is an illustrative request, not a command
to execute whenever the skill is loaded.

```json
{
  "calls": {
    "path": "tools.jev.evaluate",
    "input": {
      "accountId": "ACCOUNT_FROM_DISCOVERY",
      "input": {
        "state": "The export button stopped working.",
        "questions": {
          "category": {
            "type": "choice",
            "instructions": "Classify the reported issue.",
            "criteria": {
              "defect": "Existing functionality fails",
              "enhancement": "New functionality requested",
              "other": "Neither category applies"
            }
          }
        },
        "model": "jev-latest"
      }
    }
  }
}
```

Check the outer Executor status and each call's `ok` and `value` or `error`.
Preserve the underlying result, including model and usage when supplied. Never
replace failed calls with invented judgments. Resolve authentication or schema
errors before retrying. For transient rate-limit or capacity failures, honor any
retry delay and use bounded backoff, at most three attempts per record; report
remaining failures. Timeouts may have consumed tokens even without a result.

For dependent calls or larger jobs, read Executor's
`skills({app: "executor", name: "code-mode"})` before using `execute`. Use its
current runtime and persistence APIs rather than assuming Node filesystem access.
When building a deployed product, keep the connection in the server or Executor
runtime; an agent's connected account is not automatically application auth.

## Larger jobs

Validate unique record IDs and questions before sending data. Start with a small
representative sample, inspect results and observed usage, then process the
requested dataset. Keep concurrency modest and respect current account limits.

Use durable checkpoints in an authorized location. Record each ID, a fingerprint
of state/questions/model, and either the complete response or an error. Persist
successes after each bounded group; resume only matching unfinished records.
Changed inputs or questions need a new run or distinct fingerprint. Prevent
concurrent writers and preserve completed results when a checkpoint is damaged.
An interruption between a response and its checkpoint can duplicate a charged
request; do not promise exactly-once execution or automatic resumability without
actually implementing durable checkpoints.

Report completed and failed counts, output location, observed usage, and any
uncertainty. Keep private datasets and results out of the public skill repository.
