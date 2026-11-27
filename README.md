# aisona-lab

Production AI systems (**80%**) and applied research (**20%**) focused on **deterministic verification harnesses** around agents.

## Why deterministic verification

In [`peacethefrontier-research`](https://github.com/aisona-lab/peacethefrontier-research), **H1** ([*From Copilots to Autonomous Agents*](https://github.com/aisona-lab/peacethefrontier-research/blob/main/src/content/articulos/en/from-copilots-to-autonomous-agents.mdx)) models autonomous delegation as verification economics:

`E[C_agent(t)] = c_compute(t) + c_audit + (1 − p(t)^K) × (d_det(t) × c_rec + (1 − d_det(t)) × L_sector)`

Autonomous infrastructure only beats copilots when net cost drops and residual tail risk `(1 − p(t)^K) × (1 − d_det(t)) ≤ ε_sector` stays bounded. Every engineering repo below targets the same two levers: pushing deterministic detection `d_det` toward `1.0` while driving per-check audit cost `c_audit` toward `$0`.

## Pinned portfolio

| # | Repo | Role | Verified metrics & capabilities |
|---|---|---|---|
| 1 | [agent-action-gate](https://github.com/aisona-lab/agent-action-gate) | Runtime deterministic tool-call policy gate (`v0.2.0`) | `0.004–0.06 ms` p50 (`Policy.decide` `0.0041 ms`, memory `0.0393 ms`, SQLite `0.0603 ms`), `61/61` evals (`FP=0`, `FN=0`), `$0.000/1k` calls, SQLite `BEGIN IMMEDIATE` budgets, SARIF 2.1.0, Docker |
| 2 | [skill-guard](https://github.com/aisona-lab/skill-guard) | Static pre-install supply-chain analyzer (`v0.2.3`) | `0/73` OOD false-`BLOCK` (`11/73` `WARN`), `25/25` adversarial, `8/8` OOD-unsafe (`FN=0/8`), `17/17` core unsafe (`0/9` FPR), `$0.000/1k` scans, `102` tests, Action + Docker + PyPI (`aisona-skill-guard`) |
| 3 | [lazycoder](https://github.com/aisona-lab/lazycoder) | Deterministic diff-review harness (`v0.3.0`) | `213` offline tests, pre-LLM secret redaction, seeded canaries, append-only JSONL `replay`, `$0.000/1k` offline mode, Action + Docker + PyPI; Stage 1 (`0/13`, P `0.17` / R `0.92`) & Stage 2 (`86%–100%` quiet, `1–5/15` hunk recall) stay advisory (`fail-on: never`) |
| 4 | [rag-eval-gate](https://github.com/aisona-lab/rag-eval-gate) | Hybrid RAG + cost/confidence router + CI eval gate (`v0.1.0`) | BM25 + dense + RRF + rerank, `<0.1 ms` p95 local router (`0.0644–0.084 ms`) saving `74.47%` vs always-frontier (`$0.5753` vs `$2.2537/1k`), `recall@5=1.0000`, `MRR=0.9583`, `faith=1.0000`, FastAPI + Docker + `rag-eval gate` + Action |
| 5 | [owninfra](https://github.com/aisona-lab/owninfra) | TypeScript + AWS CDK deterministic blueprint compiler *(pre-alpha, paused)* | Schema/semantic `validate` (L0), local Next.js/Postgres `generate`/`dev`, `cdk synth` with `cdk-nag` (`AwsSolutions`) and idle-cost guards (Aurora Serverless v2 `min=0` ACU auto-pause, zero NAT/EC2 idle billing) |
| 6 | [peacethefrontier-research](https://github.com/aisona-lab/peacethefrontier-research) | Bilingual applied research portfolio (`v0.2.0` Scenario) | Astro 7 + strict TypeScript, formal H1–H3 simulation models (`3,300` / `500` / `1,500` rows), `SHA-256`-verified manifests, [`peacethefrontier.com`](https://peacethefrontier.com), H1 verification-economics thesis (`d_det` / `c_audit`) |

## Honesty boundary

- **Releases & PyPI**: `skill-guard` (`aisona-skill-guard`) and `lazycoder` have OIDC PyPI workflows (`v0.2.3` / `v0.3.0` tags pending release); `agent-action-gate` (`v0.2.0`) and `rag-eval-gate` (`v0.1.0`) provide local wheel builds, Dockerfiles, and OIDC publish stubs with no live PyPI package published yet.
- **Offline vs. live scope**: Latency, `$0.000/1k` cost, and gate pass rates above come from deterministic offline suites and local synthetic/golden corpora. `lazycoder` enforces `fail-on: never` in CI because live Stage 2 hunk recall (`1–5/15`) is not calibrated for hard blocking.
- **Paused & synthetic work**: `owninfra` is local-only pre-alpha (`deploy`, `destroy`, and L1+ harness unimplemented; paused). `peacethefrontier-research` H1–H3 outputs are parameterized simulations (`synthetic=true`), with `h1-empirico` at `0` observed rows (`collection-pending`) and H2/H3 frozen pending H1 calibration.
