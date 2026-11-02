# AI Agent Operations · Free Live Sessions

Make AI agents reliable, secure and affordable in production. We teach operate.

Free, live, 30-minute sessions with **Dr. Emmanuel Naweji** ([Transformed 2 Succeed](https://transformed2succeed.com)).
This course is presented on **Week 4, Thursday at 7:30 PM Central** of a 4-week rotation (8 courses, every Monday and Thursday).
This repo holds the slides, the recording of every live session, and the notes and links from each one.

## Session recordings

| Date | Recording | Notes |
|---|---|---|
| _First session coming soon_ | | |
<!-- sessions:end -->

## What the session covers

1. **Your First Production Agent**: Build a working agent, then see the five things a happy-path demo never tests.
2. **The Agent Cost Problem**: Measure, forecast and bound what your agent really costs, before it reaches the CFO.
3. **Running AI Agents in Production**: The flagship: identity, budget caps, checkpointed runs and day-to-day operations.

## Three things to remember

- **Working is not production-ready**: Course 1: an agent is a loop. The model asks; your code acts. Score: 0 / 5.
- **Reasoning is unbounded: bound it**: Course 2: cost multiplies. Report cost per successful task.
- **Operate, don't just build**: Course 3: identity, budget caps, checkpoints, safe rollouts, baselines.

## Try it yourself

Clone the course lab repo: [first-production-agent](https://github.com/Here2ServeU/first-production-agent) · [agent-cost-control](https://github.com/Here2ServeU/agent-cost-control)

**Module 1 · Your First Production Agent**: Run the ticket-triage agent for free

```bash
git clone https://github.com/Here2ServeU/first-production-agent
cd first-production-agent
cd modules/module-1/scripts
python3 run_agent.py --input samples/normal.json --sim
```
**Module 2 · The Agent Cost Problem**: Price one healthy run

```bash
git clone https://github.com/Here2ServeU/agent-cost-control
cd agent-cost-control/modules/module-1/scripts
python3 run_agent.py --input samples/normal.json --verbose
... | python3 price_run.py --input-rate 0.80 --output-rate 4.00
```

## Slides

[`slides/08_AI_Agent_Operations_Free_Live_Session.pptx`](slides/08_AI_Agent_Operations_Free_Live_Session.pptx): the presenter deck, with full speaker notes.

## Free live session schedule (Mondays and Thursdays, 7:30 PM Central)

| Week | Day | Course |
|---|---|---|
| Week 1 | Monday | [Linux for AI-ML Systems](https://github.com/Here2ServeU/live-linux-for-ai-ml) |
| Week 1 | Thursday | [Python for AI-ML](https://github.com/Here2ServeU/live-python-for-ai-ml) |
| Week 2 | Monday | [Zero to AI-ML Systems Engineering](https://github.com/Here2ServeU/live-zero-to-ai-ml) |
| Week 2 | Thursday | [DevOps for AI-ML Systems](https://github.com/Here2ServeU/live-devops-for-ai-ml) |
| Week 3 | Monday | [SRE for AI-ML Systems](https://github.com/Here2ServeU/live-sre-for-ai-ml) |
| Week 3 | Thursday | [GPU Optimization for AI-ML Systems](https://github.com/Here2ServeU/live-gpu-optimization-for-ai-ml) |
| Week 4 | Monday | [FinOps for AI-ML Systems](https://github.com/Here2ServeU/live-finops-for-ai-ml) |
| Week 4 | Thursday | **AI Agent Operations** (this repo) |

## Want all of it?

The membership gives you **all 8 courses, every module and every lab, for $49/month**, plus a live session every month where we build something together.
Join at **https://transformed2succeed.com**.

---

### For the presenter: logging a session

After each live session, run:

```bash
bash scripts/new-session.sh 2026-11-03 "https://link-to-the-recording"
git add -A && git commit -m "Session 2026-11-03" && git push
```

This creates `sessions/2026-11-03.md` from the template (fill in the Q&A and links) and adds a row to the recordings table above.
