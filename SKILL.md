---
name: legal-achievement-writer
description: >-
  Structured drafting assistant that turns a real case result into a publication-ready
  "achievement article" (案件成果稿 / 业绩稿) for a law firm's social channels, blog, or
  newsletter. Walks the user through information intake, a mandatory professional-responsibility
  gate (confidentiality / no-guarantees / no-disparagement / fact-verification), drafting in a
  configurable house voice, and channel-specific title & summary optimization. Built for
  attorneys — and especially dual-qualified (e.g., China & U.S.) lawyers who must satisfy more
  than one set of advertising rules. Trigger when the user wants to write up a case win, draft a
  result post, produce a "业绩稿", or publicize a litigation/IP/transactional outcome.
license: MIT
---

# Legal Achievement Writer

> **Language:** This is the machine-loaded skill (English). A human-readable Chinese mirror is at
> [`SKILL.zh-CN.md`](SKILL.zh-CN.md). The skill operates in the user's language — respond in
> Chinese to a Chinese-speaking user.

Turn a case result into a compliant, on-brand, publication-ready article.

> **Operating principle — stop and confirm at every decision node.** Use the host's
> question/confirmation mechanism (e.g. AskUserQuestion). Never guess attorney names, never
> assume what may be disclosed, never invent facts. This is attorney advertising; an error is
> a professional-responsibility problem, not just a typo.

---

## 0. First run — load or create the firm config

Before anything else, look for a configuration file named **`achievement.config.md`** in the
working directory (or ask the user where theirs lives).

