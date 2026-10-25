# North Star — a Claude skill for your next job switch

Hand Claude your resume and current pay. It sets a realistic **1-year "north star"** for your next role, backs it with live market comp data, shortlists jobs that actually fit, tailors your resume for each one, and helps you apply — **stopping for your explicit "yes" before every single submit.**

## What it does

| Step | Output |
|---|---|
| 1. Profile | Reads your resume: level, ranked skills, achievements, gaps |
| 2. Market research | Comp bands for your role and 1–2 levels up in your city, with sources and dates |
| 3. North star | Three tracks — **Safe**, **Stretch**, **Pivot** — with target title, comp range and odds; one recommended, plus a 12-month plan |
| 4. Shortlist | 10–20 live postings in a tracker with fit scores, matching and missing skills |
| 5. Tailoring | `Resume_<Company>_<Role>.pdf` per job + a short cover note. No invented experience, ever |
| 6. Apply | Fills forms in your browser session; asks you any screening question it can't answer; waits for approval before each Submit |
| 7. Follow-through | Run summary and an optional weekly refresh that drafts (never submits) new applications |

## Install

### Claude Code (plugin)
```
/plugin marketplace add OWNER/north-star-skill
/plugin install career-switch-north-star@north-star-skill
```

### Claude Code (manual)
```bash
git clone https://github.com/OWNER/north-star-skill
cp -r north-star-skill/skills/career-switch-north-star ~/.claude/skills/
```

### Claude app (claude.ai / desktop)
1. Download `career-switch-north-star.zip` from the [latest release](https://github.com/OWNER/north-star-skill/releases/latest).
2. In Claude settings, open the Skills section and upload the zip.

### Claude API / Agent SDK
Upload the `skills/career-switch-north-star` folder as a custom skill. See Anthropic's skills docs.

## Usage

> "Here's my resume and I'm on ₹28 LPA fixed + 10% bonus, 60-day notice, Bengaluru, open to remote. Set my north star and find me jobs."

> "What should I be targeting for my next switch?"

Works best with web search and a browser enabled. Without a browser it stops after tailoring and gives you the files and links to apply yourself.

## Privacy & safety by design
- Your salary and resume stay **private** — never put in shared or published pages unless you ask.
- **No fabrication**: resumes, cover notes and screening answers use only what you've provided.
- **You sign in** to job sites yourself — the skill never handles passwords or OTPs.
- **Per-application approval** — approving one submit never approves the next. No mass auto-apply.
- Flags postings that charge fees, look suspicious, or ask for bank/ID documents up front.
- Every comp figure comes with a source and date.

## Repo layout
```
.claude-plugin/
  plugin.json          # Claude Code plugin manifest
  marketplace.json     # lets this repo act as a plugin marketplace
skills/
  career-switch-north-star/
    SKILL.md           # the skill
```

## Contributing
Issues and PRs welcome — especially job boards and comp sources for more regions.

## License
MIT
