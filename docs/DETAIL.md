# Extra income

Bundles the `monetize` skill into the DeepSeek Harness skill catalog. Once the plugin is installed and active in a profile, the skill is available to every agent in that profile without a separate skill installation.

## What it does

`monetize` turns one person's career history into an honest, actionable side-income plan:

1. **Hidden-skills audit** — ten skills the person under-prices, including ones they do not consider skills.
2. **Opportunity scan** — realistic paths with startup cost, time to first sale, weekly hours, difficulty, and monthly range, sorted by potential ÷ friction.
3. **Productization** — services, diagnostics, digital products, and freelance offers with priced deliverables.
4. **Leverage point** — exactly one action to start this week.
5. **Salary ceiling** — target roles above current compensation, the gap, and the transition path.
6. **AI starter pack** — five AI-leveraged services inside a realistic time and budget envelope.

The output is a report with a source appendix and an unverified-estimate appendix, plus a 30-day checklist with acceptance criteria.

## Usage

Ask in natural language; the skill triggers on career and income questions:

- "分析我的变现潜力，目标每月多赚 5000"
- "我做了 5 年会计，想搞点副业"
- "what side hustle fits my background?"

## Honesty rules

- Income is a range, never a point.
- Every number is verified with a source, or labeled "estimate, unverified".
- No income promises; competition and failure modes are stated.
- No gray-area methods.

## Limitations

- The skill provides analysis, not financial, legal, or tax advice.
- It relies on the host agent's web search for verification; without search, every figure is labeled an estimate.
- Numerical output quality depends on the background the user provides; a thin background produces a skill-acquisition plan instead of ten invented opportunities.

## Source

The skill lives at https://github.com/zhengqiuyang/monetize-skill and is copied into `skills/monetize/` here so the package is self-contained.
