# Global skills publishing review

Reviewed locally on 2026-10-08. Target: a public `.skills/` source collection.

## Recommendation

Christopher selected `bottleneck`, `cli-first`, `core-principles`, and `taskfile`
for inclusion. These four have been imported unchanged from `~/.codex/skills/`,
including their `agents/openai.yaml` files. The Codex copy of `taskfile` is the
selected version. No license has been added yet.

`github-rebase-sync` is also included, reworked to commit on the current branch
and synchronize at checkpoints and task completion. Its standing rule is recorded
in this repository’s `AGENTS.md`.

Discuss `code-plan-handoff`, `flame-architecture`, and `persona` before importing them. Other inventory recommendations remain provisional.

Keep third-party skills as upstream dependencies where practical. Record local
customizations before replacing them; installed copies may differ from upstream.
No upstream repository or license terms were verified online during this pass.

## Review scope and limits

Inspected global folder inventories, skill entrypoints, source lock metadata,
license-file presence, and selected supporting text. This is an initial selection
and portability review, not a complete script, media-rights, or secret audit.
Mentions of API keys are dependencies, not evidence of exposed credentials.

Sources: `~/.codex/skills`, `~/.agents/skills`, `~/.claude/skills`,
`~/.cursor/skills`, `~/.gemini/skills`, and the Codex plugin cache.
Cache presence does not establish that a plugin is enabled.
System skills and plugin bundles should generally be supplied by their runtime.

## Codex standalone skills

| Skill | Recommendation | Reason / next step |
|---|---|---|
| `bottleneck` | Imported | Focused strategic interview; portable Markdown workflow. |
| `cli-first` | Imported | Reusable tool-selection preference; useful in a cloud environment. |
| `code-plan-handoff` | Discuss | Concrete implementation handoff; include the HTML template. |
| `computer-use-permission` | Adapt | Useful personal policy; decide whether public wording keeps Christopher’s name. |
| `concept-planning` | Adapt | Remove or isolate AgentShelf-specific defaults; compare overlap with code-plan-handoff. |
| `core-principles` | Imported | Reusable project decision rules without a desktop dependency. |
| `design-taste-frontend` | Source review | Large external-looking taste-skill; establish origin and terms; choose one default design skill. |
| `design-taste-frontend-v1` | Defer | Legacy alternative; retain only if a project requires exact v1 behavior. |
| `expo-shaders` | Later batch | Specialist mobile graphics workflow; confirm authorship and include references. |
| `figma-implement-design` | Upstream | Bundled license exists; depends on Figma tooling. Prefer upstream installation. |
| `flame-architecture` | Discuss | Reusable scene and state ownership guidance; specialist but portable. |
| `flue` | Later batch | Relevant to cloud agents; review references and origin before importing. |
| `flutter` | Adapt | Useful personal conventions; label absolute LayoutBuilder/post-frame bans as opinionated preferences. |
| `flutter-permission-handler` | Later batch | Useful package-specific workflow; include references and document platform build requirements. |
| `frontend-design` | Hold | SKILL.md names LICENSE.txt, but that file is absent. Resolve provenance and missing terms. |
| `github-issue-flow` | Later batch | Includes installer, workflow assets, and tests; review the whole bundle before public import. |
| `github-rebase-sync` | Adapted | Current-branch commit/rebase/push workflow with remote verification and bounded race retries; standing rule in AGENTS.md. |
| `i-have-adhd` | Opt-in | Reusable communication preference; choose deliberately whether to publish under this personal label. |
| `jev` | Adapt | Uses a saved local key and fixed global skill paths; use portable script resolution and runtime secrets. |
| `persona` | Discuss | Interview/evaluation workflow with bundled reference; prefer this Codex variant over Claude copy. |
| `remotion-best-practices` | Upstream | Reference bundle with many linked files; establish origin/version and preserve any local changes. |
| `retro` | Hold | Requires writing-for-agents, not found in inspected standalone global roots; resolve dependency and origin. |
| `sentry` | Upstream | Licensed integration bundle; requires runtime Sentry credentials. |
| `simdeck` | Desktop only | Requires simulator/emulator tooling; exclude from the initial general cloud collection. |
| `sora` | Upstream | Licensed API/CLI bundle; provision credentials separately if needed. |
| `swirl-illustration` | Project only | Symlink into the Swirl repository; brand-specific guidance/assets belong there. |
| `swirl-release` | Project only | Symlink; repository-relative release contracts and macOS signing/notarization dependencies. |
| `taskfile` | Imported | Portable task-runner guidance; Codex copy selected. |
| `tldraw-offline` | Desktop only | Local desktop service, absolute user paths, per-launch token, and external helper dependency. |
| `twitter-reader` | Later batch | Useful web-reading workflow; assess external reader dependencies and fallback behavior. |
| `typesafe-ai` | Upstream | Local MIT declaration and LICENSE exist; retain attribution and establish install source. |
| `video-shotcraft` | Upstream | External bundle with code/media assets and local modifications possible; avoid copying wholesale. |
| `web-design-guidelines` | Source review | Small remote-guideline wrapper; establish origin and avoid duplicate design rules. |
| `yeet` | Upstream | Licensed GitHub PR workflow; prefer maintained upstream installation. |

