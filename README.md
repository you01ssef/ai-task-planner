# AI Task Planner

A beginner Python web app built with Streamlit. Enter a goal, get a checklist, check off completed tasks, and ask the AI to revise the remaining work. No login or database.

## Run the app

Install Python 3.10 or newer. Open a terminal in this project folder, then run:

```sh
python -m venv .venv
```

Activate the environment:

- macOS/Linux: `source .venv/bin/activate`
- Windows PowerShell: `.venv\Scripts\Activate.ps1`

Then run:

```sh
python -m pip install -r requirements.txt
python -m streamlit run app.py
```

Open the local URL printed in your terminal (usually http://localhost:8501).

## Try it

1. Leave **Demo mode** on to test without a key. This produces a generic template; it is not AI.
2. Enter “Prepare for my math exam in 3 days” and click **Create Plan**.
3. Check off one task.
4. Click **Plan my remaining tasks**. Demo mode retains the remaining tasks; AI mode revises them.
5. Check all tasks to see the completion message.

## Turn on real AI

Turn off **Demo mode** in the sidebar and enter your own OpenAI API key in the password field. You can alternatively set the `OPENAI_API_KEY` environment variable before starting the app. Do not put your key in the code or submit it with your project.

The app calls the OpenAI API, which may require API credits. It uses `gpt-4o-mini` by default; you can set `OPENAI_MODEL` to another model available to your API account that supports Responses and structured outputs. Goals and progress are sent to OpenAI on planning requests. No key is saved to a project file.

## How it works

- **Framework:** Streamlit creates the web page using Python.
- **AI:** The OpenAI model chooses actionable steps based on the goal.
- **State:** Streamlit session state keeps the plan and completed tasks during the session.
- **Feedback loop:** The user marks progress, and the planner uses that feedback to revise unfinished work.

This is a minimal, human-guided planning agent. It does not execute the tasks or autonomously call external tools. If your instructor specifically requires tool-calling agents, confirm that requirement before submitting.

All application code is in `app.py`. The `Plan` class defines the AI response shape, `make_plan` generates tasks, `update_plan` saves successful results, and the rest displays the page.

## One-minute presentation script

“My project is an AI Task Planner built with Python and the Streamlit framework. It helps someone turn a large goal into smaller steps. First, I enter a goal and click Create Plan. The AI generates a checklist. Then I mark a task as completed. When I click Plan my remaining tasks, the agent uses my progress to update the plan. This shows a simple loop: goal, plan, feedback, and revised plan. I kept the project small by using one page and storing progress only during the session.”

For your live presentation, use AI mode to demonstrate actual model-generated plans. If you show demo mode, explain that it is a template preview.

## References

- OpenAI structured outputs: https://developers.openai.com/api/docs/guides/structured-outputs
- Streamlit session state: https://docs.streamlit.io/develop/api-reference/caching-and-state/st.session_state

## Deploy from GitHub

1. Create a GitHub repository named `ai-task-planner` and put `app.py`, `requirements.txt`, `README.md`, and `.gitignore` at its root. Upload the extracted files, not the ZIP itself.
2. Sign in at https://share.streamlit.io/ and connect your GitHub account.
3. Click **Create app**, select the repository, choose branch `main`, and set the main file path to `app.py`.
4. Choose Python 3.11 in Advanced settings, then deploy.
5. Open the generated `streamlit.app` link. Demo mode works without a key. To use AI, turn off Demo mode and enter your replacement key in the sidebar for that session.

This setup keeps the API key out of GitHub. Anyone visiting the app supplies their own key for AI mode. GitHub stores the source code; Streamlit Community Cloud runs the Python app.

Deployment reference: https://docs.streamlit.io/deploy/streamlit-community-cloud/deploy-your-app/deploy
