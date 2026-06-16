# 律师业绩稿写作助手 · Legal Achievement Writer

> 中英对照 · Bilingual (中文 first, English follows)

**一个把真实案件结果，转化为合规、贴合律所风格、可直接发布的「案件成果稿 / 业绩稿」的结构化写作助手。**

**A structured, ethics-gated drafting assistant that turns a real case result into a
publication-ready law-firm article (业绩稿).**

可作为可移植的 [Agent Skill](SKILL.md) 使用，也可作为 Claude Code 斜杠命令（`/achievement`）使用。任何律所均可配置；专为**律师**设计——尤其是必须同时满足两套执业宣传规则的**中美双重执业律师**。

Works as a portable [Agent Skill](SKILL.md) or a Claude Code slash command (`/achievement`).
Configurable for any firm; built for **attorneys** — especially **dual-qualified (e.g., China &
U.S.) lawyers** who must satisfy more than one set of advertising rules at once.

> 中文用户：纯中文说明见 [SKILL.zh-CN.md](SKILL.zh-CN.md)，执业规则见 [ETHICS.zh-CN.md](ETHICS.zh-CN.md)。

---

## 为什么需要它 · Why this exists

写一篇胜诉/成果稿，风险常被低估：同一篇文章既是**营销**，又是受规则约束的**执业宣传**。多数写作工具只为传播效果优化，会毫不犹豫地生成可能**泄密、过度承诺或诋毁对方律师**的文字。本助手把**执业道德审查放在第一位**，文采放在第二位。

Writing up a win is deceptively risky: the same article is at once *marketing* and a *regulated
professional communication*. Most tools optimize only for engagement and will happily produce text
that breaches confidentiality, over-promises, or disparages opposing counsel. This skill puts the
**professional-responsibility checks first** and the prose second.

## 它做什么 · What it does

1. **引导式信息采集** —— 逐项问清案件类型、法院、结果、客户类别、关键数字与日期，而非凭记忆自由发挥。
   *Guided intake* — asks for matter type, forum, result, client category, numbers, and dates
   instead of free-writing from memory.
2. **强制合规关卡** —— 动笔前先走清单：保密（和解条款、客户同意、特权信息）、对照法院文件核实事实、
   禁止过度承诺、禁止诋毁。详见 [ETHICS.md](ETHICS.md)。
   *A mandatory compliance gate* — confidentiality, fact-verification, no guarantees, no
   disparagement — before a word is drafted. See [ETHICS.md](ETHICS.md).
3. **律所风格起草** —— 经实践检验的五段结构（开头→背景→策略→裁定→点评），套用你所的 ALWAYS/NEVER 规则。
   *House-voice drafting* — a proven 5-part structure, applying your firm's own style rules.
4. **按渠道优化标题与摘要** —— 在真实显示字数内优化（如微信公众号标题 ≤ 26 字、摘要 ≤ 54 字），给多个备选。
   *Channel-aware titles & summaries* — within real display limits, offering options.
5. **干净的产出** —— 带日期的 Markdown，内置「过往业绩不代表未来结果」免责声明与案件来源行。
   *Clean output* — a dated Markdown file with a built-in past-results disclaimer and source line.

## 优势 · Advantages

- **合规前置拦截，而非事后标记** / Compliance blocks content, it doesn't just flag it later.
- **与具体律所解耦** —— 一次性初始化生成 `achievement.config.md`，不内嵌任何内部路径/人名/品牌。
  / Firm-agnostic via a one-time setup; no internal paths, names, or branding baked in.
- **天生多法域** —— 审查同时对应美国（ABA/各州 Rule 1.6 & 7.1）与中国（《律师法》/《律师业务推广行为规则》），
  双重执业律师**从严遵守**。/ Multi-jurisdiction by design (U.S. + PRC); dual-qualified lawyers follow the stricter rule.
- **会停下来问你** —— 律师署名与排序、每项披露决定都先确认。/ It stops and confirms credit, order, and disclosure.
- **可移植** —— 一个仓库，两种安装方式。/ One repo, two install paths.

