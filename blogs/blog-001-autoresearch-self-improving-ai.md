# AutoResearch: A Simple Way to Build Self-Improving AI

*Inspired by Andrej Karpathy’s AutoResearch idea*

What if your code could improve itself without you manually tweaking prompts and logic all day?

That’s the core idea behind **AutoResearch**. It is not a heavy framework. It is a tight feedback loop with clear boundaries: the model tries, gets scored, updates itself, and tries again.

---

## The Core Idea (Plain English)

AutoResearch creates a repeatable cycle:

**Try → Measure → Improve → Repeat**

In each loop:
1. The AI attempts a task.
2. A fixed evaluator scores the result.
3. The AI updates only the allowed learning area.
4. The next attempt starts from that improved version.

This compounds quickly. The system gets better through iteration, not one-shot prompting.

---

## The 3-File Architecture

The strongest part of AutoResearch is its simplicity.

### 1) `program.md` — The Goal and Rules
This is human-authored and defines:
- the problem to solve
- constraints
- success criteria

Think of this as: **“What exactly should the AI achieve?”**

### 2) `train.py` — The Learning Surface
This is the only file the AI can change. It can contain:
- code
- prompts
- strategy logic

Every loop iteration modifies this file based on feedback.

### 3) `prepare.py` — The Evaluator
This runs the test and produces a score.

Critical rule: **AI cannot modify this file.**

Why that matters: if the evaluator changes, improvement metrics become meaningless.

---

## Why This Works So Well

Most teams optimize AI workflows manually:
- tune prompts
- tweak code
- rerun
- compare outcomes

AutoResearch automates that cycle safely by separating:
- **objective function** (`prepare.py`, fixed)
- **optimization surface** (`train.py`, mutable)

That separation prevents reward hacking and keeps progress measurable.

---

## A Simple Analogy

Think of exam preparation:
- **Question paper** = `program.md`
- **Student answers** = `train.py`
- **Teacher grading** = `prepare.py`

Now imagine the student gets immediate feedback and rewrites answers repeatedly. Performance naturally improves.

That is AutoResearch in action.

---

## Practical Use Cases

AutoResearch can be applied anywhere output quality is measurable:
- prompt optimization pipelines
- autonomous coding agents
- extraction and classification workflows
- ranking/relevance systems
- automated content pipelines

If you can define a stable evaluator, you can run this loop.

---

## Final Takeaway

AutoResearch is powerful because it is minimal:
- clear file roles
- controlled self-modification
- fixed, trustworthy evaluation
- continuous iterative improvement

No over-engineered stack required. Just a disciplined loop that keeps getting better.

If you build AI systems for automation, content, or developer tooling, this pattern is absolutely worth adopting.
