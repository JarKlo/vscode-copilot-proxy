# Sprint 5 – Producer Plan (DOCS_NAMESPACE: security‑hardening)

**Run folder:** `docs/security-hardening/sprints/sprint-5/runs/run-20260902-1200`

## Objectives
1. **Port default change** – document the new default port 4141 (already merged).
2. **Auth & CORS notes** – add brief notes to `docs/CONFIGURATION.md` that `/health` is the only unauthenticated endpoint and that logs are only in‑process (Output channel).
3. **Release** – merge the four completed sprints, tag version v0.0.19, publish the VSIX.
4. **Retrospective** – capture any open gaps (rate‑limiting, connection limits, security headers) for future sprint.

## Acceptance Criteria
- All documentation updated to reference port 4141.
- `producer-progress.md` tracks the above tasks (initially empty, will be filled during execution).
- `producer-closeout.md` will record merge commit SHA, release tag, and a short retrospective.

## Next Steps
- Create the run folder and accompanying markdown files.
- Update `LATEST.md` pointer (not required for this sprint as no prior sprint folder exists).
- Hand off to Dev/QA agents to verify the merge and release.
