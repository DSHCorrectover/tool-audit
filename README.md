# tool-audit — Protocol-agnostic tool-call authorization audit

**Did your agent exceed the authorization it was actually granted?** Not "is this tool whitelisted" — but "was every parameter and target of this call approved?" Isolation-legal API calls to the wrong server are still unacceptable.

Tool-call authorization needs verdicts per parameter, per target, per runtime state — **before execution**, with tamper-evident receipts after.

## What you get (free, replayable, CC0)

- **576 verdict anchors** — exhaustive cross-product of six dimensions: delegation shape × revocation × tool version × side effect × runtime state × integrity. Not hand-tuned: the verdict distribution is a mathematical consequence of the dimension definitions.
- **Protocol-agnostic** — the same verdict shape lands for MCP, OpenAI function calling, Google ADK, LangGraph, custom runtimes. MCP is one sampling surface among several.
- **Live page**: https://dshcorrectover.github.io/tool-audit/

## Related

- Verdict table + public CI runs (green and red): [correctover-recovery-admission/INTEGRATION-SURFACE.md](https://github.com/DSHCorrectover/correctover-recovery-admission/blob/main/INTEGRATION-SURFACE.md)
- Sample assessment of our own engine (adversarial read encouraged): [ecr-arena/samples/first-report.md](https://github.com/DSHCorrectover/ecr-arena/blob/main/samples/first-report.md)

---

**Commercial verification engagements** — post-migration authorization integrity assessment, court-ready dossier: [tiers & free sample](https://dshcorrectover.github.io/correctover-recovery-admission/services.html) · wangguigui@correctover.com

*AI-assisted disclosure: this repository is maintained with AI assistance, reviewed by Guigui Wang.*
