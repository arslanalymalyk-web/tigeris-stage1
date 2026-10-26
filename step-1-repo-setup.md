# Step 1 — Repository setup and guardrails

> Paste into **Claude Code** (or another coding agent that can read and edit your repository), opened at the repository root. Run only after `README.md`, `CLAUDE.md` and `docs/` are committed to the repository.
>
> Note: the Claude Project used for planning cannot see or change your repository. Step 1 must be run in a tool that has the repository open.

```text
Read CLAUDE.md, README.md, docs/STAGE1_BUILD_BRIEF.md and docs/DECISIONS.md.

Task: Step 1 only — repository setup. No product screens yet.

1. Inspect the repository and report what already exists (files, framework, package manager, CI). Do not change anything until you have reported. If the repository already contains application code, stop and ask me before scaffolding over it.

2. Check these decisions in docs/DECISIONS.md. They must be CONFIRMED or PROVISIONAL. If any is PROPOSED or OPEN, stop and ask me:
   - D-08 stack: Vite + React + TypeScript, front end only
   - D-09 no external AI calls
   - D-12 repository name and team size intentionally unspecified
   - D-13 local preview only

3. Scaffold the app with Vite + React + TypeScript (D-08):
   - Strict TypeScript.
   - Package name: tigeris-ai-os-stage1. Do not add an author, repository URL, organisation or team details (D-12).
   - Folders: src/config, src/domain, src/fixtures, src/calc, src/policy, src/services, src/state, src/ui, src/map, tests/unit, tests/e2e.
   - Scripts: dev, build, preview, lint, typecheck, test (Vitest), test:e2e (Playwright).
   - ESLint + Prettier configuration.
   - One placeholder page that says "TIGERIS AI OS — Stage 1 Demonstrator (setup only)" and shows the text "DEMONSTRATION MODE — synthetic data only".
   - A GitHub Actions workflow (.github/workflows/ci.yml) that runs install, lint, typecheck, test and build on push and pull request. No deploy step (D-13).
   - .gitignore for node_modules, dist, coverage and Playwright output.
   - .nvmrc or "engines" field with the Node LTS version you used; report which version.

4. Add src/config/product.ts with productName "TIGERIS AI OS", descriptor "AI-Native Sovereign Intelligence Operating System" and tagline "Intelligence into Capability. Capital into Sovereign Advantage." in one place, with a comment that the name is provisional (DECISIONS X-04, C-01).

5. Add tests/unit/guardrails.test.ts with two tests marked "todo":
   - "every displayed number and map object has a label and lineage" (Step 3)
   - "no option reaches Approved without a human decision record" (Step 5)
   Also add one real test that passes now: the placeholder page renders "DEMONSTRATION MODE".

6. No network at runtime: no analytics, CDN fonts, external scripts, map tiles, AI SDKs or API clients. Do not install any AI/LLM SDK (D-09). Report every runtime dependency you added and why.

7. Update README.md with a short "Run locally" section (install, dev, preview, test) that matches what you actually built.

Do NOT build screens, fixtures, the map, calculations, policy rules or any business logic.

At the end, report:
- files created or changed
- commands you actually ran and their real results (install, lint, typecheck, test, build)
- anything you could not run, and why
- dependency list with reasons
- assumptions and open questions
Then stop and wait for my review. Do not start Step 2.
```

**You review:**
- the folder structure
- `npm run lint`, `npm run typecheck`, `npm test` and `npm run build` all pass, and the CI run on GitHub is green
- `npm run dev` opens the placeholder page locally
- no AI SDKs, analytics or external runtime calls in `package.json`
