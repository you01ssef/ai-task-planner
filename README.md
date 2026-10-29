# AI Task Planner

A simple Python **Flask** web app for creating a checklist from a goal and revising it after the user marks progress. This version runs on **Vercel**.

## Run locally

Use Python 3.12 or newer, then:

```sh
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python app.py
```

On Windows activate with `.venv\Scripts\Activate.ps1`. Open http://127.0.0.1:5000.

## Deploy

Import this GitHub repository at https://vercel.com/new. Vercel detects Flask through `app.py` and installs `requirements.txt`. Deploy with the default root directory. No API key is committed or required for demo mode.

## Use real AI

Open Settings, turn off Demo mode, and enter your own OpenAI API key. Requests go through the Flask server to OpenAI. The key stays in page memory and is not written to project files or browser storage. Do not share a key in chat or commit it to GitHub. API use may require credits.

Demo mode is a fixed template and does not call an AI. In AI mode, the model creates steps for the goal and revises unfinished work using completed tasks as feedback. This is a minimal human-guided planning agent, not an autonomous task executor.

## Files

- `app.py`: Flask routes, input validation, and OpenAI structured output request.
- `index.html`: page, styling, checkboxes, progress, and browser state.
- `requirements.txt`: Python dependencies.
- `vercel.json`: function timeout configuration.

## Presentation

“I built an AI Task Planner using Python and Flask. I enter a goal and the AI creates a checklist. After I mark tasks complete, it uses that progress to revise the remaining work. The app demonstrates a goal, plan, feedback, and revised-plan loop. Vercel hosts the web app and GitHub stores the source code.”

Progress resets on refresh. Real AI needs an API key; demo mode works without one.

References: https://vercel.com/docs/frameworks/backend/flask and https://developers.openai.com/api/docs/guides/structured-outputs
