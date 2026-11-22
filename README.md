# Chunav Mitra — Election Education Assistant

An AI-powered web app to educate Indian citizens about the election process, built for PromptWars Virtual Challenge 2 (Google for Developers x Hack2Skill).
## Build note (election-edu-assistant)
Solo project, built for PromptWars Virtual Challenge 2 with AI-assisted development. I'm still learning Flask and working toward being able to explain every route myself.
## Live Demo 
COMING SOON...

## Build note
Solo project, built for PromptWars Virtual Challenge 2 with AI-assisted development. I'm still learning Flask and working toward being able to explain every route myself.

## Features
- Chat: Ask any question about Indian elections powered by Gemini AI
- Timeline: Visual history of Indian general elections
- Quiz: AI-generated MCQs to test your knowledge
- Glossary: Key election terms explained simply

## Tech Stack
- Python + Flask backend
- Google Gemini API (model set with the GEMINI_MODEL environment variable)
- Docker + Gunicorn (port 8080) + Google Cloud Run

## Prompt Strategy
Each feature uses intent-driven prompting. Chat keeps Gemini on-topic and neutral. Quiz returns structured MCQ JSON validated on the server. Glossary asks for short plain-text definitions.

## Run Locally
1. Clone the repo
2. Copy `.env.example` to `.env` and set `GEMINI_API_KEY` (never commit `.env`)
3. `pip install -r requirements.txt`
4. `python app.py` — open http://127.0.0.1:8080

## Deploy (Google Cloud Run)
Build and deploy with your GCP project (no secrets in the image). Example:

```powershell
gcloud config set project YOUR_PROJECT_ID
gcloud builds submit --tag REGION-docker.pkg.dev/PROJECT/REPO/IMAGE:latest
gcloud run deploy SERVICE_NAME --image REGION-docker.pkg.dev/PROJECT/REPO/IMAGE:latest --region REGION --platform managed --allow-unauthenticated --set-env-vars "GEMINI_API_KEY=YOUR_KEY"
```

Replace placeholders; keep the API key only in Cloud Run environment variables or Secret Manager.

## Known limitations
- Not an official source: verify with the Election Commission of India
- AI answers can be wrong; the quiz is validated for format, not for correctness
- Needs a Gemini API key; free-tier rate limits may apply
