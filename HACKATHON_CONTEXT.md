# HRL X GitLab Hackathon — Master Context & Handoff Prompt

> **Copy-paste this entire file into your new console conversation to resume with 100% state, project IDs, active MRs, and verified 0-MR issue targets.**

---

## 1. Identity, Workspace & Repository Coordinates

- **Contributor**: Pavan Kumar Sadashiv (`@hrlpavan`)
  - **GitLab User ID**: `41966919` | **Profile**: https://gitlab.com/hrlpavan
  - **GitHub Profile**: https://github.com/hrlpavan
  - **Git Author Email**: `pavan@hrlpavan.dev`
  - **Hackathon Portal**: https://contributors.gitlab.com/hackathon *(Registered & rules accepted)*
- **Command Center Repo (`HRL X GitLab Hackathon`)**:
  - **Local Path**: `/Users/pavankumars/.gemini/antigravity/scratch/hrl-x-gitlab-hackathon`
  - **GitLab Remote**: https://gitlab.com/hrlpavan/hrl-x-gitlab-hackathon *(Project ID: `87398369`)*
  - **GitHub Remote**: https://github.com/hrlpavan/hrl-x-gitlab-hackathon
- **Upstream vs. Community Fork Project IDs (for GitLab MCP / API calls)**:
  | Repository | Upstream Project ID | Community Fork Project ID (`gitlab-community/...`) | Local Clone Path |
  | :--- | :--- | :--- | :--- |
  | `gitlab-org/gitlab` | `278964` | `41372369` | *(Use GitLab MCP `get_file_contents` / `push_files` on `41372369`)* |
  | `gitlab-org/omnibus-gitlab` | `20699` | `44355627` | `/Users/pavankumars/.gemini/antigravity/scratch/omnibus-gitlab` |
  | `gitlab-org/modelops/applied-ml/code-suggestions/ai-assist` | `39903947` | `61015838` | `/Users/pavankumars/.gemini/antigravity/scratch/ai-assist` |

---

## 2. Active Merge Requests (Monitor & Turn Around Feedback Immediately)

