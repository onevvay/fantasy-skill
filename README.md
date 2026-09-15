# fantasy-skill

Personal skills directory for `npx skills`.

[中文](README.zh-CN.md) | **English**

## Layout

Skills will be added under `skills/<skill-name>/`.

Published skills:

- `tapd` — TAPD requirements, tasks, bugs, iterations, timesheets, comments, and controlled bug-fix workflow.

Install it with:

```bash
npx skills add onevvay/fantasy-skill --skill tapd
```

## TAPD Skill Workflow

The `tapd` skill uses a gated bug-fix workflow rather than treating a code change as a completed TAPD resolution.

1. **Read first**: load the bug with its full TAPD ID, current status, description, and comments. For a `重新打开` bug, comments must be fully paged and read before any status change, comment, code change, or repair preparation.
2. **Read-only diagnosis**: inspect the workflow transitions, reproduce the issue, and collect environment, version, request, log, and screenshot evidence without changing code or TAPD state.
3. **Plan checkpoint**: present the confirmed facts, suspected root cause, scope, tests, E2E plan, screenshot evidence, commit message, and TAPD update plan. Wait for explicit user approval before repair. An explicit instruction such as “直接修复” may skip this checkpoint, but never skips the read, E2E, screenshot, or status safeguards.
4. **Handle and repair**: after approval or an explicit bypass, move the bug through the configured `接受/处理` transition, publish the initial HTML comment, then make the minimal fix and regression test. Any Git commit for the bug must contain the complete 19-digit TAPD bug ID in its subject.
5. **Real acceptance**: validate the original scenario in the matching dev/test environment. UI or user-flow bugs also require accessible screenshot evidence bound to the bug ID, environment, version, URL, time, and steps.
6. **Close with evidence**: publish the final root-cause, fix, impact, E2E, and screenshot evidence comment first; only then move the bug to an actually reachable resolved or later state. Failed or ambiguous writes stop the workflow and trigger read-back verification instead of blind retries.

The skill keeps TAPD comments in HTML, avoids duplicate comments, and never treats local tests, builds, commits, or pull requests alone as proof of business completion.