## 适用对象 · Who it's for

发布案件成果的诉讼律师、知识产权/商事律师——无论发在律所官网、领英还是微信公众号。**对中美双重执业律师尤其有用**：成果稿须在同一篇里同时通过两套法域的宣传与保密规则。

Litigators and IP/transactional attorneys who publish case results — on a firm blog, LinkedIn, or
WeChat. **Especially useful for China–U.S. dual-qualified lawyers.**

## 安装 · Install

**作为 Agent Skill：** 把本文件夹放到宿主加载 skill 的位置（读取 `SKILL.md`）。
*As an Agent Skill:* place this folder where your host loads skills (it reads `SKILL.md`).

**作为 Claude Code 斜杠命令 · As a Claude Code slash command:**
```bash
cp commands/achievement.md ~/.claude/commands/achievement.md
# 重启 Claude Code，然后运行 /achievement · restart, then run /achievement
```

## 配置（一次性）· Configure (one time)

```bash
cp config.example.md achievement.config.md
# 填入律所名称、律师名册与排序、执业法域、发布渠道字数、风格、保密立场
# fill in firm name, attorney roster + ordering, jurisdiction(s), channels + limits, voice, posture
```
或直接在无配置时运行一次，本助手会访谈你并写入该文件。
Or just run it once with no config present — it will interview you and write the file.

> 若 `achievement.config.md` 含非公开信息，请排除在版本控制之外。
> Keep `achievement.config.md` out of version control if it holds anything non-public.

## 使用 · Use

调用本助手（或 `/achievement`），可把裁定 PDF 指给它。它依次走：采集 → 合规关卡 → 起草 → 标题/摘要 → 产出，每步与你确认。完整虚构样例见 [examples/example-output.zh-CN.md](examples/example-output.zh-CN.md)（中文）/ [examples/example-output.md](examples/example-output.md)（English）。

Invoke the skill (or `/achievement`), optionally pointing it at the order PDF. It runs intake →
compliance gate → draft → titles/summaries → output, confirming at each step.

## 免责声明 · Disclaimer

本软件仅供参考，**不构成法律意见**，也不替代你所属律师协会现行的执业行为规范。你须对所发布内容的合规性自行负责。详见 [ETHICS.md](ETHICS.md) 与 [LICENSE](LICENSE)。

This software is for informational purposes and is **not legal advice**. It does not substitute for
your bar's current rules of professional conduct. You are responsible for the compliance of anything
you publish. See [ETHICS.md](ETHICS.md) and [LICENSE](LICENSE).

---

## 关于作者 · About the author

<table>
<tr>
<td valign="top">

**邓宏昌 · Hongchang (Richard) Deng** —— 中美双重执业律师 / China &amp; U.S. lawyer

- 美国加州律师（Bar No. 354529）· USPTO 商标律师 · 中国执业律师 · 中国专利代理师
  <br/>California Attorney · USPTO Trademark Attorney · PRC Lawyer · PRC Patent Attorney
- **LawMay P.C.（路迈律师事务所）** 合伙人 · 深圳 · 加州 / Partner, Shenzhen &amp; California
- 专注中美跨境知识产权诉讼与合规 / Cross-border IP litigation &amp; compliance
- 🔗 [www.lawmayus.com](https://www.lawmayus.com) ｜ GitHub [@DHCatLaw](https://github.com/DHCatLaw)

本工具作为开源项目分享给法律同行，欢迎通过 PR 贡献各法域的规则补充与改进。
Shared as open source for the legal community — PRs with jurisdiction-specific notes welcome.

欢迎交流（中文）· Feel free to connect →

</td>
<td valign="top" width="220">
<img src="assets/wechat-qr.png" width="190" alt="WeChat — 邓宏昌 中国及美国律师"/>
<br/><sub align="center">微信 · WeChat</sub>
</td>
</tr>
</table>
