# ArthArohi — ElevateHer (Track 3)

##Live Link
https://vision-empower-portal.lovable.app

## The Idea

- Most "empowerment" platforms are content dumps — course links, scheme lists, articles — the same catalogue for every visitor.
- A 19-year-old student, a housewife, a pregnant woman, and a widow all have completely different needs, but generic content sites treat them identically. That's not empowerment, it's a folder of links.
- **ArthArohi fixes this by putting personalization at the core, not as a bonus feature.** A short onboarding flow feeds an AI agent that generates a personal weekly action plan — a specific video, a skill to start, a scheme she's actually eligible for, and a quiz — instead of a menu of everything we have.
- Built for Indian women — students, housewives, working women, small business owners, rural entrepreneurs, mothers, and career-break women — across education, financial literacy, and career growth.

## Important Links

- **Live Deployment Link:** [Insert URL here]
- **Demo Video Link:** [Insert YouTube/Drive URL here]

## Features

**AI Life Navigator (flagship)**
- Onboarding captures who she is, age, education, income bracket, goal, state, interests, and time available
- An n8n-orchestrated AI pipeline cross-checks her answers against real scheme eligibility data before generating a roadmap — so it never recommends something she doesn't qualify for
- Returns a personalized weekly plan: one video, one skill, one eligible scheme, one quiz, with a plain-language reason for each pick

**AI Budget Coach**
- Enter income, expenses, and a savings goal
- AI-generated budget split and emergency fund target
- Clearly labelled as educational guidance only, never financial advice

**Sakhi — Site Assistant**
- Floating chat assistant available on every page
- Answers questions by voice or text, aware of which page she's on
- Built for users with limited digital literacy, not just power users

**Opportunity Finder**
- Filterable database of government schemes, scholarships, internships, grants, and free certifications
- Filter by state, occupation, and need — no external APIs required

**Curated Learning Hub & Skill Modules**
- Real curated video content from trusted sources (Khan Academy, NPTEL, Apna College, and India/Hindi-specific channels for home-and-life skills)
- Per-video completion tracking
- Auto-generated, downloadable certificate on course completion

**Digital Safety Academy**
- Modules on phishing, OTP fraud, fake job scams, romance scams, deepfake awareness, and QR-code fraud

**Career Readiness Dashboard**
- A computed readiness score, not just a raw progress counter
- Tracks skills learned, schemes eligible for, courses completed, hours invested

**Illustrative Case Studies**
- Two to three representative personas (not real individuals) the Life Navigator can reference, giving an emotional anchor without a full community board

**Accessibility Layer**
- Regional language toggle (English + Odia/Hindi)
- Text-to-speech on key pages
- First-Time User Mode — large icons, minimal text, for low digital literacy

**Gamification**
- XP, streaks, and badges layered on existing progress data

## Business Model

- **Who pays / how it sustains:** Freemium core — all learning content, the Opportunity Finder, and Digital Safety Academy stay free, since access is the whole point.
- **Revenue paths we'd pursue post-hackathon:**
  - **B2G / NGO partnerships** — state skill-development missions, SHG networks, and women-focused NGOs sponsor access for their beneficiaries in exchange for outcome reporting (courses completed, schemes accessed).
  - **CSR sponsorship** — corporates fund "seats" for rural women as part of CSR mandates, in exchange for branded impact reports, not ads inside the product.
  - **Affiliate/referral on legitimate financial products** — e.g. verified micro-loan or insurance partners in the Opportunity Finder, disclosed clearly, never influencing the AI's recommendations.
  - **Premium tier (later, optional)** — advanced features like 1:1 mentorship matching or resume review for working women/entrepreneurs who can pay, cross-subsidizing free access for others.
