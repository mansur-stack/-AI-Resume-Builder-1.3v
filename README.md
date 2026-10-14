# AI Resume Builder

A modern, responsive resume builder written in plain **HTML, CSS and JavaScript**. No frameworks, no backend, no build step.
Fill in the form and watch your resume update live, pick a template, improve your text with the built-in AI demo and export a clean PDF.

## Features

- Live resume preview that updates as you type
- 4 templates (Modern, Professional, Minimal and the official Uzbek Ma'lumotnoma / obyektivka) plus font, size, spacing and 5 accent colors
- Sections: personal info, photo, summary, education, experience, skills, projects, languages
- "Improve with AI" for the summary and experience (demo logic, ready for a real API)
- AI Assistant chat panel with pre-written tips
- Resume Score (0-100) with a per-section breakdown
- Download PDF through the browser print dialog (print CSS exports only the resume)
- Save to `localStorage`, Clear All with confirmation, Load Demo Resume
- Dark mode, form validation, empty state, keyboard and screen-reader friendly

## Project structure

```text
AI-Resume-Builder/
├── index.html
├── style.css
├── script.js
└── README.md
```

## Run locally

1. Download or clone the repository.
2. Open `index.html` in any modern browser (or use the VS Code "Live Server" extension).

## Download as PDF

Click **Download PDF**, choose **Save as PDF** as the destination and turn off "Headers and footers".

## Connect a real AI API

All demo AI logic lives in `script.js`, in the section `AI demo`:

- `aiSummary()` returns the improved summary.
- `aiBullets(text)` returns the improved experience bullets.
- `improveWithAI(kind, btn, id)` calls them after a short delay. Replace them with an async `fetch` to your own server.
- `assistantReply(key)` powers the chat panel and can be replaced the same way.

Never put an API key in front-end code. Send requests to your own backend (for example a Node.js route) which calls the AI provider.

## License

MIT

## Ma’lumotnoma (official Uzbek CV) and PDF printing

The **Ma’lumotnoma** template is a plain black-on-white official document (Times New Roman, A4, 2 pages: details + work history, then the relatives table).
Choose it in *Templates*, fill in the "Ma’lumotnoma ma’lumotlari" and "Yaqin qarindoshlari" cards and press **Download PDF**.

In the print dialog:

1. Destination: **Save as PDF**
2. Paper size: **A4**, Scale: **100%**
3. Margins: any value. The page margins are built into the document (`@page { margin: 0 }` plus our own padding), which is also what stops **Chrome and Edge** from printing the date, page title, website URL and page numbers ("1/2").
4. **Firefox / Safari:** these browsers were not tested. If a date, URL or page number still appears, turn **off "Headers and footers"** in the print dialog. That checkbox is controlled by the browser, and CSS cannot override it in every browser.

The print CSS hides the whole website (navbar, form, buttons, labels, footer, assistant) and prints only the resume. Long work histories and many relatives continue on extra A4 pages with the same margins; the relatives table repeats its header row on every page.
