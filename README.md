# SKILLS

个人 Codex / Claude Code skill 集合。

License: MIT

## Included Skills

- `trekmind-ui-style`: TrekMind 编辑感前端设计系统。用于把现有 HTML、Vue 3、NextJS、Tailwind UI 改成 TrekMind 风格，或从零构建符合这套风格的新前端。
- `mini-app-evaluator`: 小微应用想法评估器。用于按六维权重给 Web Demo / 小微应用想法打分、排序，并判断是否值得做。
- `llm-wiki`: 从项目文件和选定的 Agent 对话中，自动维护带来源记录的项目级知识库。默认使用 DeepSeek V4.1 Flash。
- `lw`: `llm-wiki` 的显式快捷入口。在 Codex 的 slash 菜单中输入 `/lw` 使用。

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
cp -R .claude/skills/llm-wiki ~/.claude/skills/
cp -R .claude/skills/lw ~/.claude/skills/
```

## Codex

Codex 可用的安装位置是：

```bash
mkdir -p ~/.codex/skills
cp -R .claude/skills/trekmind-ui-style ~/.codex/skills/
cp -R .claude/skills/mini-app-evaluator ~/.codex/skills/
cp -R .claude/skills/llm-wiki ~/.codex/skills/
cp -R .claude/skills/lw ~/.codex/skills/
```

安装后重启 Codex，让新的 skill 生效。

### LLM Wiki 配置

```bash
export DEEPSEEK_API_KEY="..."
```

在项目目录内初始化并更新：

```bash
python ~/.codex/skills/llm-wiki/scripts/wiki.py init
python ~/.codex/skills/llm-wiki/scripts/wiki.py update --episode "本轮对话里需要长期保留的结论"
python ~/.codex/skills/llm-wiki/scripts/wiki.py context "要查询的项目知识"
```

模型默认为 `deepseek-flash`，API 地址默认为 `https://api.deepseek.com`。项目只需按需编辑 `.llm-wiki/purpose.md`；目录、页面索引和来源记录由 skill 自动管理。

安装后可以直接使用：

```text
/lw              # 初始化（如需要）并更新 Wiki
/lw init         # 只初始化
/lw status       # 查看待处理内容
/lw ask 为什么选择 SQLite
/lw scan
/lw lint
```

`lw` 关闭了自动触发，只有显式输入 `/lw` 或 `$lw` 时才会运行。

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

.claude/skills/llm-wiki/
├── SKILL.md
├── agents/openai.yaml
├── references/architecture.md
└── scripts/wiki.py

.claude/skills/lw/
├── SKILL.md
└── agents/openai.yaml
```
