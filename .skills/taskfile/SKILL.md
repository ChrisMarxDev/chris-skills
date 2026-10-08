---
name: taskfile
description: Use when creating, editing, running, or debugging Taskfile.dev automation and `task` CLI workflows.
---

# Taskfile.dev Guide

Task is a cross-platform task runner that uses YAML Taskfiles. Use this skill when:

- creating or editing `Taskfile.yml`
- running project tasks
- debugging task dependencies, includes, vars, or caching
- designing build/dev/release automation around `task`

## CLI Quick Reference

```bash
task                    # Run default task
task <name>             # Run a specific task
task ns:task            # Run a namespaced task from an include

task -l                 # List public tasks
task -a                 # List all tasks including internal ones
task --summary <name>   # Show task details

task --dry              # Preview commands without executing
task -f                 # Force run
task -w                 # Watch mode
task -p task1 task2     # Run tasks in parallel

task VAR=value          # Pass variables
task -- arg1 arg2       # Forward CLI args via {{.CLI_ARGS}}
```

## Taskfile Structure

```yaml
version: "3"

includes:
  app:
    taskfile: ./app/Taskfile.yml
    dir: ./app

vars:
  GIT_SHA:
    sh: git rev-parse --short HEAD

env:
  NODE_ENV: production

tasks:
  default:
    cmds:
      - task: build

  build:
    desc: Build the project
    deps: [clean, generate]
    cmds:
      - go build -o bin/app
    sources:
      - "**/*.go"
    generates:
      - bin/app
```

## Task Properties

| Property | Purpose |
|----------|---------|
| `cmds` / `cmd` | Commands to run |
| `deps` | Tasks to run first |
| `desc` | Short description for discovery |
| `summary` | Longer help text |
| `dir` | Working directory |
| `sources` | Inputs for up-to-date checks |
| `generates` | Outputs for up-to-date checks |
| `status` | Custom commands that decide whether work is needed |
| `preconditions` | Conditions that must hold before execution |
| `internal` | Hide helper tasks from `task -l` |
| `aliases` | Alternative task names |
| `platforms` | Restrict to selected OSes |

## Useful Patterns

### Monorepo Includes

```yaml
includes:
  api:
    taskfile: ./services/api
    dir: ./services/api
  web:
    taskfile: ./services/web
    dir: ./services/web
```

### Cached Generation

```yaml
tasks:
  generate:
    cmds:
      - go generate ./...
    sources:
      - "**/*.go"
      - "!**/*_gen.go"
    generates:
      - "**/*_gen.go"
```

### Conditional Execution

```yaml
tasks:
  install:
    cmds:
      - npm install
    status:
      - test -d node_modules
```

### Required Vars

```yaml
tasks:
  deploy:
    cmds:
      - echo "Deploying to {{.ENV}}"
    requires:
      vars: [ENV]
```

## Best Practices

1. Add `desc` so `task -l` stays useful.
2. Use `includes` to keep large repos understandable.
3. Use `sources` and `generates` to avoid rerunning expensive work.
4. Mark helper tasks `internal: true`.
5. Prefer `deps` over manually chaining other tasks.
6. Use `summary` for tasks that need operational context.

## Debugging

```bash
task --dry <name>
task --summary <name>
task -v <name>
```
