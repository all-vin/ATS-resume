# ATS-resume
# 🎯 ATS Resume Consultant

An AI-powered resume analyzer that compares your CV against any job description, gives you an ATS compatibility score, and provides actionable improvement advice — all in a clean, professional interface.

---

## ✨ Features

- **ATS Match Score** — Visual gauge (0–100%) showing how well your CV matches the job description
- **Verdict & Summary** — Instant read on your candidacy: Excellent / Good / Partial / Poor Match
- **Strengths / Gaps / Risks** — A structured breakdown of what's working, what's missing, and what could hurt your chances
- **Missing Keywords** — Ranked by importance (High / Medium / Low) with context from the JD so you know exactly where to add them
- **Section-by-section Feedback** — Rating and specific suggestions per CV section (Summary, Experience, Skills, Education, etc.)
- **Rewrite Suggestions** — Side-by-side before/after examples with ATS reasoning

---

## 🖥️ How to Use

1. **Add your Resume / CV** — paste plain text or upload a PDF
2. **Add the Job Description** — paste plain text or upload a PDF
3. **Click "Analyze & Generate ATS Report"**
4. Navigate the results across five tabs:
   - 📊 Overview
   - ⚡ Strengths / Gaps / Risks
   - 🔑 Missing Keywords
   - 📋 Section Feedback
   - ✍️ Rewrite Suggestions

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Framework | React (via Claude Artifact) |
| AI Engine | Claude Sonnet (`claude-sonnet-4-20250514`) |
| API | Anthropic Messages API (`/v1/messages`) |
| Styling | Inline CSS / custom design system |
| File Parsing | Browser FileReader API (PDF as base64) |

---

## 🎨 Design System

| Token | Color | Hex |
|---|---|---|
| Primary | Verde Esmeralda | `#1B6B4A` |
| Neutral | Cinza Grafite | `#2D2D2D` |
| Danger / Alert | Vermelho Argila | `#B5533C` |
| Background | Off-white | `#F5F3EE` |

---

## 🤖 AI Prompt Design

The app sends both documents (resume + JD) to Claude via the Anthropic API and instructs it to return a structured JSON object containing:

```json
{
  "matchScore": 0-100,
  "verdict": "Excellent Match | Good Match | Partial Match | Poor Match",
  "verdictReason": "...",
  "strengths": ["..."],
  "gaps": ["..."],
  "risks": ["..."],
  "missingKeywords": [
    { "keyword": "...", "importance": "High | Medium | Low", "context": "..." }
  ],
  "sectionFeedback": [
    { "section": "...", "rating": "Strong | Good | Needs Work | Missing", "feedback": "...", "suggestion": "..." }
  ],
  "rewriteSuggestions": [
    { "section": "...", "issue": "...", "original": "...", "improved": "...", "reason": "..." }
  ]
}
```

PDF files are converted to base64 and sent as `document` content blocks, allowing Claude to read them natively.

---

## ⚠️ Limitations

- PDF parsing quality depends on the document's text layer (scanned/image PDFs may not parse correctly)
- Results are AI-generated and should be used as guidance, not as a definitive hiring guarantee
- No data is stored — all analysis happens in-session only
- Requires a valid Anthropic API key configured in the environment

---

## 🚀 Possible Improvements

- [ ] Export full report as PDF
- [ ] Copy improved text to clipboard per section
- [ ] Support for multiple job descriptions (batch compare)
- [ ] Language detection & multilingual support
- [ ] Interview question predictions based on JD
- [ ] Cover letter generator using resume + JD as context

---

## 📄 License

MIT — free to use, modify, and distribute.
