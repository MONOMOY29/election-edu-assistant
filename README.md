# Chunav Mitra — Election Education Assistant

An AI-powered web app that explains the Indian election process to citizens. Ask questions in the chat, explore a timeline, take quizzes and look up key terms. Built for PromptWars Virtual Challenge 2 (Google for Developers x Hack2Skill).

**Live demo:** [https://election-edu-assistant.onrender.com](https://election-edu-assistant.onrender.com) (free hosting: the first load can take up to ~50 seconds)

## Build note
Solo project, built with AI-assisted development. I'm still learning Flask and working toward being able to explain every route myself.

## Features
- Chat: ask any question about Indian elections, powered by Gemini AI
- Timeline: visual history of Indian general elections
- Quiz: AI-generated multiple-choice questions to test your knowledge
- Glossary: key election terms explained simply

## Tech Stack
- Python + Flask backend (served with Gunicorn)
- Google Gemini API (model set with `GEMINI_MODEL`; by default it tries `gemini-3.8-flash` first, then older models)
- Hosted on Render (free tier)

## Prompt Strategy
Each feature uses intent-driven prompting. Chat keeps Gemini on-topic and neutral. Quiz returns structured MCQ JSON validated on the server. Glossary asks for short plain-text definitions.

## Run Locally
1. Clone the repo
2. Copy `.env.example` to `.env` and set `GEMINI_API_KEY` (never commit `.env`)
3. `pip install -r requirements.txt`
4. `python app.py`, then open http://127.0.0.1:8080

## Deploy (Render, free tier)
1. Create a new Web Service on Render and connect this repo
2. Build command: `pip install -r requirements.txt`
3. Start command: `gunicorn app:app`
4. Add environment variables: `GEMINI_API_KEY` (your key) and `PYTHON_VERSION` (for example `3.13.5`)

## Known limitations
- Not an official source: verify with the Election Commission of India
- AI answers can be wrong; the quiz is validated for format, not for correctness
- Needs a Gemini API key; free-tier rate limits may apply
- Free hosting sleeps when idle, so the first request can be slow
