# Model Behavior Layer

> Make any AI model behave more like Claude. Drop it in any system prompt.

Most models aren't frustrating because they're dumb — they're frustrating because they agree when pushed, declare done when they're not, and warm up instead of answering. This fixes that.

## What This Is

Every AI model has behavioral failure modes that aren't about capability — they're about trained reflexes that survive even when the model clearly knows better. This guide names 8 of them, reverse-engineered from Claude Code's internal `verificationAgent.ts` architecture — the layer that intercepts rationalizations before they fire. It combines that with a cognitive performance framework for consistent output quality, and a single copy-paste block you can drop into any system prompt today.

It works on GPT-5.4, Gemini, Ollama, Codex, or anything that takes a system prompt. It won't make a base model into Claude. It will make any capable model stop doing the things that make it frustrating.

## The 8 Failure Modes

Full breakdowns with exact rationalizations and counter-instructions are in `MAKE_ANY_MODEL_CLAUDE.md`.

| # | Name | What it looks like |
|---|---|---|
| 1 | **Sycophancy Under Challenge** | Agrees when pushed back on, even when right |
| 2 | **Verification Avoidance** | Narrates verification instead of running it |
| 3 | **Confabulation Confidence** | Presents inference as fact |
| 4 | **Preamble Reflex** | "Certainly!", "Great question!" — can't start with the answer |
| 5 | **Permission-Seeking Paralysis** | Asks before doing low-risk, clearly-scoped things |
| 6 | **Completion Theater** | Declares done before done |
| 7 | **Context Amnesia** | Treats established session context as unknown |
| 8 | **Failure Softening** | Apologizes instead of diagnosing |

Each failure mode includes: what it looks like in practice, the exact rationalizations the model reaches for, and a counter-instruction that intercepts the rationalization before it fires.

## The Cognitive Framework

From Eric (@outsource_)'s 3-layer performance stack — the positive side of this guide (what the model *should* do, not just what it shouldn't):

**3-Layer Performance Stack:**
- **Layer 1 — Cognitive Framework:** Think before executing. Identify what exists. Decompose. Verify.
- **Layer 2 — Domain Knowledge:** Inject the specific mechanics of the problem space. Generic prompts produce generic output.
- **Layer 3 — Few-Shot Example:** One good example outperforms 500 words of instruction. Show the model what 10/10 looks like.

**Output Quality Rules:** Be opinionated (one recommendation + why). Be specific (files, commands, not hand-waving). Show code, not descriptions of code. Match depth to complexity.

**Critique Loop:** Draft → score → revise. Use when money is involved, output is public, or quality matters more than speed. Skip for routine tasks.

## The Drop-In System Prompt

The full copy-paste block is at the bottom of `MAKE_ANY_MODEL_CLAUDE.md` — Part 5. Under 700 tokens. Works standalone in any system prompt on any model. Ordered by impact.

## How to Use

### Option 1: Drop-in system prompt (fastest)
Copy the block from `MAKE_ANY_MODEL_CLAUDE.md` → Part 5 → paste into your system prompt, SOUL.md, or AGENTS.md file. Done.

See `examples/SOUL_MD_EXAMPLE.md` for a ready-to-use example.

### Option 2: Full guide
Read the full `MAKE_ANY_MODEL_CLAUDE.md` and apply the failure mode framework section by section. Each mode has exact rationalization patterns — you'll recognize them immediately.

### Option 3: Model-specific
Jump to Part 4 for severity tables by model: GPT-4, GPT-5.4, and Gemini each have specific failure mode rankings and weight guidance.

## What It Can't Fix

The assistant reflex isn't fully suppressible via prompting — Claude's behavioral characteristics come from training objectives, not just system prompts. You can reduce deference and sycophancy with explicit instruction; you can't eliminate the underlying frame. Confabulation frequency is baseline-determined — instructions reduce it, they don't zero it out. For long sessions (30+ turns), context handling degrades regardless of instruction; restate critical context explicitly rather than relying on retrieval.

## Source

Reverse-engineered from:
- Claude Code's internal `verificationAgent.ts` — failure mode naming + rationalization intercept pattern
- Eric (@outsource_) cognitive performance framework — 3-layer stack + output quality rules
- Practical inference from real-world model behavior across GPT, Gemini, and Ollama deployments

## Files

```
model-behavior-layer/
├── README.md                    — this file
├── MAKE_ANY_MODEL_CLAUDE.md     — full guide (5 parts)
├── LICENSE                      — MIT
└── examples/
    └── SOUL_MD_EXAMPLE.md       — ready-to-use system prompt example
```

## License

MIT — use it, fork it, drop it into your stack.
