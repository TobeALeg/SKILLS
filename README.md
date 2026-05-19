# SKILLS

个人 Codex / Claude Code skill 集合。

License: MIT

## Included Skills

- `trekmind-ui-style`: TrekMind 编辑感前端设计系统。用于把现有 HTML、Vue 3、NextJS、Tailwind UI 改成 TrekMind 风格，或从零构建符合这套风格的新前端。
- `mini-app-evaluator`: 小微应用想法评估器。用于按六维权重给 Web Demo / 小微应用想法打分、排序，并判断是否值得做。

## Claude Code

Claude Code 会识别项目里的 `.claude/skills/<skill-name>/SKILL.md`。

在这个仓库里使用 Claude Code 时，skills 已经位于：

```text
.claude/skills/trekmind-ui-style/SKILL.md
.claude/skills/mini-app-evaluator/SKILL.md
```

如果想装成个人级 Claude Code skill，可以复制到：

```bash
mkdir -p ~/.claude/skills
cp -R .claude/skills/trekmind-ui-style ~/.claude/skills/
cp -R .claude/skills/mini-app-evaluator ~/.claude/skills/
```

## Codex

Codex 可用的安装位置是：

```bash
mkdir -p ~/.codex/skills
cp -R .claude/skills/trekmind-ui-style ~/.codex/skills/
cp -R .claude/skills/mini-app-evaluator ~/.codex/skills/
```

安装后重启 Codex，让新的 `$trekmind-ui-style` / `$mini-app-evaluator` 生效。

## Skill Layout

```text
.claude/skills/trekmind-ui-style/
├── SKILL.md
├── agents/openai.yaml
├── references/
│   ├── style-rules.md
│   └── framework-adapters.md
└── assets/
    ├── trekmind-base.css
    └── design-system-preview.html

.claude/skills/mini-app-evaluator/
├── SKILL.md
├── agents/openai.yaml
└── references/
    └── evaluation-rubric.md
```
