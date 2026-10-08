# ai-resume-assistant# 📄 ATS Resume Checker

Upload a resume (PDF, DOCX or TXT) and get an **ATS score out of 100**, a score breakdown, missing keywords, prioritized improvement tips, and example bullet rewrites. Optionally paste a job description for better keyword matching.

Built with [Streamlit](https://streamlit.io) and Google's Gemini Flash model.

## Features
- PDF / DOCX / TXT resume upload
- Overall ATS score plus Keywords, Formatting, Sections, Impact and Readability sub-scores
- Strengths, weaknesses, missing keywords and missing sections
- Prioritized improvement suggestions and before/after bullet rewrites
- Optional job description matching
- Downloadable JSON report

## Run locally
```bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

Get a free API key at https://aistudio.google.com/app/apikey, then either:

- set an environment variable: `export GEMINI_API_KEY="your-key"` (Windows PowerShell: `$env:GEMINI_API_KEY="your-key"`), or
- create `.streamlit/secrets.toml` (do **not** commit it):
  ```toml
  GEMINI_API_KEY = "your-key"
  ```
- or just paste the key into the app's sidebar.

```bash
streamlit run app.py
```

## Configuration
| Setting | Purpose |
|---|---|
| `GEMINI_API_KEY` | Your Gemini API key (secret or env var) |
| `GEMINI_MODEL` | Optional. Force a specific model, e.g. `gemini-2.5-flash`. If unset, the app tries a list of Flash models in order. |

## Deploy on Streamlit Community Cloud
1. Push this repo to GitHub (public, or private with access granted).
2. Go to https://share.streamlit.io and sign in with GitHub.
3. Click **Create app** → choose your repo, branch `main`, main file `app.py`.
4. Open **Advanced settings → Secrets** and add: `GEMINI_API_KEY = "your-key"`
5. Click **Deploy**.

## Notes
- Scanned/image-only PDFs can't be read (ATS systems can't read them either) - use a text-based PDF or DOCX.
- The score is an AI-based estimate, not the result of any real employer's ATS.
- Resume text is sent to the Gemini API. Don't upload anything you aren't comfortable sharing.