- **If it exists**, read it and use those values throughout (firm name, attorney roster &
  ordering policy, jurisdiction(s), publishing channels & character limits, house voice
  do/don't list, default confidentiality posture, storage location).
- **If it does not exist**, run the **one-time setup interview** below, then write the answers
  to `achievement.config.md` so future runs skip this step. Confirm each answer before saving.

**Setup interview questions:**

1. Firm name and how it should appear in copy (e.g., "Smith & Co." / "本所统一称谓").
2. Attorney roster — names as they should be printed, and the **default ordering policy**
   (alphabetical / by seniority / lead-first / **ask every time**). *Recommended: ask every time.*
3. Jurisdiction(s) the firm and its lawyers are admitted in (drives which advertising rules
   apply — see `ETHICS.md`). For dual-qualified lawyers, list all.
4. Publishing channel(s) and their display limits — e.g., WeChat 公众号 (title ≤ 26 chars for
   mobile feed, summary ≤ 54 chars), LinkedIn, firm blog, X/Twitter. Store each channel's limits.
5. House voice — 3–6 ALWAYS rules and 3–6 NEVER rules (tone, person, banned words). A starter
   set is in `config.example.md`.
6. Default confidentiality posture (e.g., "never name clients unless written consent on file").
7. Where to save finished articles (path or "ask each time").

> Keep `achievement.config.md` **out of version control** if it contains anything non-public.
> A redacted template is provided as `config.example.md`.

---

## 1. Information intake (Q&A)

Ask the following before drafting. Do not draft without the key items.

### 1A. Case basics

| Field | Capture |
|------|---------|
| Matter type | TRO/PI defense · affirmative TRO/PI · Schedule A · patent invalidity · trademark/TTAB · arbitration · other |
| Forum | Federal district (state + division) / TTAB / arbitration / platform complaint |
| Result | The actual ruling (PI denied / TRO dissolved / settlement / dismissal / account released / opposition denied) |
| Client description | Category + count (use a category, not a name, by default) |
| Key numbers | Frozen amount / settlement figure / timeline — only if the user provides and clears them |
| Dates | Filing / ruling / closing dates |

### 1B. Decision items (confirm each — never assume)

**① Attorney credit & order** — Who worked on it? In what printed order? *Ask every time per
config policy; ordering carries meaning (lead vs. support vs. ranking).*

**② Disclosure level** — Put the docket/case number in the body? (default: no) · Name the
opposing party? (default: no) · Name the client / store / company? (default: no — use a category).

**③ Right type** (if IP) — Utility patent / design patent / utility model / trademark / copyright.
Type affects how the "capability" is characterized.

---

## 2. Professional-responsibility gate (must clear before drafting)

> This is the heart of the skill. **Every item below is confirmed with the user. Any "no /
> not sure" means that content does not go into the article.** See `ETHICS.md` for the rules
> behind each check, including notes for dual-qualified (China & U.S.) lawyers.

### Confidentiality

- **Settlement terms** — Did the matter settle? If so, does the settlement contain a
  confidentiality clause? If yes, the amount, terms, and party names must **not** be disclosed.
  *(Most settlements are confidential. Disclosing terms can breach both the agreement and the
  duty of confidentiality.)*
- **Client consent** — Has the client agreed to publication? Has the client agreed to be
  identified? Default: no client name; use a category. Identify only with clear consent.
- **Privileged / non-public information** — After drafting, scan each paragraph for: internal
  legal analysis or strategy beyond the public record; confidential facts the client shared;
  litigation information not yet public. Remove all of it, even if the client knows it.

### Advertising compliance

- **Fact verification** — Every number, date, court name, judge name, and matter type must be
  checked against the actual court documents. Nothing from memory.
- **No guarantees / no unjustified expectations** — After drafting, delete or rewrite any
  phrase that promises outcomes or implies past results predict future ones ("guaranteed win",
  "we always win", "all similar cases can…"). Where the jurisdiction requires it, add a
  past-results disclaimer (template in `ETHICS.md`).
- **No false or unfair comparison** — Do not elevate the firm by disparaging opposing counsel,
  the bench, or other firms.

---

## 3. Drafting rules

### 3A. Structure (standard 5 parts)

```
① Lead      — result first; one sentence stating the core win
② Background — what the client faced + when they engaged the firm
③ Strategy   — the concrete approach, broken into labeled points
④ Ruling     — key numbers + the court's language (quote original, then explain)
⑤ Comment    — capability characterization + attorney credit line
```

### 3B. Voice (apply the firm's configured ALWAYS/NEVER; sensible defaults below)

**ALWAYS** — name the firm consistently · state result numbers on their own, not buried · break
strategy into labeled, bolded points · sign the participating attorneys in the closing paragraph ·
quote court language in the original, with a plain-language gloss underneath.

**NEVER** — first person ("we", "our firm") in place of the firm name · melodrama ("dire
situation", "cash flow devastated") — state facts plainly · spotlight the opponent's mistakes
instead of what the firm did · client names without consent · docket/patent numbers unless asked ·
sensational words.

### 3C. Capability framing by matter type

| Type | Capability keywords |
|------|--------------------|
| Utility-patent PI/TRO defense | claim construction, prior-art search, validity analysis, element-by-element comparison (technical depth) |
| Design-patent TRO defense | rapid response, non-infringement analysis, asset/account release |
| Affirmative TRO/PI | end-to-end handling, filing through injunction, cross-platform evidence |
| Schedule A | multi-defendant coordination, efficient filing |
| Trademark / TTAB | administrative-procedure depth, opposition/cancellation strategy |
| Low settlement vs. freeze | negotiation, settlement-vs-frozen-amount contrast (the numbers are the story) |
| Award recognition | cross-border enforcement, China–U.S. procedural coordination |

---

## 4. Title & summary (per publishing channel)

After the body, optimize for each configured channel. WeChat 公众号 example (use the firm's
configured limits):

- **Title — best mobile display ≤ 26 chars.** Formula: `[Firm] + [verb + result] + [forum/region]`.
  Include a number where natural; include the forum/region; no exclamation marks or hype words;
  give the user **2–3 options** and confirm.
- **Summary — best bubble display ≤ 54 chars.** Has a hook; focuses on the firm's strategy/
  capability, not the opponent's failure; adds something the title doesn't (client count /
  strategy direction / one core result); give **1–2 options** and confirm.

---

## 5. Output

```
Format : .md  (Markdown; convert to other formats only if the user asks)
Naming : YYYYMMDD <title>.md
```

File template:

```markdown
# <title>

> **【Summary / 摘要】** <summary>

(five-part body)

---
<MANDATORY DISCLAIMER — see ETHICS.md; insert the firm's configured/jurisdiction-appropriate text>

*Source: <case name>, <court>, Order dated <date>*
```

Save to the location set in config (or ask). Then run whatever catalog/index step the firm uses,
if any.

---

## 6. After publishing (remind the user)

Once published, record in the firm's matter/marketing system: publish date, public link,
related matter, and the participating attorneys.