## Shared agent skills

Sources below come from the local skills lockfile; they have not been checked remotely.

| Skill | Recorded source | Recommendation |
|---|---|---|
| `agents-sdk` | `cloudflare/skills` | Upstream dependency; preserve local modifications before reinstalling. |
| `cloudflare` | `cloudflare/skills` | Upstream dependency; preserve local modifications before reinstalling. |
| `cloudflare-email-service` | `cloudflare/skills` | Upstream dependency; preserve local modifications before reinstalling. |
| `cloudflare-one` | `cloudflare/skills` | Upstream dependency; preserve local modifications before reinstalling. |
| `cloudflare-one-migrations` | `cloudflare/skills` | Upstream dependency; preserve local modifications before reinstalling. |
| `durable-objects` | `cloudflare/skills` | Upstream dependency; preserve local modifications before reinstalling. |
| `find-skills` | `vercel-labs/skills` | Upstream dependency; preserve local modifications before reinstalling. |
| `google-ads-manager` | `claude-office-skills/skills` | Upstream dependency; preserve local modifications before reinstalling. |
| `grill-me` | `mattpocock/skills` | Upstream; consolidate interview variants with grilling. |
| `grill-with-docs` | `mattpocock/skills` | Upstream; consolidate interview variants with grilling. |
| `grilling` | `Not recorded` | No lockfile source entry; compare with grill-me and grill-with-docs before choosing one. |
| `improve-codebase-architecture` | `mattpocock/skills` | Upstream dependency; preserve local modifications before reinstalling. |
| `prototype` | `mattpocock/skills` | Upstream dependency; preserve local modifications before reinstalling. |
| `research` | `mattpocock/skills` | Upstream dependency; preserve local modifications before reinstalling. |
| `sandbox-sdk` | `cloudflare/skills` | Upstream dependency; preserve local modifications before reinstalling. |
| `seo-audit` | `coreyhaines31/marketingskills` | Upstream dependency; preserve local modifications before reinstalling. |
| `triage` | `mattpocock/skills` | Upstream dependency; preserve local modifications before reinstalling. |
| `turnstile-spin` | `cloudflare/skills` | Upstream dependency; preserve local modifications before reinstalling. |
| `wayfinder` | `mattpocock/skills` | Upstream dependency; preserve local modifications before reinstalling. |
| `web-perf` | `cloudflare/skills` | Upstream; requires browser/DevTools capability and UI permission. |
| `workers-best-practices` | `cloudflare/skills` | Upstream dependency; preserve local modifications before reinstalling. |
| `wrangler` | `cloudflare/skills` | Upstream dependency; preserve local modifications before reinstalling. |
| `writing-great-skills` | `mattpocock/skills` | Upstream dependency; preserve local modifications before reinstalling. |

## Claude skills and alternate copies

| Skill / entry | Recommendation |
|---|---|
| `autoplan` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `benchmark` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `browse` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `bug-finder` | Later candidate; establish source/ownership and assess overlap before import. |
| `canary` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `careful` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `codex` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `connect-chrome` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `cso` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `design-consultation` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `design-html` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `design-review` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `design-shotgun` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `document-release` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `flutter-it` | Later candidate; establish source/ownership and assess overlap before import. |
| `freeze` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `gstack` | Upstream suite; keep as a dependency and assess Claude/runtime assumptions. |
| `gstack-upgrade` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `guard` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `investigate` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `land-and-deploy` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `landing-page-creator` | Overlaps design skills; source/ownership review before selecting. |
| `learn` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `norma-design-system` | Project-specific design system; keep with its owning project. |
| `office-hours` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `persona` | Overlapping Codex version; compare and choose one canonical skill. |
| `plan-ceo-review` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `plan-design-review` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `plan-eng-review` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `qa` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `qa-design-review` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `qa-only` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `retro` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `review` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `sentry-fix` | Nested package, not a top-level SKILL.md; review nested workflow separately. |
| `setup-browser-cookies` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `setup-deploy` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `shadcn-ui` | Later candidate; establish source/ownership and assess overlap before import. |
| `ship` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |
| `skill-creator` | Runtime/upstream skill; avoid maintaining a duplicate. |
| `taskfile` | Overlapping Codex version; compare and choose one canonical skill. |
| `tldraw-offline` | Desktop-only duplicate; exclude from first cloud batch. |
| `unfreeze` | gstack alias; install the upstream suite if needed, rather than vendoring this link. |

