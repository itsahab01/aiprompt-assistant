# AI Prompt Assistant — Project Write-Up

**Track C — Prompt-Engineering Tool** · Generative AI Summer Bootcamp · Najran University

---

**Live Demo:** [huggingface.co/spaces/itsahab01/AI-Prompt-Assistant](https://huggingface.co/spaces/itsahab01/AI-Prompt-Assistant)

## Problem

Most people who use LLMs write prompts that are vague or incomplete — missing a defined role, context, or output format. This leads to inconsistent, generic, or off-target responses, and most users have no easy way to know *why* their prompt underperformed or how to fix it.

## Solution

**AI Prompt Assistant** evaluates any prompt against the **Five Essential Prompt Components** (Instructions, Role, Context, Input Data, Output Format) and 10 quality criteria (clarity, specificity, context quality, constraints, practicality, etc.). It returns a structured report that combines a component-by-component review, weaknesses, strengths, an overall quality score, actionable improvement suggestions, and a ready-to-use **optimized rewrite** — while preserving the user's original intent.

## Models Used

- **Qwen2.5-1.5B-Instruct**
- **Gradio** — interactive web interface
- **Hugging Face Spaces** — public deployment; prototyped on Google Colab (T4 GPU)

## Design Decisions

- **Evaluation-first output order:** the model is required to review the Five Components *before* writing Weaknesses, Strengths, and the Overall Score, so each later section is grounded in the component analysis instead of being generated independently.
- **Consistency rule:** the system prompt explicitly requires that any component marked Weak or Missing must also appear in Weaknesses, and forbids contradictory statements like "no weaknesses" when a component is missing.
- **Scoring guide (anchored scale):** the score is tied to the number of components present (e.g., all 5 present → 8–10, 0 present → 0–1) and must always be reported in an explicit `X/10` format, reducing arbitrary or inconsistent scoring.
- **Fixed generation settings:** temperature, max output length, and repetition penalty are fixed rather than user-adjustable, keeping evaluations consistent and reproducible across users.
- **Code-level consistency check:** after generation, the app scans the model's own output and flags (without altering) any case where a component marked Weak/Missing wasn't reflected in Weaknesses — an extra safety net beyond prompt instructions alone.
- **Input validation:** empty or very short inputs are caught before calling the model, avoiding wasted generations and giving immediate, clear feedback.

## What Works

- Provides a clear written evaluation combining a component-by-component review, weaknesses, and strengths.
- Provides practical, actionable improvement suggestions.
- Generates an optimized version of the prompt while preserving the original intent.
- Reports an overall score in a consistent `X/10` format.
- Successfully deployed on Hugging Face Spaces.

## Limitations

- Supports English only.
- As a 1.5B-parameter model, occasional inconsistencies between sections can still occur despite the consistency rule and code-level check.
- Response time depends on server availability.
- Prompt history is not currently saved.
- Additional evaluation features may be added in future versions.
