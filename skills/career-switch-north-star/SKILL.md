---
name: career-switch-north-star
description: Read the user's resume and current pay, set a realistic 1-year job-switch north star with market comp research, shortlist matching jobs, tailor applications, and apply with per-job approval. Use when someone wants to plan a job switch, figure out what salary or level to target next, find jobs that fit their resume, or get help applying.
license: MIT
metadata:
  version: "1.0.0"
---

# Career Switch North Star

Turn a resume + current pay into a concrete 1-year switch target, then find and apply to jobs that move the user toward it.

## Output conventions (portable across Claude apps)
Wherever this skill says "brief" or "tracker", use the best output the current environment offers:
- **Brief**: a private document — a Docs artifact in the Claude app if available, otherwise a Markdown or PDF file.
- **Tracker**: a Sheets artifact (or an artifact with a database) if available, otherwise a `.xlsx` or `.csv` file.
Keep both private unless the user explicitly asks to share them.

## 0. Gather inputs (ask only for what's missing)
- **Resume**: attached file (PDF/DOCX) or a file in a connected folder. Read it fully.
- **Current pay**: fixed, variable/bonus, ESOPs/RSUs (with vesting), currency. Treat as confidential: never put it in a shared or published page.
- **Notice period**, current location, open-to-relocate / remote preference.
- **Hard constraints**: minimum hike, roles or companies to avoid, visa needs.
- **Job boards** to use. Defaults by market:
  - India: LinkedIn, Naukri, Instahyre, Cutshort, Wellfound, company career pages.
  - US / global: LinkedIn, Wellfound, Indeed, Otta/Welcome to the Jungle, company career pages.
  - Elsewhere: LinkedIn, company career pages, plus the dominant local board.
If the user has given these before in this session, reuse them; don't re-ask.

## 1. Build the profile
Extract from the resume: current title and level, years of experience, domain, core skills (ranked by depth of evidence), measurable achievements, education, and gaps (missing metrics, vague bullets, outdated skills). Note anything the resume implies but doesn't prove.

## 2. Research the market (always search; comp data goes stale)
- Comp bands for the current role and 1-2 levels up in the user's city/market: Levels.fyi, Glassdoor, and regional sources (e.g. AmbitionBox, Instahyre/Cutshort salary pages in India; Blind and H-1B salary data in the US), plus recent public offer data.
- Demand signals: number of live openings, which companies are hiring, which skills recur in postings.
- Typical switch hikes for the profile (note the range and the source; don't invent a single number).
Cite sources for every comp figure.

## 3. Set the north star
Propose three tracks, each with target title, target company tier/examples, target total-comp range, and probability of landing within 12 months:
- **Safe**: same function, better company or pay; high probability.
- **Stretch**: one level up or a premium company tier; medium probability.
- **Pivot**: adjacent role with better long-term ceiling; lower near-term probability.

Recommend one as the north star, with a one-paragraph reason grounded in the profile and market data. For the chosen track, list: skill gaps to close, resume changes, and a month-by-month 12-month plan (apply windows vs. upskilling windows, accounting for notice period).

Deliver this as the private **North Star Brief**. Get the user's confirmation of the north star before searching for jobs.

## 4. Shortlist jobs
- Search the chosen boards for roles matching the north-star track (and safe track as backup).
- Collect 10-20 live postings into the **tracker**: company, title, link, location/remote, posted date, stated or estimated comp, fit score (0-100), key matching skills, missing skills, apply method (Easy Apply / external ATS / referral).
- Drop postings older than ~30 days, duplicates, and anything violating hard constraints.
Show the shortlist and let the user strike or star rows before applying.

## 5. Tailor each application
- Reorder and reword resume bullets toward the posting's keywords. Never invent experience, titles, numbers, or skills; if a gap matters, flag it instead.
- Draft a short cover note / recruiter message (under 150 words) where the form allows it.
- Save tailored resumes as files (PDF by default, DOCX if the user prefers) named `Resume_<Company>_<Role>.pdf`.

## 6. Apply (human-in-the-loop, always)
- If a browser skill exists for the browser being used, read it before the first browser step.
- The user signs in to job sites themselves. Never create accounts, enter passwords, or handle OTPs for them.
- Fill forms with the tailored resume and known facts. For any screening question whose answer isn't in the inputs (expected CTC, notice period buyout, visa, relocation, diversity questions), ask the user; never guess.
- **Stop before every final Submit**: show the company, role, filled answers, and attached resume, and wait for an explicit "yes" for that application. Approval of one application is not approval of the next.
- Skip and flag anything with a fee, a suspicious domain, or requests for bank/ID documents at the application stage.
- After each submit, update the tracker: status = Applied, date, resume version, notes.

If no browser is available, stop at step 5 and hand the user the tailored resumes, cover notes, and links to apply themselves.

## 7. Follow-through
- End each run with: applied count, pending-approval count, top 3 next actions (e.g., referrals to request, skills to start on).
- If scheduled tasks are available, offer a weekly one that refreshes the shortlist and comp data and drafts (but never submits) new applications for approval.

## Guardrails
- Salary and resume contents stay private; nothing is shared or published unless the user asks.
- No fabrication anywhere: resume, answers, or cover notes.
- Comp numbers always come with a source and date.
- Respect site terms: no scraping behind logins beyond what the user's own session shows, no mass auto-apply.