Cursor and Gemini each also contain `tldraw-offline`; these are alternate
installations, not additional initial publishing candidates.

## System skills

Runtime-managed: `imagegen`, `openai-docs`, `review-agent`, `skill-creator`, `skill-installer`.

## Cached plugin skill bundles

Treat these as runtime/plugin dependencies rather than copied public skill bodies.
Names below enumerate skill files present in each cached version; they do not
prove activation, ownership, or runtime compatibility.

### claude-plugins-official / superpowers (6.4.1)

15 skill files: `brainstorming`, `diagnosing-superpowers`, `dispatching-parallel-agents`, `executing-plans`, `finishing-a-development-branch`, `receiving-code-review`, `requesting-code-review`, `subagent-driven-development`, `systematic-debugging`, `test-driven-development`, `using-git-worktrees`, `using-superpowers`, `verification-before-completion`, `writing-plans`, `writing-skills`.

### openai-bundled / visualize (1.0.46)

1 skill files: `visualize`.

### openai-curated-remote / openai-templates (0.1.1)

20 skill files: `artifact-template-analytics-dashboard`, `artifact-template-business-review`, `artifact-template-design-report`, `artifact-template-experiment-analysis`, `artifact-template-financial-budget`, `artifact-template-investment-committee-memo`, `artifact-template-legal-memorandum`, `artifact-template-market-trends-report`, `artifact-template-minimal-letterhead`, `artifact-template-operating-calendar`, `artifact-template-operating-review`, `artifact-template-project-kickoff`, `artifact-template-project-tracker`, `artifact-template-sales-pipeline`, `artifact-template-simple-dark-mode`, `artifact-template-simple-light-mode`, `artifact-template-strategy-memorandum`, `artifact-template-system-design`, `artifact-template-team-alignment`, `artifact-template-three-statement-forecast`.

### openai-curated-remote / pages (0.1.21)

4 skill files: `maintain-space`, `manage-schedules`, `organize-space`, `write-page`.

### openai-curated-remote / plugin-management (0.1.0)

1 skill files: `plugin-management`.

### openai-curated-remote / product-design (0.1.56)

10 skill files: `audit`, `design-qa`, `get-context`, `ideate`, `image-to-code`, `index`, `research`, `share`, `url-to-code`, `user-context`.

### openai-curated-remote / sites (1.0.0-c)

1 skill files: `sites`.

### openai-curated-remote / work-pets (0.1.6)

3 skill files: `create-pet`, `pets`, `update-pet`.

### openai-primary-runtime / documents (26.1005.12141)

1 skill files: `documents`.

### openai-primary-runtime / pdf (26.1005.12141)

1 skill files: `pdf`.

### openai-primary-runtime / presentations (26.1005.12141)

1 skill files: `presentations`.

### openai-primary-runtime / spreadsheets (26.1005.12141)

2 skill files: `excel-live-control`, `spreadsheets`.

### openai-primary-runtime / template-creator (26.1005.12141)

1 skill files: `template-creator`.

### paddle-agent-skills / paddle (0.1.0)

10 skill files: `billing-history`, `catalog-setup`, `checkout-web`, `customer-portal`, `pricing-pages`, `sandbox-testing`, `subscription-cancel`, `subscription-sync`, `subscription-update`, `webhooks`.

### posthog / posthog (1.0.64)

