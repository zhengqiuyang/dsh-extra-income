# dsh-extra-income

DeepSeek Harness plugin that bundles the [`monetize`](https://github.com/zhengqiuyang/monetize-skill) skill: turn a career history into an honest, actionable side-income plan.

Installing the plugin puts the skill into the profile's skill catalog, so every agent in that profile can use it — no separate skill installation.

## Install

```bash
# From a local checkout (recommended while unreleased)
dsh plugin add ./dsh-extra-income
```

Or in the Web UI: **Plugins** → **Add plugin** → select the package directory.

## What it adds

- The `monetize` skill (hidden-skills audit, opportunity scan, productization, leverage point, salary ceiling, AI starter pack).
- A Plugins entry with its own title, description, detail page and icon.

## How it works

`index.js` registers a skill provider with `ctx.skills.registerProvider`. The provider reads `skills/monetize/SKILL.md` at catalog time and returns it as a bundled candidate, with the skill directory as the resource base so relative references resolve.

## Structure

```
package.json          # manifest + dsh.bundle.patch
cordis.patch.yml      # inserts the plugin row into the profile
index.js              # skill provider
locale/en.json        # Plugins title / description / detail
locale/zh.json
icon.svg
docs/DETAIL.md
skills/monetize/      # bundled skill (copy of the source repository)
```

## Verification status

- **Provider logic** — covered by `npm test` (`test/provider.test.mjs`): registers the provider against a stub context, asserts the candidate metadata, and loads the skill body.
- **Install** — installed into a DSH profile as bundle `dsh-extra-income` 0.1.0; the installer reported `application: applied` with no warnings.
- **Skill catalog** — must be confirmed in a new session: a running session builds its skill catalog at start, so the plugin's skill appears only after reopening.

```bash
npm test
```

## License

MIT
