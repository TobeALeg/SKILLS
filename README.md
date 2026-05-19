# SKILLS

个人 Codex / Claude Code skill 集合。

## Included Skills

- `trekmind-ui-style`: TrekMind 编辑感前端设计系统。用于把现有 HTML、Vue 3、NextJS、Tailwind UI 改成 TrekMind 风格，或从零构建符合这套风格的新前端。

## Claude Code

Claude Code 会识别项目里的 `.claude/skills/<skill-name>/SKILL.md`。

在这个仓库里使用 Claude Code 时，`trekmind-ui-style` 已经位于：

```text
.claude/skills/trekmind-ui-style/SKILL.md
```

如果想装成个人级 Claude Code skill，可以复制到：

```bash
mkdir -p ~/.claude/skills
cp -R .claude/skills/trekmind-ui-style ~/.claude/skills/
```

## Codex

Codex 可用的安装位置是：

```bash
mkdir -p ~/.codex/skills
cp -R .claude/skills/trekmind-ui-style ~/.codex/skills/
```

安装后重启 Codex，让新的 `$trekmind-ui-style` 生效。

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
```
