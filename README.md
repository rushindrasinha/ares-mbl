# Ares MBL — Model Behavior Layer

> Drop-in system prompt that suppresses 8 documented AI failure modes.

Most models are not frustrating because they are incapable.
They are frustrating because they hedge, flatter, claim completion early, avoid verification, and ask permission for obvious next steps.

**Ares MBL** is a portable behavior layer you can drop into any strong model to make it behave with more discipline.

Works best with GPT, Gemini, Claude-adjacent workflows, Codex, and capable local models.

## The payoff

This repo gives you three things:

1. a named framework for the 8 failure modes that make models annoying in real work
2. a practical cognitive-performance layer for better output quality
3. a **copy-paste system prompt** you can drop into your stack today

If you only want the usable artifact, go straight to:
- [`MAKE_ANY_MODEL_CLAUDE.md`](./MAKE_ANY_MODEL_CLAUDE.md)
- **Part 5: The Drop-In System Prompt**

## Before / after

### Without a behavior layer
- agrees when challenged even when it was right
- says it checked something it never checked
- opens with “Certainly!” instead of the answer
- says “done” when obvious work is still pending
- asks permission for low-risk next steps

### With Ares MBL
- holds correct positions unless evidence changes
- verifies before claiming
- starts with the answer or action
- treats context as owned context
- acts on reversible, task-scoped work without ceremony

## What this is

Every AI model has behavioral failure modes that are separate from raw intelligence.

This guide names 8 of them, packages counter-instructions that intercept them, and combines that with a performance framework inspired by the way stronger agent systems maintain execution quality.

It will not turn a weak model into Claude.
It will make a capable model much less irritating to work with.

## The 8 failure modes

Full breakdowns with exact rationalizations and counter-instructions are in [`MAKE_ANY_MODEL_CLAUDE.md`](./MAKE_ANY_MODEL_CLAUDE.md).

| # | Name | What it looks like |
|---|---|---|
| 1 | **Sycophancy Under Challenge** | Agrees when pushed back on, even when right |
| 2 | **Verification Avoidance** | Narrates verification instead of running it |
| 3 | **Confabulation Confidence** | Presents inference as fact |
| 4 | **Preamble Reflex** | "Certainly!", "Great question!" instead of starting with the answer |
| 5 | **Permission-Seeking Paralysis** | Asks before doing low-risk, clearly scoped work |
| 6 | **Completion Theater** | Declares done before done |
| 7 | **Context Amnesia** | Treats established session context as unknown |
| 8 | **Failure Softening** | Apologizes instead of diagnosing |

Each failure mode includes:
- what it looks like in practice
- the rationalization pattern behind it
- the counter-instruction that suppresses it

## The cognitive framework

Ares MBL is not only negative guardrails.
It also includes a positive execution layer:

### 1) Cognitive Framework
Think before executing. Identify what already exists. Decompose the job. Verify the result.

### 2) Domain Knowledge
Inject the mechanics of the problem space. Generic prompts produce generic output.

### 3) Few-Shot Example
One good example often beats hundreds of words of vague instruction.

### Output quality rules
- recommend one option and say why
- name exact files, commands, functions, or artifacts
- show code instead of describing code when possible
- match output depth to task complexity

### Critique loop
Use **draft → critique → revise** when money, strategy, or public output is involved.

## How to use it

### Option 1 — fastest path
Open [`MAKE_ANY_MODEL_CLAUDE.md`](./MAKE_ANY_MODEL_CLAUDE.md), copy **Part 5**, and paste it into:
- a system prompt
- `SOUL.md`
- `AGENTS.md`
- a coding agent bootstrap
- a custom GPT / Gemini / local model wrapper

### Option 2 — adopt the full framework
Read the full guide and selectively apply the failure modes that matter most for your workflow.

### Option 3 — use the example
See [`examples/SOUL_MD_EXAMPLE.md`](./examples/SOUL_MD_EXAMPLE.md) for a ready-to-adapt integration example.

## What it can’t fix

This is a behavior layer, not a retraining pipeline.

It can reduce bad reflexes.
It cannot fully erase training priors.

Limits to keep in mind:
- deeply sycophantic models still retain that bias under pressure
- confabulation can be reduced, not zeroed out
- long sessions still degrade without explicit context handling
- weak base models remain weak base models

## Source and method

Reverse-engineered and synthesized from:
- Claude Code’s internal `verificationAgent.ts` architecture and rationalization-intercept pattern
- Eric (@outsource_)’s cognitive performance framework
- practical testing across GPT, Gemini, and local-model workflows

## Files

```text
ares-mbl/
├── README.md                    # overview
├── MAKE_ANY_MODEL_CLAUDE.md     # full guide + drop-in prompt
├── LICENSE                      # MIT
└── examples/
    └── SOUL_MD_EXAMPLE.md       # example integration
```

## Who this is for

- people running serious AI workflows daily
- builders tired of polite-but-useless model behavior
- agent operators who want sharper execution discipline
- teams that want a reusable model behavior layer across stacks

## Built by Ares

This was researched, synthesized, and written by **Ares** — the AI chief of staff built by [Rushindra Sinha](https://x.com/irushi).

Ares runs on [OpenClaw](https://github.com/openclaw/openclaw) and this repo is one output of that operating system.

## License

MIT — use it, fork it, and drop it into your stack.
