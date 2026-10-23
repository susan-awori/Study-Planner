# 🎓 AZ-900 Prep Companion

> One app that covers the whole AZ-900 revision loop: **plan → quiz → flashcards → readiness → AI study buddy**, built by learners for the next cohort of #1MillionDevs.

Built for the **Vibe Coding Hackathon for #1Million Devs 2026 (AZ-900 Exam Prep Edition)**.

**Live demo:** _add your Vercel link here_  ·  **Demo video:** _add link here_  ·  **Pitch deck:** _https://canva.link/l95dezikeygmzzh_

> **Tip for reviewers:** open the demo and click **Load demo data** in the header. It fills in a full study plan, quiz history, flashcards and readiness dashboard in one click.

## ⚠️ Unofficial disclaimer

This is an independent, unofficial study tool created for learning and hackathon evaluation. It is **not** affiliated with, endorsed by, or sponsored by Microsoft. Content follows the public [AZ-900 skills outline on Microsoft Learn](https://learn.microsoft.com/en-us/credentials/certifications/azure-fundamentals/). **All questions are original. No real exam questions and no Microsoft logos are used.**

---

## 📌 The problem

Learners preparing for AZ-900 told us the same things:

- **"I don't know how to split the syllabus across the days I have."** (Planning)
- **"I practise questions but don't understand why an answer is right or wrong."** (Practice)
- **"I forget terms like LRS vs ZRS vs GRS."** (Memory)
- **"Cloud ideas feel abstract."** (Understanding)
- **"I don't know if I'm ready to book the exam."** (Confidence)

Most tools solve one of these. Learners end up juggling five different tools, and none of them talk to each other.

## 💡 Our solution

A single app where each part feeds the next:

```
   ┌──────────┐   miss a question   ┌────────────┐
   │   Quiz   │ ──────────────────▶ │ Flashcards │
   └────┬─────┘                     └────────────┘
        │ scores by topic
        ▼
   ┌───────────┐  weak topics   ┌──────────┐
   │ Readiness │ ─────────────▶ │   Plan   │  (rebuilt around your weak areas)
   └───────────┘                └──────────┘
        ▲
        │ "explain this simply"
   ┌────┴──────┐
   │ AI Buddy  │  everyday African examples, local languages
   └───────────┘
```

---

## ✨ Features

| Tab | What it does |
|---|---|
| 📅 **Plan** | Enter your exam date, hours per day, rest day and confidence per topic. Get a day-by-day plan weighted toward weak areas, with practice sessions, a final light-review day, a countdown, progress checklists, print and copy. **"Use my quiz results"** sets your confidence from real scores and rebuilds the plan. |
| 📝 **Quiz** | 55 original questions across all 11 skills-outline topics. Choose a topic, a mixed round, or **My weakest topics**. Every answer gives instant feedback and an explanation of why the right answer is right and why the tempting one is wrong. |
| 🧠 **Flashcards** | 36 starter cards plus every question you miss. Spaced repetition with Leitner boxes (gaps of 1, 2, 4, 8 and 16 days). Cards you get wrong come back first. |
| 📊 **Readiness** | Estimated readiness score weighted by the AZ-900 domain percentages, a per-topic breakdown, a day streak, "focus next" topics, and a button to rebuild your plan from your scores. |
| 🤖 **AI Study Buddy** | Simple explanations with everyday African examples (the grid vs a generator, a market stall, a compound with a gate). Built-in English, Naija Pidgin and Kiswahili, plus Yoruba, Hausa and French through the AI. Ask your own question and get a short answer ending with "Remember" and an "Exam tip". |

Also: dark mode, keyboard-accessible controls, screen-reader labels, reduced-motion support, mobile-friendly layout, and all progress saved on the device (no account needed).

---

## 🛠️ Tech stack

| Layer | Choice | Why |
|---|---|---|
| Front end | Plain HTML, CSS and JavaScript in one `index.html` | Loads instantly, no build step, easy for a team to merge and read |
| Storage | Browser `localStorage` | No sign-up friction; learners start in seconds |
| AI | Anthropic Claude API, called from a Vercel serverless function (`api/buddy.js`) | The API key stays on the server and is never in the browser |
| Hosting | Vercel | Free, deploys from GitHub, runs the serverless function |
| Build tools | Claude, plus the other vibe-coding tools our team used _(list only the ones you really used)_ | |

### Project structure

```
├── index.html          # the whole front end (Plan, Quiz, Flashcards, Readiness, AI Buddy)
├── api/
│   └── buddy.js        # serverless function that talks to the Claude API
├── prompts/
│   └── PROMPTS.md      # every AI prompt and the reasoning behind it
├── PITCH.md            # pitch deck content and demo script
├── .env.example        # shows which environment variables are needed
└── README.md
```

---

## 🧩 How it works

**Planner.** Each topic gets a weight from its typical study minutes and the learner's confidence (lower confidence means more time). Time is split into learn, revise and practice blocks, spread across the available days (skipping the rest day), with a light-review day before the exam.

**Quiz and flashcards.** Questions live in a data array (correct answer first, shuffled when shown). A wrong answer is saved as a flashcard in Leitner box 1, due today. "Got it" moves a card up a box and schedules it further away. "Again" drops it back to box 1.

**Readiness.** Per-topic score is `correct ÷ max(attempts, 3)`, so one lucky answer cannot show 100%. Topic scores are weighted by domain percentages (about 27.5%, 37.5% and 32.5%, the midpoints of the published ranges) and combined into one number. It is an estimate for motivation, not a prediction of the real exam.

**AI Buddy.** The browser sends only the topic, language and question to `/api/buddy`. The function adds a carefully written system prompt (see [`prompts/PROMPTS.md`](prompts/PROMPTS.md)) and calls the Claude API. If the function is not available, the app falls back to the built-in explanations.

---

## 🚀 Run it

### Option A: front end only (no setup)

Open `index.html` in a browser. Plan, Quiz, Flashcards, Readiness and the built-in explanations all work. The "Ask the AI buddy" button will say it is not connected.

### Option B: everything, including the AI buddy

1. **Get an API key.** Create an account at [console.anthropic.com](https://console.anthropic.com), add a small amount of credit under Billing (API usage is billed separately from a Claude.ai subscription), then go to **API keys → Create key** and copy it.
2. **Add it locally.** Copy `.env.example` to `.env.local` and paste your key:
   ```
   ANTHROPIC_API_KEY=your-key-here
   ```
   `.env.local` is already in `.gitignore`. **Never commit your key.**
3. **Start the local server** (needs [Node.js](https://nodejs.org)):
   ```bash
   npx vercel dev
   ```
   Follow the prompts the first time (log in, accept defaults), then open the address it prints, usually `http://localhost:3000`.

### Deploy to Vercel

1. Push the repo to GitHub and import it in Vercel.
2. In **Project Settings → Environment Variables**, add `ANTHROPIC_API_KEY`.
3. Redeploy. (Optional: set `BUDDY_MODEL` to choose a different Claude model.)

---

## 🔒 Privacy and safety

- No accounts and no tracking. Scores, flashcards and plans stay in the learner's browser. **Reset my data** in the header clears them.
- The AI function only receives the topic, language and the learner's question (capped at 400 characters).
- The AI prompt limits answers to the AZ-900 outline, refuses to write real exam questions, admits uncertainty on details that change, and ignores instructions typed into the question box.

---

## ✅ Quality and testing

- Every tab was exercised end to end in a headless browser: plan generation, a full quiz round, flashcard review, readiness, plan update from scores, demo data, and the AI fallback.
- Questions were written from the public skills outline and **should be verified against Microsoft Learn** before relying on them for the real exam.
- The Pidgin and Kiswahili explanations were drafted with AI and **should be reviewed by native speakers**.

## ⚠️ Known limitations

- Progress is stored per device and browser, so there is no cross-device sync yet.
- The AI buddy function has no rate limiting yet. Add one before sharing the link widely.
- 55 questions is a starting bank, not a full exam simulator.
- The readiness number is an estimate based on self-practice, not an official score.

## 🗺️ Roadmap and scalability

- **Optional accounts** (Supabase) to sync progress across devices.
- **Larger question bank**, community-contributed and reviewed.
- **More certifications.** The topic list, question bank and explanations are plain data, so AZ-104, AI-900, SC-900 and others can be added by swapping the data. The app logic stays the same.
- **More languages** and **voice** for learners with limited data or reading time.
- **Mobile app** and **offline mode** (installable web app).
- **Study groups**: shared plans and friendly streak leaderboards for cohorts.

---

## 👥 Team
SUSAN ONYANGO
FIONNA SIBORA
FRANCIS TAIWO
HARITH PARVEZ

## 📄 Licence

MIT. See [LICENSE](LICENSE).