- **Distribution (the real go-to-market problem):** many target users won't discover or use a website directly. Planned channel: WhatsApp-based delivery through existing trusted touchpoints — ASHA workers, anganwadi workers, and Self-Help Groups — sharing simple voice-note based content, rather than expecting direct app/website adoption from day one.
- **Why this isn't "just a content site":** the AI Life Navigator is the product — personalization is what justifies a platform over a YouTube playlist, and it's what a partner or sponsor is actually paying to provide at scale.

## Tech Stack & Tools

**Frontend**
- React + TanStack Start / TanStack Router
- Tailwind CSS + shadcn/ui (Radix UI primitives)
- Framer Motion for animation
- Recharts for dashboard visualizations
- Vite build tooling

**Backend / Data**
- Supabase (Postgres + client SDK) for data and auth
- Row Level Security for access control on stored data

**AI / Automation**
- n8n for agent orchestration (webhook-triggered workflows)
- Google Gemini (`gemini-1.5-flash` / `gemini-2.0-flash`) as the LLM powering the Life Navigator, Budget Coach, and Sakhi assistant
- Custom eligibility-filtering logic (Code nodes) that constrains the AI to only recommend schemes/courses the user is actually eligible for — a real grounding step, not free-form generation

**Tooling**
- Built with Lovable (frontend scaffolding) + Claude (planning, prompt design, and n8n workflow architecture)
- GitHub for version control

## Documentation

**How the AI Life Navigator works under the hood:**
1. User submits onboarding profile (role, age, education, income, goal, state, interests, time available) via the frontend.
2. Request hits an n8n webhook, which first runs a filtering step against our schemes and course-catalog data — narrowing to only what she's genuinely eligible for and relevant to her stated goal.
3. That filtered, grounded data — not the raw user input alone — is passed to Gemini, along with a system prompt instructing it to recommend only from the provided list and explain *why* each pick fits her specifically.
4. Gemini returns structured JSON (greeting, video, skill, scheme, quiz topic, weekly focus), which the webhook returns directly to the frontend and renders on the dashboard.

**How we coordinated our AI tools:**
- **Claude** was used throughout for architecture decisions, prompt engineering, and debugging the n8n workflows (e.g., diagnosing a Gemini quota misconfiguration during testing, choosing Gemini over other providers for reliable structured JSON output).
- **n8n** hosts the actual agent logic as separate, independently testable workflows (Life Navigator, Budget Coach, Site Assistant) rather than one monolithic pipeline — so a failure in one never takes down the others.
- **Lovable** was used to scaffold and iterate on the frontend, wired to the above n8n webhooks rather than calling any LLM directly from the browser.

**Known scope decisions (deliberate, not gaps):**
- No real SMS/WhatsApp bot, no live stock trading data or advice, no real payment integration — named explicitly as future roadmap rather than built partially.
- Course completion tracking is self-paced (user marks videos watched) rather than verified watch-time, which we've been upfront about rather than overselling as automatic detection.


##Screenshots
<img width="1901" height="1078" alt="Screenshot 2026-07-11 003859" src="https://github.com/user-attachments/assets/1daf0830-8e6e-4945-9dc1-d5dc3c26e731" />
<img width="1901" height="1078" alt="Screenshot 2026-07-11 003955" src="https://github.com/user-attachments/assets/2b459a12-2d1a-4fc2-9df7-f19f47e880e9" />
<img width="1901" height="1075" alt="Screenshot 2026-07-11 003940" src="https://github.com/user-attachments/assets/11ee4e4d-597f-4e6f-bba3-51dc397eefb7" />
<img width="1900" height="1078" alt="Screenshot 2026-07-11 003932" src="https://github.com/user-attachments/assets/6c3364de-2917-4335-9cae-fb1b0d70ae85" />
<img width="1902" height="1078" alt="Screenshot 2026-07-11 003919" src="https://github.com/user-attachments/assets/c5c7dfb9-9f67-4582-8c4c-96619767f052" />
<img width="1900" height="1078" alt="Screenshot 2026-07-11 003909" src="https://github.com/user-attachments/assets/9fb35b6e-c1b0-40cc-8339-19bcb32495e7" />



