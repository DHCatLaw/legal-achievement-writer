---
description: Draft a compliant, on-brand law-firm case-result article (业绩稿) — intake → professional-responsibility gate → drafting → channel title/summary → output.
argument-hint: "[optional: case PDF path or a one-line case summary]"
---

# /achievement — Legal Achievement Writer (slash-command form)

This command runs the same workflow as `SKILL.md` in this repo. Install by copying this file to
`~/.claude/commands/achievement.md`, then call `/achievement`.

> **中文用户：** 完整中文说明见仓库内 [`SKILL.zh-CN.md`](../SKILL.zh-CN.md)、规则见
> [`ETHICS.zh-CN.md`](../ETHICS.zh-CN.md)。本命令按用户语言运作——中文提问即用中文作答。

**Stop and confirm at every decision node (use AskUserQuestion). Never guess attorney names,
never assume what may be disclosed, never invent facts. This is attorney advertising.**

## Step 0 — config
Look for `achievement.config.md` in the working directory. If found, use it. If not, run the
one-time setup interview (firm name; attorney roster + ordering policy; jurisdiction(s);
publishing channels + character limits; house ALWAYS/NEVER voice; default confidentiality
posture; save location) and write `achievement.config.md`. See `config.example.md`.

## Step 1 — intake
Case type · forum (court + division) · result · client category + count · key numbers (only if
cleared) · dates. Then confirm decision items: attorney credit & **order** (ask every time);
disclosure level (docket no. / opposing party / client name — all default **no**); IP right type.

## Step 2 — professional-responsibility gate (clear BEFORE drafting)
- **Confidentiality:** settlement confidentiality clause? → if yes, do not disclose amount/terms/
  parties. Client consent to publish / to be named? → default no name, use a category.
  Scrub privileged & non-public info after drafting.
- **Advertising:** verify every fact against court documents (nothing from memory); delete any
  guarantee / future-results implication and add a past-results disclaimer where required; no
  disparagement of opposing counsel or other firms.
See `ETHICS.md` for the rules behind each check and dual-jurisdiction (China & U.S.) notes.

## Step 3 — draft (5 parts)
① result-first lead · ② background + engagement timing · ③ strategy in labeled bold points ·
④ ruling: key numbers + court quote (original, then gloss) · ⑤ comment + attorney credit line.
Apply the firm's configured ALWAYS/NEVER voice.

## Step 4 — title & summary (per configured channel)
Give 2–3 title options and 1–2 summary options within the channel's character limits; confirm
before finalizing. (WeChat 公众号 default: title ≤ 26, summary ≤ 54.)

## Step 5 — output
Save as `YYYYMMDD <title>.md` to the configured location. Include the mandatory disclaimer and a
source line. Remind the user to log publish date / link / matter / attorneys in their system.
