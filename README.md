# SKILLS

个人 Agent Skills 集合。

License: MIT

## Included Skills

- `trekmind-ui-style`: TrekMind 编辑感前端设计系统。用于把现有 HTML、Vue 3、NextJS、Tailwind UI 改成 TrekMind 风格，或从零构建符合这套风格的新前端。
- `mini-app-evaluator`: 小微应用想法评估器。用于按六维权重给 Web Demo / 小微应用想法打分、排序，并判断是否值得做。

## Repository Layout

技能源码统一位于根目录的 `skills/<skill-name>/`，每个 skill 的根部都有一个 `SKILL.md`。

## Claude Code

如果想安装成个人级 Claude Code skill，可以复制到：

```text
~/.claude/skills/<skill-name>/
```

```bash
mkdir -p ~/.claude/skills
cp -R skills/trekmind-ui-style ~/.claude/skills/
cp -R skills/mini-app-evaluator ~/.claude/skills/
```

## Codex

Codex 和其他 Agent Skills-compatible 客户端的用户级安装位置是：

```bash
mkdir -p ~/.agents/skills
cp -R skills/trekmind-ui-style ~/.agents/skills/
cp -R skills/mini-app-evaluator ~/.agents/skills/
```

Codex 会扫描项目中的 `.agents/skills` 和用户级的 `~/.agents/skills`。安装后如果 skill 没有出现，再重启 Codex。

## Skill Layout

```text
skills/trekmind-ui-style/
├── SKILL.md
├── agents/openai.yaml
├── references/
│   ├── style-rules.md
│   └── framework-adapters.md
└── assets/
    ├── trekmind-base.css
    └── design-system-preview.html

skills/mini-app-evaluator/
├── SKILL.md
├── agents/openai.yaml
└── references/
    └── evaluation-rubric.md
```
