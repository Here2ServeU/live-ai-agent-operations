# AI Agent Operations · Free Live Sessions

Make AI agents reliable, secure and affordable in production. We teach operate.

**Free · Live · 30 minutes · Mondays and Thursdays, 7:30 PM Central** · with Emmanuel N. ([Transformed 2 Succeed](https://transformed2succeed.com))

### [Register free on Zoom](https://us06web.zoom.us/meeting/register/fT235rLjQaihJYrWj2_vjw)

Register once and you're in for every session. Zoom emails you the join link and reminders. Bring your questions: every session ends with live Q&A.

## Watch the recordings

Missed a session or want to watch it again? Recordings are added here after each live session.

| Date | Recording |
|---|---|
| _Coming after the first session_ | |

## Download the slides

**[08_AI_Agent_Operations_Free_Live_Session.pdf](slides/08_AI_Agent_Operations_Free_Live_Session.pdf)** (PDF)

## What you'll learn

1. **Your First Production Agent**: Build a working agent, then see the five things a happy-path demo never tests.
2. **The Agent Cost Problem**: Measure, forecast and bound what your agent really costs, before it reaches the CFO.
3. **Running AI Agents in Production**: The flagship: identity, budget caps, checkpointed runs and day-to-day operations.

## Three things to remember

- **Working is not production-ready**: Course 1: an agent is a loop. The model asks; your code acts. Score: 0 / 5.
- **Reasoning is unbounded: bound it**: Course 2: cost multiplies. Report cost per successful task.
- **Operate, don't just build**: Course 3: identity, budget caps, checkpoints, safe rollouts, baselines.

## Try it yourself

Get the hands-on labs here: [first-production-agent](https://github.com/Here2ServeU/first-production-agent) and [agent-cost-control](https://github.com/Here2ServeU/agent-cost-control)

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

## All free live sessions

A different course every session. The rotation repeats every 4 weeks, so if you miss one, it comes back around.

| Week | Day | Course |
|---|---|---|
| Week 1 | Monday | [Linux for AI-ML Systems](https://github.com/Here2ServeU/live-linux-for-ai-ml) |
| Week 1 | Thursday | [Python for AI-ML](https://github.com/Here2ServeU/live-python-for-ai-ml) |
| Week 2 | Monday | [Zero to AI-ML Systems Engineering](https://github.com/Here2ServeU/live-zero-to-ai-ml) |
| Week 2 | Thursday | [DevOps for AI-ML Systems](https://github.com/Here2ServeU/live-devops-for-ai-ml) |
| Week 3 | Monday | [SRE for AI-ML Systems](https://github.com/Here2ServeU/live-sre-for-ai-ml) |
| Week 3 | Thursday | [GPU Optimization for AI-ML Systems](https://github.com/Here2ServeU/live-gpu-optimization-for-ai-ml) |
| Week 4 | Monday | [FinOps for AI-ML Systems](https://github.com/Here2ServeU/live-finops-for-ai-ml) |
| Week 4 | Thursday | **AI Agent Operations** (you are here) |

## Want the full course?

The membership gives you **all 8 courses, every module and every lab, for $49/month**, plus a live session every month where we build something together.

**[Join at transformed2succeed.com](https://transformed2succeed.com)**
