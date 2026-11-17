# dsh-extra-income

[![npm](https://img.shields.io/npm/v/dsh-extra-income)](https://www.npmjs.com/package/dsh-extra-income)
[![license](https://img.shields.io/npm/l/dsh-extra-income)](LICENSE)
[![GitHub stars](https://img.shields.io/github/stars/zhengqiuyang/dsh-extra-income?style=flat)](https://github.com/zhengqiuyang/dsh-extra-income/stargazers)

> A [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness) plugin that puts the `monetize` skill into your profile's skill catalog — install once, every agent in that profile can use it.

> 把 `monetize` 技能打包进 DeepSeek Harness：装一次，profile 里所有 agent 都能用。把职业经历变成一份诚实、可执行的副业收入方案。

**If this helps you, please give it a star** — it helps others find it.

[Install](#install) · [What it does](#what) · [How it works](#how) · [Verification](#verification) · [Structure](#structure)

<a id="install"></a>

## Install

```bash
dsh plugin add dsh-extra-income
```

Or in the Web UI: **Plugins** → **Add plugin** → `dsh-extra-income`.

From a local checkout: `dsh plugin add ./dsh-extra-income`. Published on npm as [`dsh-extra-income@0.1.1`](https://www.npmjs.com/package/dsh-extra-income).

<a id="what"></a>

## What it does

The bundled `monetize` skill turns one person's career history into an honest, actionable side-income plan:

- **Hidden-skills audit** — ten skills the person under-prices, including ones they do not consider skills.
- **Opportunity scan** — realistic paths with startup cost, time to first sale, weekly hours, difficulty and monthly range, sorted by potential ÷ friction.
- **Productization** — services, diagnostics, digital products and freelance offers with priced deliverables.
- **Leverage point** — exactly one action to start this week.
- **Salary ceiling** — target roles above current compensation, the gap and the transition path.
- **AI starter pack** — five AI-leveraged services inside a realistic time and budget envelope.

Output: a report with a source appendix and an unverified-estimate appendix, plus a 30-day checklist with acceptance criteria.

Ask in natural language; no slash command is involved:

```text
分析我的变现潜力，目标每月多赚 5000
我做了 5 年会计，想搞点副业
what side hustle fits my background?
```

<a id="how"></a>

## How it works

`index.js` registers a skill provider with `ctx.skills.registerProvider`. At catalog time the provider reads `skills/monetize/SKILL.md` from the package and returns it as a bundled candidate whose resource base is the skill directory, so relative references resolve. No network calls, no dependencies, no model calls of its own.

<a id="verification"></a>

## Verification

- **Provider logic** — `npm test` registers the provider against a stub context, asserts the candidate metadata and loads the skill body.
- **Install** — installed into a DSH profile as bundle `dsh-extra-income` 0.1.0; the installer reported `application: applied` with no warnings.
- **npm** — published as `dsh-extra-income@0.1.1`; a clean install from the registry contains all 11 package files.
- **Skill catalog** — verify in a new session: a running session builds its catalog at start, so the plugin's skill appears only after reopening.

Tested against the DSH build shipped with the current DeepSeek Harness desktop app (harness packages 0.2.2-rc.3).

<a id="structure"></a>

## Structure

```
package.json          # manifest + dsh.bundle.patch
cordis.patch.yml      # inserts the plugin row into the profile
index.js              # skill provider
locale/en.json        # Plugins title / description / detail
locale/zh.json
icon.svg
docs/DETAIL.md        # longer description for the Plugins detail page
skills/monetize/      # bundled skill (copy of the source repository)
test/provider.test.mjs
```

## Limitations

- Analysis, not financial, legal or tax advice.
- Verification depends on the host agent's web search; without it every figure is labeled an estimate.

## License

MIT. The bundled skill is also MIT, from [zhengqiuyang/monetize-skill](https://github.com/zhengqiuyang/monetize-skill).
