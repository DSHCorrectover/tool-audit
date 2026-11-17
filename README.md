# tool-audit — tool-call authorization as a per-call verdict problem

**The observation, with a line number.** crewAI's `BaseTool` interface (`crewai/tools/base_tool.py:353` on main) exposes no call-time authorization parameters at all: a tool receives inputs and a context, but never receives a machine-checkable statement of *who is calling, under which grant, with what freshness*. Same shape in OpenAI function calling and LangGraph tool APIs — the hole is interface-level, not library-specific.

**Why existing designs can't hold this.** Whitelists and permission matrices answer "is this tool allowed for this principal" — a static, install-time question. What breaks in practice is per-call: delegation carries through retries with the same principal (`agent/core.py` `_handle_execution_error` re-enters `execute_task` with no actor change), targets differ from what was approved, and tool versions drift under a stale grant. None of these are expressible as a whitelist row; they need a verdict per call over `(principal, scope, side_effect_class, freshness)`.

**What this repo is.** The live audit page (576 verdict anchors, six-dimension cross-product: delegation shape × revocation × tool version × side effect × runtime state × integrity) and the reasoning behind each dimension.

- **Live page**: https://dshcorrectover.github.io/tool-audit/
- **Verdict table + public CI runs (green AND red)**: [correctover-recovery-admission/INTEGRATION-SURFACE.md](https://github.com/DSHCorrectover/correctover-recovery-admission/blob/main/INTEGRATION-SURFACE.md)
- **Sample verdict on our own engine** (adversarial read encouraged): [ecr-arena/samples/first-report.md](https://github.com/DSHCorrectover/ecr-arena/blob/main/samples/first-report.md)

The verdict table is CC0. Implement it yourself — that's the point: a verdict you can reproduce beats any README.

*AI-assisted disclosure: maintained with AI assistance, reviewed by Guigui Wang.*
