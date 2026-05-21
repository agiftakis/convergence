# convergence
 AI software-engineering substance is the orchestration system:
Convergence
> A Windows desktop app that orchestrates a structured multi-round debate between frontier AI models (Claude, GPT, Gemini, Grok) on a single task, then synthesizes a unified final answer.
Built by Andrew Giftakis · Software Engineering Project
---
What is Convergence?
When you ask one AI a question, you get one perspective. Convergence asks several AIs the same question, lets them debate each other across multiple rounds, and produces a single synthesized answer that incorporates the best of all of them.
It runs entirely on your Windows machine — no servers, no accounts, no subscriptions. You bring your own API keys (free options available), and Convergence does the rest.
Why it exists
A single LLM can be confidently wrong. It can miss edge cases, hallucinate facts, or fixate on one approach. By forcing multiple models from different companies to debate each other, weak answers get challenged and strong ones get reinforced. The final synthesized output is meaningfully better than any individual model's first attempt — especially for complex code, research questions, and design decisions.
---
Quick Start (5 Minutes)
Download the installer → Convergence_1.0.0_x64-setup.exe (13.6 MB)
Double-click the installer → click Next → Next → Finish
Launch Convergence from your Start menu
Click SETTINGS → paste in at least one API key (see Free API Keys below)
Click RUN → type a task → click "RUN ORCHESTRATION"
That's it. The app does the rest.
---
System Requirements
OS: Windows 10 or Windows 11 (64-bit)
Disk: ~50 MB
RAM: 4 GB minimum (8 GB recommended)
Internet: Required (the app calls AI provider APIs)
> **Note:** You do NOT need Python, Node.js, or any developer tools installed. The installer bundles everything.
---
Free API Keys (Recommended)
You can run Convergence at $0 cost using free-tier API providers. You only need one key to get started — but the magic of the app is using two or more so they can debate.
The Cheapest Path: OpenRouter + Gemini (both free)
These two providers alone let you run multi-model debates without spending a cent:
1. OpenRouter (Free Tier — Recommended Starting Point)
What you get: Access to many models through one API key, including free-tier models like Llama 3.3 70B
Cost: $0 for free-tier models (look for `:free` suffix in model names)
Get your key: https://openrouter.ai/keys
Steps:
Sign up with Google/GitHub (free, no credit card needed for free-tier models)
Go to https://openrouter.ai/keys
Click "Create Key"
Copy the key (starts with `sk-or-v1-...`)
Paste into Convergence Settings → OpenRouter field
In the "OpenRouter Model Slug" field, enter: `meta-llama/llama-3.3-70b-instruct:free`
2. Google Gemini (Free Tier)
What you get: Free access to Gemini models (rate-limited but generous)
Cost: $0 within free-tier limits
Get your key: https://aistudio.google.com/apikey
Steps:
Sign in with your Google account
Click "Create API Key"
Copy the key (starts with `AIza...`)
Paste into Convergence Settings → Google Gemini field
Paid Providers (Optional — Higher Quality Results)
If you want top-tier models (Claude Opus, GPT-4, Grok), you'll need accounts with these providers. Each charges per token used (usually pennies per debate):
Provider	Get Key Here	Key Prefix
Anthropic (Claude)	https://console.anthropic.com/settings/keys	`sk-ant-...`
OpenAI (GPT)	https://platform.openai.com/api-keys	`sk-...`
xAI (Grok)	https://console.x.ai/	`xai-...`
> **Tip:** Most students should start with **OpenRouter free tier + Gemini free tier**. You can always add paid providers later.
---
How to Use the App
The RUN Page
Type your task in the big text box. Examples that work well:
"Write Python code to convert .epub files to .pdf"
"Compare React vs Vue for a small team building a SaaS dashboard"
"Explain the tradeoffs between PostgreSQL and MongoDB for a social media app"
Click RUN ORCHESTRATION
Watch as each model responds, critiques the others, and refines its answer
When the models converge (agree on an answer), or hit the safety cap, you'll see a final synthesized answer
The SETTINGS Page
API Keys: Paste your keys here. They're stored locally on YOUR machine only — never sent anywhere except to the AI provider.
OpenRouter Model Slug: Which OpenRouter model to use (e.g., `meta-llama/llama-3.3-70b-instruct:free`)
Safety Cap: Max number of debate rounds before forcing convergence (default: 7)
Temperature: How creative the models should be (0.0 = strict, 1.0 = creative, default: 0.7)
The HISTORY Page
All your past debates, saved locally
Click any past session to see the full transcript
---
How It Works (Behind the Scenes)
```
Your Task
   ↓
Round 1 → Each model writes its first answer independently
   ↓
Round 2 → Each model sees the others' answers, critiques them, refines its own
   ↓
Round 3 → ... and so on, up to the Safety Cap
   ↓
Convergence Check → Do the models now agree on the core answer?
   ↓
Final Synthesis → A single unified answer combining the best ideas
```
The app uses a convergence engine that detects when models start agreeing and stops the debate early. If they never agree (rare), the safety cap kicks in after 7 rounds.
---
Where Your Data Lives
Everything is stored locally on your machine:
API keys & settings: `%APPDATA%\com.andy.convergence\`
Debate history: `%APPDATA%\com.andy.convergence\convergence.db`
To find this folder, press Win + R, paste `%APPDATA%\com.andy.convergence`, and press Enter.
Nothing is uploaded to any server other than the AI providers' APIs. Your prompts go directly from your machine to the providers you've added keys for.
---
Troubleshooting
"Convergence won't start" or "Crashes on launch"
Make sure you ran the installer (don't just unzip the .exe)
Check Windows Defender — it may have quarantined the app on first run. Restore it from the Defender history.
"I clicked Run Orchestration and nothing happened"
Open the SETTINGS page and confirm at least one API key is filled in
Make sure the key has no trailing spaces (a common copy-paste mistake)
"I get an API error"
The provider may have rejected your key — double-check it's still valid
For free-tier models, you may have hit a rate limit (wait a few minutes)
Make sure you used the right OpenRouter model slug (free-tier models need the `:free` suffix)
"Port 8732 already in use"
Another instance of Convergence is already running. Check Task Manager for `convergence-server.exe` and end it, then relaunch.
---
FAQ
Q: Do I need to pay for anything?
A: No. Using OpenRouter's free-tier models and Gemini's free tier, you can run Convergence completely free.
Q: Are my prompts or API keys sent to Andy or anyone else?
A: No. The app runs 100% locally. Your prompts go directly from your computer to whatever AI provider's API you've configured. Andy never sees them.
Q: Will this work on Mac or Linux?
A: Not currently. This is a Windows-only build. (The underlying code could be built for Mac/Linux, but no installer is provided yet.)
Q: Can I use this for class assignments?
A: Check your school's AI policy first. Convergence is a tool — your school's rules about AI assistance apply.
Q: I found a bug / I have a feature request.
A: Open an Issue on the GitHub repo: https://github.com/agiftakis/convergence/issues
---
Credits
Andy Giftakis — Project lead, full-stack development
Frontier AI Models — Claude (Anthropic), GPT (OpenAI), Gemini (Google), Grok (xAI), and Llama (Meta via OpenRouter)
Tauri v2 — Desktop application framework
FastAPI + Python — Backend orchestration engine
 Software Engineering marvels.
---
License
Released in  beta mode -Open source license.
