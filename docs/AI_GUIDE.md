# Working with AI on this project

**AI is allowed and encouraged when it improves your learning and your work.** You are not expected to record every prompt or maintain a running AI activity log. But **you are responsible for understanding, testing and explaining everything you submit**—a pull request is your contribution, even when AI helped write it.

> **Best approach:** try to implement the task yourself first. If you get stuck, write the algorithm in plain English or pseudocode, then ask AI to critique or improve *your plan*. Use AI to write code when it is useful, but never as an excuse to skip understanding the method.

## 1. Before you ask AI

1. Read your GitHub issue. Define the input, output and "done" criteria in your own words.
2. Try a small implementation or write pseudocode:
   - What data goes in, with which columns, units and dates?
   - What are the calculation steps?
   - What should happen on missing/invalid data?
   - What is one simple example whose answer you can calculate by hand?
3. Consult existing code before asking for a new module. Aim for **one small change, one PR**.
4. If you need help, give AI the issue and *your* attempted solution; don't just say "do issue #X."

### Prompt 1 — help write or improve the implementation

Copy this prompt into an AI assistant. Replace the placeholders and share **only** the files/data you are allowed to share.

```text
You are assisting me on a student quantitative-finance research project. I am
responsible for understanding and reviewing the submitted work.

GitHub issue and acceptance criteria:
[PASTE THE RELEVANT ISSUE TEXT]

Relevant existing code / interfaces:
[PASTE THE SMALLEST NECESSARY CODE OR EXPLAIN THE FILES]

My proposed algorithm (in my own words or pseudocode):
[YOUR STEPS HERE]

Please:
1. Review my approach first. Identify missing assumptions, edge cases or
   conceptual mistakes. If an important choice is ambiguous, explain it
   rather than silently deciding for me.
2. Suggest the smallest implementation or improvement consistent with the
   existing repository. Prefer clear Python functions, no unnecessary
   dependencies, and keep data processing separate from notebook narration.
3. Explain inputs, outputs, units, date alignment, and why each key step
   works in simple language.
4. Give at least two tiny hand-checkable examples and focused tests.
5. Flag any risk of look-ahead leakage, adjusted vs unadjusted prices,
   inconsistent return definitions, missing observations or wrong units.
6. Do not invent data, sources, empirical results or successful test runs.
   Say explicitly what I must verify or run myself.

Keep the change small enough for one PR, and tell me what I should be able
to explain to my reviewer.
```

## 2. Review with a fresh perspective

After you've edited the code, **run it yourself** before asking for a review. Prefer a *new AI chat*, with the issue, your code or diff, and any real test output. AI reviews are an additional check, **not a substitute for Seb's PR review**.

### Prompt 2 — act as a skeptical reviewer

```text
Act as a strict reviewer of my proposed GitHub pull request for a student
commodity-ETP research project.

Issue requirements:
[PASTE THE ISSUE TEXT]

Changes / git diff:
[PASTE THE DIFF OR RELEVANT FILES]

Tests I actually ran and their outputs:
[PASTE RESULTS, OR STATE "NOT RUN"]

Please do NOT rubber-stamp this. Look for:
- Incorrect economics, formulas, sign conventions or units.
- Fund total-return / split handling vs spot-price comparisons.
- Off-by-one date alignment or data that was not available at the time.
- Futures expiry/rolling mistakes, missing data and biased sample selection.
- Bad assumptions in regression or unsubstantiated causal claims.
- Unnecessary complexity and divergence from the issue scope.
- Tests that appear to pass but fail to verify the important behavior.

For each finding, give its severity, exact location or code snippet,
why it matters, a minimal suggested fix, and how to test it.
Separate verified bugs from possible concerns and say when you lack
the information to check something.

Finish with three questions I should be able to answer without AI
before I submit this PR. Don't rewrite everything unless I ask.
```

## 3. Minimum verification before opening a PR

- [ ] I can explain *every function or formula I changed* without looking at the AI response.
- [ ] I can describe the **input, output, units and date convention**, and where the data came from.
- [ ] I ran the changed code (or reviewed every source link if this is docs-only). **Do not claim tests were run if they weren't.**
- [ ] I manually checked at least one tiny result: e.g. `F2/F1 - 1`, a one-month return, or growth of $1.
- [ ] I tested a corner case (missing data, mismatched dates, no observations, zero slope, or a small synthetic example).
- [ ] I checked that only information available at that date enters predictors; specifically, *slope at month t must not contain information from the return gap in t+1*.
- [ ] I verified any external economic or data-source claims against primary documentation.
- [ ] I can state **one assumption and one reason the result could mislead**.
- [ ] My PR description states the checks I actually performed; any uncertainties are explicit.

**A useful self-test:** If Seb asks "Why is this line here?" or "What happens if the date is missing?", can you answer in your own words? If not, the PR is not ready yet.

## 4. What AI cannot establish

- It cannot certify that downloaded prices are the right series, correctly adjusted, licensed or available point-in-time. Check provider and fund documentation.
- It cannot make a regression causal or rescue an invalid sample. Check definitions, plots, test split, confidence intervals and limitations.
- "The code looks correct" is not evidence it ran. Execute it and inspect output.
- Avoid sharing passwords, API keys, personal/private data, or restricted licensed datasets with external AI services.

## 5. Course deliverable: short AI-usage note, not a prompt diary

The project brief asks for an **AI-usage note** in the final deliverables. We will keep this lightweight: at the end of the project, write a **short, truthful group-level summary** of where AI helped (for example, brainstorming, boilerplate, debugging, prose review) and **how the resulting work was checked** (tests, manual calculations, source checks, peer review). There is **no requirement in this team's workflow to log every chat or prompt**. Don't claim verification you didn't do.

The standard is human understanding and verification, not a prohibition on AI.
