# Someday

Ideas that are not committed to a date. Moved here from the aisentry.co roadmap on 2026-08-22.

Nothing on this page is in progress. Nothing here should be cited as a shipping plan, in the README, on the site, or in a pitch. If something moves to committed work it gets a quarter on the site and comes off this list.

## Why these moved

The site carried a Q2 2026 "In Progress — April 2026" block that included MCP Server Scanning. That work had not started, and measurement against real MCP servers since then showed aisentry has no representation of the MCP tool boundary at all. Advertising it as in progress overstated the state of the tool.

The one thing now on the public roadmap is Q3 2026 — MCP tool boundary analysis.

## Agent security

- **Agentic flow analysis** — trace agent chains through LangGraph, CrewAI, AutoGen.
- **RAG pipeline security** — vector DB injection, unsafe loaders, PII in embeddings.
- **VS Code extension** — real-time scanning in the editor.

## Deep analysis

- **Prompt template analyzer** — static analysis for injection vectors in prompt templates.
- **Guardrails scanner** — detect missing NeMo Guardrails, LlamaGuard, Guardrails AI. Note that guardrail *libraries* are currently a large false-positive source for our own detectors - code that names and pattern-matches dangerous operations reads as performing them. This needs the precision work below first.
- **Fine-tuning data security** — PII detection and poisoning indicators in training data.
- **LLM gateway scanner** — audit LiteLLM and AI Gateway proxy configs.

## Advanced

- **Multi-modal security** — image prompt injection, audio input sanitization.
- **Runtime–static bridge** — generate Garak tests from static findings.
- **JavaScript/TypeScript support** — TypeScript is 31% of public MCP servers versus Python's 35%, so this is the largest single coverage gap by language. Blocked on the Python detectors being trustworthy first.
- **Team dashboard** — cloud dashboard with trend tracking.

## Deferred detector work

Beyond the committed Q3 item:

- **S3 missing-consent detection** — flag destructive sinks reachable from a tool parameter with no confirmation gate. Scope strictly to tool bodies; applied broadly it reproduces the absence-of-feature false positives.
- **S4 MCP-specific classes** — tool-description injection, tool shadowing, transport exposure (`stdio` vs unauthenticated `streamable-http`), over-broad resource globs.
- **S5.2 dataflow instead of co-occurrence** for "sensitive data in log" and "LLM output flows to sink". Needs real dataflow, belongs with S2.
- **S5.3 suppress matches inside string literals and regex patterns.**
- **S5.4 stop emitting absence-of-feature findings on wrappers, factories and passthrough methods.**

## Legacy packages

`secscan-cli` and `ai-security-cli` are still live on PyPI, and `deosha/secscan` is still a public unarchived repo. Deprecating and redirecting them to aisentry is unresolved — scope was never decided.
