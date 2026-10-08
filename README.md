# AI Interview Board — Project Starter

A local, multi-agent-style interview practice app. Upload a CV, complete a realistic eight-question interview, and receive a strict review with evidence-based strengths and areas to improve.

## What it does

- **Reem — CV reader:** extracts the candidate's name, specialty, experience, skills, education, and projects from the CV.
- **Noura — specialty interviewer:** asks four role-specific questions in English, tailored to the CV where possible.
- **Mazen — HR interviewer:** asks four behavioral and motivation questions in Arabic.
- **Lina — evaluator:** scores the written answers against clear evidence signals.
- **Rashid — summary writer:** reports supported strengths, weaknesses, and feedback for each answer.

> This project uses local rules and text signals. The agents are simulated roles; they do not call an LLM or an external AI service.

## Run locally

### Requirements

- Node.js LTS
- Internet access to load the PDF and Word text-extraction libraries from their CDN

### VS Code (recommended)

1. Download and extract this project folder.
2. Open the `interview-board` folder in VS Code. It should contain `server.js` and the `.vscode` folder.
3. Press `Ctrl+Shift+P`, choose **Tasks: Run Task**, then select **تشغيل المقابلة محليًا**.
4. Open the local URL printed in the terminal. It is usually `http://127.0.0.1:4174/`.
5. Keep the terminal open while using the app. Press `Ctrl+C` in that terminal to stop the server.

### Terminal

From the project folder, run:

```bash
node server.js
```

The server prints the URL it selected. If port `4174` is already in use, it automatically tries the next port.

## CV formats

Supported formats: text-based PDF, DOCX, TXT, and Markdown. Scanned image PDFs are not supported because OCR is not included. PDF and Word text is extracted in the browser, then sent to the local server on `127.0.0.1` for analysis.

## Local API

- `GET /api/health` — check that the service is running.
- `POST /api/cv/analyze` — analyze extracted CV text and return a candidate profile.
- `POST /api/interviews` — create an interview session and return the first question.
- `POST /api/interviews/:id/answers` — record and evaluate an answer, then return the next question or final report.

Interview sessions are held temporarily in server memory. They are removed after the report is returned, and restarting the server clears any active sessions. No database or API key is required.

## Project structure

```text
interview-board/
├── index.html                 # User interface and browser-side CV text extraction
├── server.js                  # Local HTTP server and API routes
├── backend/
│   └── agents.js              # CV analysis, question generation, evaluation, and report
├── .vscode/
│   └── tasks.json             # VS Code run task
├── مقابلة.code-workspace      # VS Code workspace
├── .gitignore
└── README.md
```

## Publish your submission

1. Create a GitHub repository or fork the project repository.
2. Open the project folder in VS Code and use **Source Control** to review the files.
3. Commit and push your project files:

   ```bash
   git add README.md index.html server.js backend/agents.js .vscode
   git commit -m "Build local multi-agent interview app"
   git push
   ```

4. Add your name and tag the academy at the bottom of this README, then commit and push the change:

   ```text
   Submitted by: Your Name — academy: @SDAIAAcademy
   ```

## Notes

- Specialty questions are in English; HR questions and feedback are in Arabic.
- The evaluation is a rules-based prototype, not a hiring decision or a substitute for a human reviewer.
- CV data and interview answers are processed by the local server and are not sent to an external AI provider.

Submitted by: Your Name — academy: @SDAIAAcademy
