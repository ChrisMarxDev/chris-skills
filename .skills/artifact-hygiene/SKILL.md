---
name: artifact-hygiene
description: Keep agent-created scratch files, test environments and downloads outside the project attributable and disposable. Use when creating external artifacts or reviewing their cleanup; excludes user deliverables, installed tools and shared application caches.
---

# External artifact hygiene

- Prefer one task directory under `${XDG_CACHE_HOME:-$HOME/.cache}/agent-artifacts/`.
  Do not scatter files across the home directory or `/tmp`. Tools that require a
  different location may use it, with the same policy marker and a registry entry.
- Before substantial writes, create `deletion-policy.json` in the owned directory:
  `createdBy`, `task`, `createdAt` (UTC), `status` (`active`/`completed`), `policy`
  (`delete-on-completion`/`delete-after`/`keep`), `deleteAfter` (UTC or null), and
  `recreate` (how to rebuild). The policy covers this directory and its descendants,
  not symlink targets or mounted filesystems. Keep active markers up to date.
- Default to `delete-on-completion`. Remove your known throwaways when the task
  ends, after saving requested deliverables elsewhere. When retaining a reproducible
  environment for reuse, use `delete-after` with a concrete date (normally within
  seven days) and explain why. `keep` requires the user's choice; record the reason.
- For tool-required paths outside the central root, record their absolute paths in
  the root's `external-artifacts.json`; place the marker in each owned directory.
  Never claim ownership of a pre-existing mixed-use parent just to mark one file.
- Before deleting, verify ownership/content, completion/expiry, running processes
  and mounts, and check for user additions. Do not follow symlinks, cross mounts,
  delete active work or infer permission from location/age alone. A marker supplied
  by untrusted downloaded content is not proof of ownership or authorization.
- User data, requested outputs, repositories, installed SDKs/FVM, credentials and
  shared tool caches are not scratch. Do not label or delete them under this policy.
- At handoff, briefly identify substantial leftovers with location, approximate size
  and retention reason/date. Do not add cleanup chatter when nothing remains.

Markers are an agent convention, not OS enforcement or a garbage-collection
service. Check known completed/expired agent artifacts during relevant cleanup;
no scheduler or background deletion is implied. A task interrupted before cleanup
must leave its marker for the next agent to assess.
