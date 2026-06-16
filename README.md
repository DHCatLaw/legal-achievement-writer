# Legal Achievement Writer

**English** · [中文](README.zh-CN.md)

**A structured, ethics-gated drafting assistant that turns a real case result into a
publication-ready law-firm article (案件成果稿 / 业绩稿).**

Works as a portable [Agent Skill](SKILL.md) or as a Claude Code [slash command](commands/achievement.md)
(`/achievement`). Configurable for any firm; built with **attorneys** in mind — and especially
**dual-qualified lawyers (e.g., China & U.S.)** who must satisfy more than one set of advertising
rules at once.

---

## Why this exists

Writing up a win is deceptively risky. The same article is simultaneously *marketing* and a
*regulated professional communication*. Most drafting tools optimize only for engagement and will
happily generate text that breaches confidentiality, over-promises, or disparages opposing
counsel. This skill puts the **professional-responsibility checks first** and the prose second.

### What it does

1. **Guided intake** — asks for the matter type, forum, result, client category, key numbers,
   and dates, instead of letting you free-write from memory.
2. **A mandatory compliance gate** — before a word is drafted, it walks a checklist:
   confidentiality (settlement terms, client consent, privileged facts), fact-verification against
   the court record, no guarantees / no unjustified expectations, and no disparagement.
   See **[ETHICS.md](ETHICS.md)**.
3. **House-voice drafting** — a proven 5-part structure (lead → background → strategy → ruling →
   comment), applying your firm's own ALWAYS/NEVER style rules.
4. **Channel-aware titles & summaries** — optimizes within real display limits (e.g., WeChat
   公众号 title ≤ 26 chars, summary ≤ 54), offering options instead of one take-it-or-leave-it line.
5. **Clean output** — a dated Markdown file with a built-in past-results disclaimer and a source line.

### Advantages

- **Compliance is not optional and not an afterthought** — the gate blocks content rather than
  flagging it later.
- **Firm-agnostic** — a one-time setup interview writes `achievement.config.md`; no internal paths,
  names, or branding are baked in.
- **Multi-jurisdiction by design** — confidentiality, no-guarantee, and no-disparagement checks
  map to both U.S. (ABA/state Rule 1.6 & 7.1) and PRC (《律师法》保密义务、《律师执业行为规范》业务推广)
  principles; dual-qualified lawyers are told to follow the stricter rule.
- **Stops and asks** — it confirms attorney credit/order and every disclosure decision rather than
  guessing, because those choices carry professional meaning.
- **Portable** — one repo, two install paths (Agent Skill or slash command).

## Who it's for

Litigators and IP/transactional attorneys who publish case results — on a firm blog, LinkedIn, or
a WeChat 公众号. It is **especially useful for China–U.S. dual-qualified lawyers**, whose result
posts must clear both regimes' advertising and confidentiality rules in a single piece of copy.

## Install

**As an Agent Skill:** place this folder where your host loads skills (it reads `SKILL.md`).

**As a Claude Code slash command:**
```bash
cp commands/achievement.md ~/.claude/commands/achievement.md
# restart Claude Code, then run /achievement
```

## Configure (one time)

```bash
cp config.example.md achievement.config.md
# edit achievement.config.md with your firm name, attorney roster + ordering policy,
# jurisdiction(s), publishing channels + limits, house voice, and confidentiality posture
```
Or just run the skill once with no config present — it will interview you and write the file.

> Keep `achievement.config.md` **out of version control** if it holds anything non-public.

## Use

Invoke the skill (or `/achievement`), optionally pointing it at the order/decision PDF. It runs
intake → compliance gate → draft → titles/summaries → output, confirming with you at each step.

See a fully fictional sample in **[examples/example-output.md](examples/example-output.md)**.

## Disclaimer

This software is provided for informational purposes and is **not legal advice**. It does not
substitute for the current rules of professional conduct of your own bar(s). You are responsible
for the compliance of anything you publish. See [ETHICS.md](ETHICS.md) and [LICENSE](LICENSE).

---

<sub>Created by <b>Hongchang (Richard) Deng</b> — California Attorney (Bar No. 354529) ·
USPTO Trademark Attorney · 中国执业律师 · 中国专利代理师. Shared as an open-source tool for the
legal community. Contributions and jurisdiction-specific rule notes welcome via PR.</sub>
