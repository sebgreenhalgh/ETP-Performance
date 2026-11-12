# How we work on GitHub

**Audience:** first-time GitHub contributors to the Commodity ETP Performance Gap project.  
**Lead / merge owner:** Seb. **Only Seb merges pull requests into `main`.** Contributors do **not** commit directly to `main`. This is our team rule; it is **not automatically enforced** by this document.

> **For the first session:** everyone completes one small, documentation-only issue (#3, #4 or #5) before taking on analysis code.

## The four things to understand

| Term | Meaning | Here |
| --- | --- | --- |
| **Issue** | A task with a goal, dependencies and acceptance criteria | The single place we agree what to build |
| **Branch** | A safe copy of the project's working history | Make one branch per issue |
| **Commit** | A saved checkpoint of changed files | Write messages describing what changed |
| **Pull request (PR)** | A proposal to merge branch changes into `main` | Seb reviews; only Seb merges |

**Main rule:** one issue → one branch → one focused PR → review → merge. Aim for changes small enough that another student can review them in one sitting.

## 1. Pick an issue

1. Open [the roadmap, issue #1](https://github.com/sebgreenhalgh/ETP-Performance/issues/1).
2. Choose a task with **all dependencies merged**, starting with a green beginner issue.
3. Comment on the issue: **"I'd like to take this—my plan is ...; can I start?"** Agree ownership with the group/lead, then assign the issue if you have permissions.
4. Read the acceptance criteria and ask if any definition is unclear **before coding**.
5. Do not start a downstream issue if its underlying data/method choices are still being changed.

## 2. Create a branch (never work directly on main)

Name it `issue-<number>-short-description`, for example **`issue-3-glossary`**.

### Simple browser-first route (great for your first PR)

1. Open the repository and navigate to the relevant file (or choose **Add file → Create new file**).
2. Use the branch selector or the edit screen's option to **create a new branch** based on `main`, not to commit straight to `main`.
3. Name the branch `issue-3-glossary`. Create or edit only the relevant Markdown file.
4. Write a clear commit message such as `docs: define commodity ETP terms`; commit to **your branch**.
5. Open **Pull requests → New pull request**; set **base = main** and **compare = your issue branch**.
6. If unsure of the current GitHub interface, ask at the meeting—never click "Commit directly to main" by default.

### Optional terminal route (for Python work later)

```bash
git clone https://github.com/sebgreenhalgh/ETP-Performance.git
cd ETP-Performance
git switch main
git pull
git switch -c issue-3-glossary

# Edit the requested file, then:
git status
git add docs/glossary.md
git commit -m "docs: define commodity ETP terms"
git push -u origin issue-3-glossary
```

If you already cloned the repository, skip `git clone`; start with `git switch main && git pull`.

## 3. Make a **small, verifiable** change

- Follow your issue's scope and acceptance criteria; use existing functions where possible.
- For Markdown: check links, spelling and whether claims are properly sourced.
- For Python: run your modified code and appropriate tests. Start with **tiny hand-checkable examples**. If you cannot explain a line, use [the AI guide](docs/AI_GUIDE.md) or ask a teammate.
- Never invent financial prices, fill missing futures months without an approved method, or silently change return/date definitions.
- Do not commit passwords, access tokens, restricted raw datasets, `.venv/`, huge generated data, or notebook checkpoints.
- Prefer logic in `src/` and **one final notebook** in `notebooks/`; avoid several people editing the same notebook at the same time.

## 4. Open a PR

Choose **base `main`** and **compare your issue branch**. A good PR contains:

```text
Title: Docs: explain key commodity ETP terms

Closes #3

What changed?
- Added 11 glossary definitions and a concrete roll example.

How did I verify it?
- Read each definition against provider documentation.
- Checked source links.

Questions / limitations:
- Still confirming the exact UNG roll schedule.
```

- Add **`Closes #3`** (use your own issue number) in the PR body so GitHub can close the issue when merged.
- Request **Seb** as reviewer. If you don't see the reviewer control, paste the PR link in the group chat and tag Seb.
- Keep feedback in the PR comments where possible. **A request for changes is normal**—respond and push more commits to the same branch.
- Do not open a second PR for the same issue just because feedback arrived.
- Never press **Merge pull request**: Seb does the final review and merge.

## 5. Seb's review / merge checklist

Seb checks:
- [ ] PR corresponds to one issue and satisfies its acceptance criteria.
- [ ] Work is intelligible, documented, and not AI-generated code the author cannot explain.
- [ ] Calculations and tests have evidence; dates, source availability and return units are defensible.
- [ ] No accidental data leaks, secrets, unlicensed raw datasets or unrelated changes.
- [ ] No conflicts with other PRs; notebook still runs after integration where relevant.
- [ ] Merge **only** after feedback is addressed (prefer squash merge for a clean history).
- [ ] Issue closes, or remaining work is clearly split into a follow-up issue.

**Important:** this file expresses policy, not permissions. If enforced lead-only merging is required, Seb must configure GitHub branch protection/rulesets and repository collaborator permissions where supported.

## 6. After your PR is merged

1. Confirm the issue was closed, or note what's still outstanding.
2. Sync your local `main` with `git switch main && git pull`.
3. Pick your next **unblocked** issue from [the roadmap](https://github.com/sebgreenhalgh/ETP-Performance/issues/1), and repeat.

### How to respond when something goes wrong

- **Merge conflict?** Stop and ask Seb to help synchronize your branch; don't overwrite someone else's changes.
- **PR feels too big?** Split it into independently reviewable issues/PRs.
- **Source or methodology uncertain?** Comment on the issue; record the decision in `docs/decision_log.md` once agreed.
- **Want to use AI?** Completely fine, but run/test and understand what it produced; see [AI guide](docs/AI_GUIDE.md).

## Good first PRs

- [#3 — Write a commodity ETP glossary](https://github.com/sebgreenhalgh/ETP-Performance/issues/3)
- [#4 — Make a data-source availability matrix](https://github.com/sebgreenhalgh/ETP-Performance/issues/4)
- [#5 — Build a report outline and figure checklist](https://github.com/sebgreenhalgh/ETP-Performance/issues/5)

No coding experience is required to complete these. The goal is to practice the full cycle **issue → branch → commit → PR → review**.
