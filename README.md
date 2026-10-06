# aisona-lab

AI engineer building **deterministic harnesses** around agents.

## Thesis → trailer

| Role | Repo | Idea |
|------|------|------|
| **Thesis / auth** | [agent-action-gate](https://github.com/aisona-lab/agent-action-gate) | Deterministic allow / deny / human-approval for tool calls. **Zero LLM** in the auth path. |
| **Trailer** | [lazycoder](https://github.com/aisona-lab/lazycoder) | Rubric code review (APPROVE / REQUEST_CHANGES / BLOCK). Offline prove & replay without a key; live review optional. |

Related: [skill-guard](https://github.com/aisona-lab/skill-guard) — static pre-install audit for Agent Skills.

## Hiring skim

**Thesis → trailer:** [agent-action-gate](https://github.com/aisona-lab/agent-action-gate) is the auth thesis: local-first, deterministic allow / deny / human approval, with zero LLM keys in `decide()`. [lazycoder](https://github.com/aisona-lab/lazycoder) is the optional trailer: rubric review with deterministic replay and optional live review; neither repo is a hard dependency of the other.

**Proof → security:** The gate's offline proof is [`scripts/prove.sh`](https://github.com/aisona-lab/agent-action-gate/blob/main/scripts/prove.sh). [`aag decide --format sarif`](https://github.com/aisona-lab/agent-action-gate#sarif-export-offline) exports SARIF, and the [SARIF example](https://github.com/aisona-lab/agent-action-gate/tree/main/examples/ci-sarif) shows upload to GitHub **Security → Code scanning**. [Stage 3a path/glob](https://github.com/aisona-lab/agent-action-gate/commit/676d3369fa08acc25316748e8de395a34cf11624) covers string-only `glob` / `startswith` matching with fixtures; residual: no path normalization, symlink resolution, or `..` collapsing.

**Honesty boundary:** Agent Action Gate is source-install for now; no live PyPI release is claimed. lazycoder's Stage 2 corpus **LIVE** scoring remains pending credits; the claim here is offline proof / replay. Optional adjacent one-liner: [skill-guard](https://github.com/aisona-lab/skill-guard) — static pre-install audit for Agent Skills.

## Delivery loop

Short loop from each repo's `LEARNINGS.md`: **SPEC → PLAN → OK → smallest unit → prove with a command → merge → clean tree.** No invented precision.

## Start here

1. [agent-action-gate](https://github.com/aisona-lab/agent-action-gate)
2. [lazycoder](https://github.com/aisona-lab/lazycoder)
3. [skill-guard](https://github.com/aisona-lab/skill-guard) *(optional)*