| MR | Title | Source Branch (Community Fork) | Reviewer | Pipeline & Discussion State | Next Action |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **[omnibus-gitlab!9851](https://gitlab.com/gitlab-org/omnibus-gitlab/-/merge_requests/9851)** | `Document Mattermost self-signed certificate handling in Docker` | `hrlpavan-doc-mattermost-docker-ssl` (`44355627`) | `@eread` (Evan Read) | **Pipeline [#2927261873](https://gitlab.com/gitlab-community/gitlab-org/omnibus-gitlab/-/pipelines/2927261873) `success`**<br>`blocking_discussions_resolved: true` | Addressed `@eread`'s feedback in commit `0c0d324d` (reverted 6 `doc-locale/` files so only `doc/settings/ssl/ssl_troubleshooting.md` is touched). Check for `@eread`'s approval/merge. |
| **[ai-assist!7251](https://gitlab.com/gitlab-org/modelops/applied-ml/code-suggestions/ai-assist/-/merge_requests/7251)** | `feat(model-selection): add Gemini 4 Argon to model registry` | `hrlpavan-add-gemini-4-argon` (`61015838`) | `@dblessing` (Drew Blessing) | **Pipeline [#2909374146](https://gitlab.com/gitlab-community/gitlab-org/modelops/applied-ml/code-suggestions/ai-assist/-/pipelines/2909374146) `success` (24/24)**<br>`blocking_discussions_resolved: true` | Transitioned to `workflow::ready for review` via `@gitlab-bot ready` on Oct 8. Monitor for `@dblessing`'s review. |

*(Note: Previous MRs `gitlab!260212` on `#584258` and `gitlab!259119` on `#595159` were closed by maintainers because `#584258` was no longer reproducible upstream and `#595159` already had competing community MR `!260039`.)*

---

## 3. GitLab Hackathon Winning Strategy & Execution Protocol

1. **Pre-Flight Zero-Conflict Check (Mandatory Gate)**:
   - Before writing code for any issue, query `GET /api/v4/projects/:id/issues/:iid` and `GET /api/v4/projects/:id/issues/:iid/related_merge_requests`.
   - Verify **`assignees == []`** AND **`merge_requests_count == 0`**.
   - **Claim the issue first**: Post a comment (`@gitlab-bot assign` or ask to be assigned) before opening the MR to prevent duplicate work.
2. **Prioritize High-Yield Multipliers**:
   - Target `community-bonus::100` / `community-bonus::200` issues (**~230 pts**) and `weight: 1` + `quick win` + `Seeking community contributions` issues (**~90 pts**).
3. **Speed Up Review & Merge Time**:
   - **Keep MRs small and atomic**: Never include unrelated file changes or `doc-locale/` edits.
   - **Ensure clean pipelines on first push**: Run local unit/lint checks (`pytest`/`ruff` in `ai-assist`, `rubocop`/`rspec` or `docs-lint` rules in `gitlab`) and include proper commit trailers (`Changelog: added|fixed|changed` when required).
   - **Follow bot feedback immediately**: Resolve Danger bot warnings, add missing labels (`@gitlab-bot label ...`), and run **`@gitlab-bot ready`** as soon as the pipeline is green.
   - **Resolve all discussions**: Ensure `blocking_discussions_resolved: true` so nothing blocks maintainer merge.

---

## 4. Verified Unassigned, `0-MR` Target Queue (Ready to Claim & Ship)

All 7 issues below were verified via the GitLab API on `2026-10-08T21:50+05:30` to have **`assignees: []`** and **`merge_requests_count: 0`**:

### Tier 1: Bonus Multiplier (`community-bonus::100` — ~230 Points)
1. **[gitlab#592471](https://gitlab.com/gitlab-org/gitlab/-/work_items/592471)** — *Remote workflows can not easily be identified*
   - **Project ID**: `278964` | **Fork ID**: `41372369`
   - **Labels**: `community-bonus::100`, `automation:quick-win-judged`, `group::agent execution`, `type::maintenance`, `workflow::ready for development`
   - **Open MRs**: `0` | **Assignees**: `[]`

### Tier 2: Ultra-Fast CI (`ai-assist` — 3-Minute Pipelines, ~90 Points Each)
2. **[ai-assist#2449](https://gitlab.com/gitlab-org/modelops/applied-ml/code-suggestions/ai-assist/-/work_items/2449)** — *fix: JSON schema validation fails for fields with `maxLength` or `maxItems`*
   - **Project ID**: `39903947` | **Fork ID**: `61015838` | **Local Clone**: `/Users/pavankumars/.gemini/antigravity/scratch/ai-assist`
   - **Labels**: `quick win`, `automation:quick-win`, `type::bug`, `group::ai core infra`
   - **Fix**: Cast float `maxLength` and `maxItems` values to `int` in `json_schema_to_pydantic` + add unit test.
3. **[ai-assist#1939](https://gitlab.com/gitlab-org/modelops/applied-ml/code-suggestions/ai-assist/-/work_items/1939)** — *Remove unnecessary `git fetch --unshallow` step for remote flows*
   - **Project ID**: `39903947` | **Fork ID**: `61015838` | **Local Clone**: `/Users/pavankumars/.gemini/antigravity/scratch/ai-assist`
   - **Labels**: `quick win`, `automation:quick-win`, `backend`, `maintenance::performance`, `type::maintenance`
   - **Fix**: Remove the redundant `git fetch --unshallow` step in remote flows + update corresponding unit test.

### Tier 3: Atomic 1-File Specs & Docs (`gitlab-org/gitlab` — Weight 1 Quick Wins)
4. **[gitlab#605149](https://gitlab.com/gitlab-org/gitlab/-/work_items/605149)** — *Remove unnecessary test from `ai_catalog_item_spec.js`*
   - **Project ID**: `278964` | **Fork ID**: `41372369`
   - **Labels**: `quick win`, `automation:quick-win`, `weight: 1`, `frontend`, `group::ai catalog`, `type::maintenance`
   - **Fix**: Delete the single redundant test block in `ee/spec/frontend/ai/` as specified in the issue description.
5. **[gitlab#603652](https://gitlab.com/gitlab-org/gitlab/-/work_items/603652)** — *Update docs to mark GitLab Secrets Manager as GA*
   - **Project ID**: `278964` | **Fork ID**: `41372369`
   - **Labels**: `quick win`, `automation:quick-win`, `weight: 1`, `docs-only`, `documentation`, `workflow::ready for development`
   - **Fix**: `docs-only` MR updating Secrets Manager availability tier to GA (~4 min docs pipeline, fast Technical Writing merge).
6. **[gitlab#628749](https://gitlab.com/gitlab-org/gitlab/-/work_items/628749)** — *Clean up `block_jwt_for_reclaimed_paths` specs: split multiple describe blocks into separate files*
   - **Project ID**: `278964` | **Fork ID**: `41372369`
   - **Labels**: `quick win`, `automation:quick-win`, `weight: 1`, `backend`, `maintenance::refactor`, `type::maintenance`
   - **Fix**: Split multiple top-level `RSpec.describe` blocks into separate spec files per maintainer follow-up from `!254058`.
7. **[gitlab#600372](https://gitlab.com/gitlab-org/gitlab/-/work_items/600372)** — *Secrets Manager: Update AuditLog spec fixtures for 3-level OpenBao paths*
   - **Project ID**: `278964` | **Fork ID**: `41372369`
   - **Labels**: `quick win`, `automation:quick-win`, `weight: 1`, `backend`, `maintenance::test-gap`
   - **Fix**: Update RSpec fixture paths in `AuditLog` specs from 2-level to 3-level OpenBao paths.

---

## 5. Prompt to Start the New Console Session

> **Prompt**:
> *"We are running our HRL X GitLab Hackathon campaign from `/Users/pavankumars/.gemini/antigravity/scratch/hrl-x-gitlab-hackathon`. First, check the status of our 2 active MRs (`omnibus-gitlab!9851` and `ai-assist!7251`) for any new reviewer comments. Then let's immediately claim and ship our next unassigned 0-MR targets starting with `ai-assist#2449`, `ai-assist#1939`, and `gitlab#592471`!"*
