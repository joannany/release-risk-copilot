# AI Release Risk Copilot

**Interactive product concept for go/no-go decision support on frontier model releases.**

🔗 **Live demo:** https://joannany.github.io/release-risk-copilot/

---

## What this is (and isn't)

This is a **design sandbox with a simulated engine** — no live model calls, no real telemetry. All data is generated in-browser and labeled as such. It exists to demonstrate a *decision architecture*, not a production pipeline.

The thesis it encodes: **release decisions fail less from weak models than from unaudited evidence and unmeasured false-go risk.** Aggregate benchmarks can improve while critical workflow slices silently regress — and a release process that can't catch that asymmetry will eventually ship the regression.

## What the sandbox demonstrates

- **Trust-weighted evidence ingestion** — source classes (internal evals, production telemetry, reviewed incidents, model-generated narratives) are confidence-weighted *before* any claim enters the decision packet.
- **A gated validation pipeline (L1–L5)** — structural schema gates with bounded repair loops, citation verification that escalates to a human approval gate on failure, and an append-only audit log: decisions are recorded, never rewritten.
- **Failure-mode injection** — seed the pipeline with a hidden slice regression or a safety-threshold breach, then verify the gates catch it. The interesting metric isn't accuracy; it's **false-go rate** (shipped-when-should-hold) and **unsupported-claim escape**.
- **Evaluation of the evaluator** — a 100-scenario validation harness with ground-truth verdicts, measuring regression recall, claim-support precision, and escape rates. An evaluation pipeline you haven't benchmarked is itself an unaudited claim.
- **Unit economics** — a gross-margin modeler for running this pipeline as an enterprise service: prompt-cache pricing asymmetry, per-evaluation COGS allocation, and an internally consistent comparison against an uncached cascade. Prices are illustrative defaults, clearly marked.

One design decision worth noting: **telemetry (runs, token counts, latency, cost) is carried on the state object but is never an input to the verdict.** Execution logs and decision logic are deliberately separated.

## How this fits my broader work

This sandbox is the *product-vision layer* of an evaluation portfolio whose working layers live in companion repos:

- [**gpt-drift**](https://github.com/joannany/gpt-drift) — open-source behavioral regression testing for LLMs (real runs: standardized probes, effect-size quantification, CI/CD deployment gating)
- [**mini-forge**](https://github.com/joannany/mini-forge) — post-training evaluation prototype with promotion-gate logic and deployment trade-off documentation

Background: I previously led post-deployment evaluation for regulated clinical AI (Lunit INSIGHT Manager 2.0) and hold a filed patent on AI lifecycle evaluation under delayed or partial ground truth (PCT/KR2025/015661). This sandbox applies the same decision discipline to frontier model releases.

## Running it

It's a single self-contained `index.html` (Tailwind via CDN). Open it in a browser, or visit the live page. No build step, no dependencies, no API keys.

## Built with

Designed and prototyped independently with agentic development support, owning the decision architecture, evaluation logic, product framing, and economics modeling end-to-end.

---

*[LinkedIn](https://www.linkedin.com/in/annajoai)*
