# Set up your lab: AI Agent Operations

When you finish this page you will have the Agent Cost Control course agent on your computer, running a healthy task and pricing it. Everything runs offline and for free. It takes about 10 to 15 minutes.

This live session previews three courses of the track: **(1) Your First Production Agent**, **(2) The Agent Cost Problem** and **(3) Running AI Agents in Production**. Only part 2 has a public lab you can clone today. See Step 2.

## What you need

- Any computer: Windows 10/11, Mac or Linux. A browser alone is enough if you use Codespaces.
- About 100 MB of free disk space.
- A free GitHub account (only for Option A, Codespaces).
- Python 3.10 or newer, and git. A terminal (the one inside VS Code is fine).
- No GPU.
- **No API key and no paid account.** The model is simulated, so every lab script runs offline, costs nothing and prints the same numbers every time. If a slide shows `export ANTHROPIC_API_KEY=...`, skip that step.
- Module 1 needs no packages. Later modules add one package (`prometheus-client`) with pip. Docker is only needed for the later course modules (5, 6 and the capstone), not for this session.

## Step 1 · Pick where to run it

### Option A: GitHub Codespaces (easiest, in your browser)

1. Sign in to GitHub and open https://github.com/Here2ServeU/agent-cost-control
2. Click **Code > Codespaces > Create codespace on main**.
3. Wait for the terminal to open. Python and git are already installed, and the repo is already cloned. Skip to Step 3.

### Option B: Windows (PowerShell)

1. Open PowerShell. `winget` comes with Windows 11 and recent versions of Windows 10.
   ```powershell
   winget install Python.Python.3.12
   winget install Git.Git
   winget install Microsoft.VisualStudioCode
   ```
2. Close PowerShell and open it again, then check:
   ```powershell
   py --version; git --version
   ```
3. On Windows the Python command is `py`. Wherever this page says `python3`, type `py`.

You can also use WSL Ubuntu (see the official guide below) and follow the Linux commands.

### Option C: Mac

1. Install Homebrew first (see brew.sh), then:
   ```bash
   brew install python git
   brew install --cask visual-studio-code
   python3 --version && git --version
   ```

**Linux (Ubuntu/Debian):** `sudo apt install -y python3 python3-venv python3-pip git`

## Step 2 · Get the lab files

**Part 2 · The Agent Cost Problem (public, clone it now):**

```bash
git clone https://github.com/Here2ServeU/agent-cost-control
cd agent-cost-control
```

**Part 1 · Your First Production Agent:** the lab files for this course are not public. They are shared during the live session and with members. You do not need them to follow along today. The course uses the same "simulated model, no API key" approach, so the agent-cost-control repo above is the best way to get hands-on right now.

**Part 3 · Running AI Agents in Production:** this part is a preview of the course ideas (per-agent identity, budget caps, checkpointed runs). There is no lab download for it yet.

## Step 3 · Install and check

Module 1 uses only the Python standard library, so there is nothing to install yet. Step into the Module 1 scripts folder and look around:

```bash
cd modules/module-1/scripts
ls
```

You should see `run_agent.py`, `price_run.py`, `sim_model.py` and a `samples/` folder holding `normal.json` and `malformed.json`. (On Windows, use `dir` instead of `ls`.)

For later modules, create a virtual environment once at the top of the repo:

```bash
cd ~/agent-cost-control      # or wherever you cloned it
python3 -m venv .venv
source .venv/bin/activate    # Windows: .venv\Scripts\Activate.ps1
pip install prometheus-client
```

You should see your prompt start with `(.venv)`. Activate it again every time you open a new terminal.

## Step 4 · Quick test for each part

**Part 1 · Your First Production Agent** (lab files shared in the live session)

You will watch this one live: a support-ticket agent that runs with `--sim` (simulated model, free, no key). The healthy ticket calls `lookup_customer`, then `search_kb`, then `route_ticket`, and finishes in 3 steps. To see the same agent loop yourself today, run the Part 2 test below.

**Part 2 · The Agent Cost Problem** (run from `modules/module-1/scripts`)

```bash
python3 run_agent.py --input samples/normal.json --verbose
python3 run_agent.py --input samples/normal.json --verbose | grep -c 'usage'
python3 run_agent.py --input samples/normal.json --verbose | python3 price_run.py
```

On Windows, count the calls with this command instead:

```powershell
(py run_agent.py --input samples/normal.json --verbose | Select-String 'usage').Count
```

You should see six steps, each with a line like `usage: {"input_tokens": 1430, "output_tokens": 430}`. The count prints `6`. The price check shows `6 calls · 15,137 input = $0.0454 · 2,119 output = $0.0318 · run $0.0772` (simulated lab rates, nothing is charged).

Then run the task that never finishes, always with the time limit:

```bash
python3 run_agent.py --input samples/malformed.json --verbose --max-seconds 120
```

You should see the steps keep scrolling and input tokens keep climbing until it is `stopped by --max-seconds`. Never remove the limit.

**Part 3 · Running AI Agents in Production** (preview, no lab yet)

For a hands-on taste of a budget cap, use the same repo's Module 3, with your `.venv` active:

```bash
cd ../../module-3/scripts
pip install -r requirements.txt
RUN_BUDGET_USD=0.02 python3 run_agent.py --input samples/normal.json
```

Two cents is set too low on purpose, so you should see a normal task stopped by the per-run cap. (In PowerShell, set the value first with `$env:RUN_BUDGET_USD="0.02"`, then run `py run_agent.py --input samples/normal.json`.)

## If something goes wrong

- **`python3: command not found` on Windows.** Use `py` instead of `python3`.
- **PowerShell says "running scripts is disabled" when you activate `.venv`.** Run this once, then try again: `Set-ExecutionPolicy -Scope CurrentUser RemoteSigned`
- **`can't open file 'run_agent.py'`.** You are in the wrong folder. Run `cd modules/module-1/scripts` from the top of the repo.
- **`ModuleNotFoundError: No module named 'prometheus_client'`.** Activate `.venv` and run `pip install -r requirements.txt` in that module's `scripts` folder.
- **`timeout: command not found` on a Mac.** Use `--max-seconds 120` instead. It works on every system.
- **Stuck for 15 minutes?** Switch to Option A, Codespaces. It works in any browser with nothing to install.

## Official guides

- Course repo (Part 2): https://github.com/Here2ServeU/agent-cost-control
- Install Git, Python and VS Code on a Mac (video): https://www.youtube.com/watch?v=8ZIiXg4XOY0
- Install Git, Python and VS Code on Windows (video): https://www.youtube.com/watch?v=f091sbQSv7I
- Python downloads: https://www.python.org/downloads/
- Git downloads: https://git-scm.com/downloads
- VS Code intro videos: https://code.visualstudio.com/docs/getstarted/introvideos
- GitHub Codespaces: https://docs.github.com/codespaces
- Install WSL on Windows: https://learn.microsoft.com/windows/wsl/install