162 skill files: `source-command-llma-cc-status`, `adding-warehouse-person-properties`, `analyzing-expensive-users`, `analyzing-experiment-session-replays`, `analyzing-task-runs`, `assessing-heatmaps`, `auditing-endpoints`, `auditing-experiments-flags`, `auditing-warehouse-source-health`, `auditing-warehouse-view-health`, `authoring-data-quality-checks`, `authoring-error-tracking-alerts`, `authoring-log-alerts`, `authoring-scouts`, `building-a-dashboard`, `building-canvases`, `building-html-canvases`, `building-loops`, `building-react-quill-canvases`, `building-workflows`, `checking-deploy-timing`, `checking-member-access`, `choosing-trend-or-slope-view`, `cleaning-up-stale-feature-flags`, `composing-grid-canvases`, `configuring-experiment-analytics`, `configuring-experiment-rollout`, `consuming-endpoints-from-client-code`, `context-layer-consolidation`, `context-layer-dreaming`, `context-layer-health-check`, `copying-endpoints-across-projects`, `copying-flags-across-projects`, `creating-ai-subscription`, `creating-an-endpoint`, `creating-box-plot-insights`, `creating-experiments`, `creating-online-evaluations`, `creating-replay-vision-scanners`, `creating-surveys`, `debugging-experiments`, `debugging-surveys`, `designing-email-templates`, `diagnosing-ci-and-merge-bottlenecks`, `diagnosing-endpoint-performance`, `diagnosing-experiment-results`, `diagnosing-failed-warehouse-syncs`, `diagnosing-missing-recordings`, `diagnosing-sdk-health`, `diagnosing-stacktrace-symbolication`, `downloading-batch-export-files`, `exploring-ai-failures`, `exploring-apm-traces`, `exploring-autocapture-events`, `exploring-endpoint-execution-logs`, `exploring-live-traffic`, `exploring-llm-clusters`, `exploring-llm-costs`, `exploring-llm-evaluations`, `exploring-llm-traces`, `exploring-mcp-intent-clusters`, `exploring-mcp-sessions`, `exploring-mcp-tool-original-user-motive`, `exploring-mcp-tool-quality`, `exploring-mcp-tool-usage`, `exploring-replay-vision-observations`, `exploring-scouts`, `feature-usage-feed`, `filtering-bot-traffic`, `finding-deleted-feature-flags`, `finding-experiments`, `finding-replay-for-issue`, `finding-sessions-to-watch`, `formatting-insight-axes`, `grouping-noisy-errors`, `inbox-exploration`, `instrument-error-tracking`, `instrument-feature-flags`, `instrument-integration`, `instrument-llm-analytics`, `instrument-logs`, `instrument-metrics`, `instrument-product-analytics`, `investigate-metric`, `investigating-ci-failures`, `investigating-error-issue`, `investigating-logs`, `investigating-metric-anomalies`, `investigating-replay`, `managing-endpoint-versions`, `managing-experiment-lifecycle`, `managing-path-cleaning-rules`, `managing-reminders`, `managing-streamlit-apps`, `managing-subscriptions`, `modeling-activation-metrics`, `modeling-conversion-metrics`, `modeling-dimension-tables`, `modeling-product-usage-metrics`, `modeling-revenue-metrics`, `modeling-warehouse-foundations`, `querying-canvas-data`, `querying-posthog-data`, `resolving-ingestion-warnings`, `review-hog-authoring`, `review-hog-blind-spots-general`, `review-hog-perspective-contracts-security`, `review-hog-perspective-logic-correctness`, `review-hog-perspective-performance-reliability`, `review-hog-resolution-criteria`, `review-hog-validation-criteria`, `scanning-experiments-with-replay-vision`, `setting-up-a-custom-rest-source`, `setting-up-a-data-warehouse-source`, `setting-up-data-catalog`, `setting-up-warehouse-properties`, `signals`, `signals-scout-ai-observability`, `signals-scout-anomaly-detection`, `signals-scout-apm`, `signals-scout-conversations`, `signals-scout-csp-violations`, `signals-scout-customer-analytics`, `signals-scout-customer-analytics-billing-and-usage`, `signals-scout-data-pipelines`, `signals-scout-data-warehouse`, `signals-scout-error-tracking`, `signals-scout-experiments`, `signals-scout-feature-flags`, `signals-scout-general`, `signals-scout-health-checks`, `signals-scout-inbox-validation`, `signals-scout-insight-alerts`, `signals-scout-logs`, `signals-scout-mcp-tool-calls`, `signals-scout-observability-gaps`, `signals-scout-pr-follow-up`, `signals-scout-product-analytics`, `signals-scout-replay-vision`, `signals-scout-revenue-analytics`, `signals-scout-session-replay`, `signals-scout-skills-store`, `signals-scout-surveys`, `signals-scout-tasks`, `signals-scout-web-analytics`, `signals-scout-web-vitals`, `signals-scout-workflows`, `skills-store`, `suggesting-data-imports`, `suggesting-path-cleaning-rules`, `suppressing-noisy-errors`, `triaging-error-issues`, `triaging-visual-review-runs`, `tuning-incremental-sync-config`, `turning-engineering-analytics-into-insights`, `understanding-billing-usage`, `validating-and-publishing-canvases`, `working-with-scouts`, `working-with-skills`, `working-with-task-comments`, `writing-simplified-technical-english`, `writing-streamlit-apps`.

## Import checklist

For each selected skill:

1. Establish authorship/source and include applicable license/attribution.
2. Read all bundled scripts and referenced assets before copying.
3. Replace personal paths and document runtime tools and secret variable names.
4. Check bundled links and include required references/templates.
5. Preserve intentional custom changes and record their source.
6. Confirm the cloud runtime can discover/install the collection.

Four selected skill bundles have been imported unchanged from the local Codex
installation. A fifth, `github-rebase-sync`, was adapted for distributed work.
No credentials, plugin caches, or external symlinks were imported.
No Git remote is configured in this checkout; no publication has been performed.
