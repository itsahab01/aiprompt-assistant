#  AI Prompt Assistant

**Track C — Prompt-Engineering Tool** · Generative AI Summer Bootcamp · Najran University

An AI-powered tool that evaluates prompts, scores their quality, and rewrites them into optimized versions — built with a local open-weight LLM (no API keys needed).

🔗 **Live Demo:** [huggingface.co/spaces/itsahab01/AI-Prompt-Assistant](https://huggingface.co/spaces/itsahab01/AI-Prompt-Assistant)

---

## 🖼️ Preview


---

## 🎯 Problem

Most people who use LLMs write prompts that are vague or incomplete — missing a defined role, context, or output format. This leads to inconsistent, generic, or off-target responses, and most users have no easy way to know *why* their prompt underperformed or how to fix it.

## 💡 Solution

**AI Prompt Assistant** evaluates any prompt against the **Five Essential Prompt Components** (Instructions, Role, Context, Input Data, Output Format) and 10 quality criteria (clarity, specificity, context quality, constraints, practicality, etc.). It returns a structured Markdown report containing an overall quality score (1–10), strengths, weaknesses, a component-by-component review, actionable improvement suggestions, and a ready-to-use **optimized rewrite** — all while preserving the user's original intent.

## ✨ Features

- **Five-Component Evaluation** — checks every prompt against Instructions, Role, Context, Input Data, and Output Format.
- **10-Criteria Quality Scoring** — clarity, specificity, completeness, context quality, role definition, input quality, output definition, constraints, practicality, and expected accuracy, summarized into a single 1–10 score.
- **Structured Markdown Report** — Overall Score → Strengths → Weaknesses → Five Components Review → Improvement Suggestions → Optimized Prompt → Clarifying Questions (when needed).
- **Consistent, Fixed Generation Settings** — temperature and max output length are fixed by design for stable, reproducible evaluations (not exposed as adjustable sliders).
- **Input Validation** — gracefully handles empty or too-short prompts instead of calling the model unnecessarily.
- **Ready-Made Examples** — one-click sample prompts to try the tool instantly.
- **Clean, Dark-Themed UI** — custom Gradio interface with a blue accent theme.

## 🛠️ Tech Stack

- **Qwen2.5-1.5B-Instruct** (Alibaba, open-weight, ungated) — the core LLM performing evaluation and rewriting, loaded via Hugging Face Transformers
- **PyTorch** — model inference
- **Gradio** — interactive web interface
- **Hugging Face Spaces** — public deployment; prototyped on Google Colab (T4 GPU)

## ⚙️ How It Works

1. The user pastes a prompt into the input box.
2. The app wraps it inside a system prompt that encodes prompt-engineering best practices and an evaluation framework.
3. **Qwen2.5-1.5B-Instruct** generates a structured Markdown evaluation using fixed, tuned generation settings.
4. The result — score, strengths, weaknesses, suggestions, and an optimized rewrite — is displayed instantly in the interface.


## ✅ What Works

- Provides a clear written evaluation combining strengths and weaknesses.
- Provides practical, actionable improvement suggestions.
- Generates an optimized version of the prompt while preserving intent.
- Successfully deployed on Hugging Face Spaces.

## ⚠️ Limitations

- Supports English only.
- Prompt history is not currently saved between sessions.
- Additional evaluation features may be added in future versions.

## 👤 Author
Sahab AL Mutlaq
