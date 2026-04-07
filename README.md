# E2E Playwright + Lighthouse Tester Skill

GitHub-ready Cursor skill package that adds a reusable `/tester` command for end-to-end Playwright checks and Lighthouse audits.

The workflow is discovery-first, prefers native project scripts, and pushes toward **100/100** Lighthouse outcomes with explicit gap reporting when perfect scores are not yet achievable.

![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)
![Agent Skill](https://img.shields.io/badge/type-agent--skill-7c3aed)
![E2E + Lighthouse](https://img.shields.io/badge/tests-Playwright%20%2B%20Lighthouse-0ea5e9)

## Quick start

```bash
npx skills add erikfiala/e2e-tester -a cursor
```

Then in Cursor chat:

```text
/tester
```

## What this includes

- Cursor skill: `.cursor/skills/tester/SKILL.md`
- Slash command: `.cursor/commands/tester.md`
- Discovery helper: `.cursor/skills/tester/scripts/discover_audit_targets.py`
- MIT license

## Install

### Skills package installer (multi-agent)

```bash
npx skills add erikfiala/e2e-tester
```

Install for a specific agent:

```bash
npx skills add erikfiala/e2e-tester -a cursor
npx skills add erikfiala/e2e-tester -a copilot
npx skills add erikfiala/e2e-tester -a cline
npx skills add erikfiala/e2e-tester -a windsurf
```

Install once, use in future sessions.

### Claude plugin system (optional path)

```bash
claude plugin marketplace add erikfiala/e2e-tester
claude plugin install e2e-tester@e2e-tester
```

### Codex (optional path)

1. Clone this repo.
2. Open Codex in the repo.
3. Run `/plugins`.
4. Search `e2e-tester`.
5. Install the plugin.

Install once, use in future sessions.

### Manual project install

Copy this repository's `.cursor` directory into your target project root.

### Manual global install (Cursor)

```bash
mkdir -p ~/.cursor/skills/tester ~/.cursor/commands
cp -R .cursor/skills/tester/* ~/.cursor/skills/tester/
cp .cursor/commands/tester.md ~/.cursor/commands/tester.md
```

## Prerequisites

- Node.js + npm (`npx`)
- Python 3
- Playwright browsers installed when Playwright is used:

```bash
npx playwright install
```

## Usage

Run from Cursor chat:

```text
/tester
```

Or ask naturally:

```text
Run e2e + Lighthouse using the tester skill.
```

## Coverage and scoring objective

The tester aims to run Lighthouse for each target across:

- `light-desktop`
- `light-mobile`
- `dark-desktop`
- `dark-mobile`

And attempts Lighthouse categories:

- `performance`
- `accessibility`
- `best-practices`
- `seo`
- `pwa` (when supported by tool version and app signals)

Goal: always strive for **100/100** in Lighthouse categories and Web Vitals-related audits, then report specific blockers and highest-impact fixes.

## Output contract

Each `/tester` run should end with:

- Commands run (native vs adapted)
- Playwright findings (failures, flaky hints, console/page/network issues)
- Lighthouse scores for:
  - `light-desktop`
  - `light-mobile`
  - `dark-desktop`
  - `dark-mobile`
- A **100/100 gap analysis** with highest-impact next fixes
- Explicit coverage gaps and blockers

## Customization

- Add or improve package scripts in your app repo (for example `perf:lighthouse`, `test:e2e`, `smoke`) so discovery can pick them first.
- Tune your own Playwright and Lighthouse runner scripts; this skill prefers existing project conventions over ad-hoc commands.

## Publish checklist (GitHub)

- Repo name: `e2e-tester` (or `cursor-e2e-tester`)
- Visibility: public
- Topics: `cursor`, `playwright`, `lighthouse`, `e2e`, `agent-skill`
- Confirm `.cursor/commands/tester.md` and `.cursor/skills/tester/SKILL.md` exist in default branch
- Optional: add a repo description like `Reusable /tester skill for Playwright + Lighthouse audits`

## Star this repo

If this tester saves you tokens, time, or CI debugging pain, please star the repo.

[![Star History Chart](https://api.star-history.com/svg?repos=erikfiala/e2e-tester&type=Date)](https://www.star-history.com/#erikfiala/e2e-tester&Date)
