# AZ-900 Prep Companion: Pitch Pack

Use this with the hackathon's Canva template. It is written to hit the pitch criteria directly:

| Criterion | Weight | Where it is covered |
|---|---|---|
| Problem Understanding | 20% | Slides 2 and 3 |
| Solution and Product | 25% | Slides 4 and 5 (live demo) |
| Target Users | 15% | Slide 6 |
| Impact and Scalability | 20% | Slide 7 |
| Clarity, Design and Delivery | 20% | The whole deck: one idea per slide, rehearsed timing |

**Fill in the 🔴 placeholders with your own story. Judges score "drawing on your own AZ-900 experience", so a real, specific moment beats anything generic.**

---

## Slide-by-slide content (8 slides, about 5 minutes)

### Slide 1: Title
**AZ-900 Prep Companion**
*Plan. Practise. Remember. Know when you're ready.*
Team name · four names · "Unofficial study aid, not affiliated with Microsoft"

### Slide 2: Our own AZ-900 story
Headline: **"We studied for AZ-900. This is what slowed us down."**
- 🔴 One real moment per teammate (for example: "I read the whole syllabus and still didn't know what to study on day 3", "I got a practice question wrong and never understood why", "I kept forgetting LRS vs ZRS vs GRS").
- Keep it to three short bullets with first-person quotes.

### Slide 3: The problem
Headline: **"Five pain points, five different tools, none connected."**

| Pain point | What learners do today |
|---|---|
| Don't know how to plan | Guess, or copy a generic schedule |
| Practise without understanding | Check the answer and move on |
| Forget terms | Re-read notes |
| Concepts feel abstract | Watch more videos |
| Don't know if they're ready | Book the exam and hope |

### Slide 4: The solution
Headline: **"One app, one loop."**
Show the loop diagram from the README (quiz → flashcards, scores → readiness → plan, AI buddy on the side).
One line under it: *"What you get wrong today becomes tomorrow's flashcards and next week's study plan."*

### Slide 5: Live demo (this is the slide that wins)
Switch to the live app. Full script below. Keep a screenshot backup on this slide in case the internet fails.

### Slide 6: Who it's for
- **Primary:** #1MillionDevs and other African learners preparing for AZ-900, often studying part-time around work or school, on phones, with limited data.
- **Why it fits them:** works in the browser with no account, loads fast, built-in English, Pidgin and Kiswahili, everyday examples they recognise (NEPA light, generators, market stalls).
- **Also:** bootcamp instructors and study-group leaders who want a plan and progress view for a cohort.

### Slide 7: Impact and scalability
Headline: **"AZ-900 is the first certification, not the last."**
- The topic list, questions, cards and explanations are **data**. Adding AZ-104, AI-900 or SC-900 means adding data, not rewriting the app.
- More languages by adding explanation sets. The AI buddy already handles Yoruba, Hausa and French.
- Next: optional accounts to sync across devices, community-written and reviewed question banks, installable offline app, study groups with streaks.
- 🔴 Add one honest number if you have it (for example how many people you could share it with in your cohort).

### Slide 8: How we built it, and the ask
- Built with Claude and AI-assisted tools 🔴 *(list only what you really used)*; plain JavaScript front end; serverless function keeps the API key private.
- Prompt engineering is documented in the repo (`prompts/PROMPTS.md`).
- Be honest about limits: questions are original and checked against Microsoft Learn; readiness is an estimate.
- **Ask:** "Try it now: [live link]. Repo: [GitHub link]."

---

## Demo script (90 seconds, rehearse it twice)

1. **(5s)** Open the live link. *"No sign-up. Let me load a learner who's been studying for a few days."* Click **Load demo data**.
2. **(15s) Readiness.** *"This learner is 66% ready. The weak spots are Networking and Identity, weighted by how much each domain counts."* Point at the gauge and "Focus next".
3. **(20s) Quiz.** Click **Practise** on Networking. Answer one wrong on purpose. *"Instant feedback, and it explains why the right answer is right and why this one is tempting."* Click **Explain simply**.
4. **(20s) AI Buddy.** Language: Naija Pidgin. *"Virtual network is like your own compound with a gate."* If the API key is live, click **Ask the AI buddy** with a typed question.
5. **(15s) Flashcards.** *"That wrong answer is now a flashcard. Miss it again and it comes back sooner."* Flip one card, click Again.
6. **(15s) Plan.** Go to **Plan**, click **Use my quiz results for confidence**. *"The plan rebuilds around what this learner actually got wrong."*

**Backup plan:** screenshots of steps 2, 3, 5 and 6 on the slide, and the demo video ready to play.

---

## Spoken script (about 4 minutes plus demo)

**Opening (20s).** "Preparing for AZ-900 is hard, and not because the content is impossible. It's because the learning is scattered. We know, because we just went through it. 🔴 [One teammate's story in two sentences]."

**Problem (30s).** "We kept hitting five problems: we didn't know how to plan our days, we practised questions without understanding them, we forgot the terms, the ideas felt abstract, and we never knew if we were ready. Every one of those has a separate tool. None of them talk to each other."

**Solution (30s).** "So we built one app with one loop. You take a quiz. Every question you miss becomes a flashcard that comes back at the right time. Your scores feed a readiness dashboard, and that dashboard rebuilds your study plan around your weak areas. And when something feels abstract, an AI study buddy explains it with examples from daily life here, in English, Pidgin or Kiswahili."

**Demo (90s).** Run the demo script above.

**Users (20s).** "It's built for learners like us across Africa: studying around work and school, often on a phone, with limited data. No account, fast, and in the language they speak."

**Impact (30s).** "AZ-900 is just the start. Everything in the app is data: topics, questions, cards, explanations. To add AZ-104 or AI-900 we add data, not code. Our next steps are syncing across devices, a community-reviewed question bank, and an offline app."

**Close (15s).** "We studied the cloud. Now we built the tool that helps the next learner pass. Try it now at [link]. Thank you."

---

## Likely judge questions and honest answers

| Question | Answer |
|---|---|
| Where do the questions come from? | We wrote them ourselves from the public skills outline, with AI help, and checked them against Microsoft Learn. None are real exam questions. |
| How accurate is the readiness score? | It's an estimate to guide study, weighted by the published domain percentages. It does not predict the real score. |
| How does the AI avoid wrong answers? | The prompt limits it to the AZ-900 outline, caps length, and tells it to say when it's unsure and point to Microsoft Learn. See `prompts/PROMPTS.md`. |
| Is the API key safe? | Yes. It lives only on the server function, never in the browser. |
| What about cost at scale? | The buddy uses a small, fast model with a 400-token cap. Next step is rate limiting and caching common questions. |
| Why no login? | Speed for learners and for reviewers. Optional accounts for sync are on the roadmap. |
| What did you build during the hackathon? | The planner, plus the quiz, flashcards, readiness tracker, AI buddy, prompts documentation and deployment, in four days. 🔴 *(adjust to the truth)* |

---

## Pre-submission checklist

- [ ] Live link works in a private window, on a phone, and with Vercel deployment protection turned off
- [ ] **Load demo data** works on the live site
- [ ] `ANTHROPIC_API_KEY` added in Vercel and the AI buddy answers a real question
- [ ] README placeholders filled in (live link, video link, team, tools used)
- [ ] A teammate has checked the questions against Microsoft Learn
- [ ] A native speaker has glanced at the Pidgin and Kiswahili lines
- [ ] Demo video (60 to 90 seconds) uploaded and linked
- [ ] Deck exported and linked before the **6:00 PM EAT** deadline today
- [ ] No API keys in the repo (`git log -p | grep -i sk-` should find nothing)
