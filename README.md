# SKILLS

个人 Agent Skills 与 Agent Plugin 集合。

License: MIT

## Included Skills

- `trekmind-ui-style`: TrekMind 编辑感前端设计系统。用于把现有 HTML、Vue 3、NextJS、Tailwind UI 改成 TrekMind 风格，或从零构建符合这套风格的新前端。
- `mini-app-evaluator`: 小微应用想法评估器。用于按六维权重给 Web Demo / 小微应用想法打分、排序，并判断是否值得做。
- `LLM Wiki`：从项目文件和选定的 Agent 对话中，自动维护带来源记录的项目级知识库。技能目录名和显式短命令为 `lw`，在 Codex 的 slash 菜单中输入 `/lw` 使用。默认使用 DeepSeek V4.1 Flash。

## Repository Layout

技能源码统一位于根目录的 `skills/<skill-name>/`，每个 skill 的根部都有一个 `SKILL.md`。

## LLM Wiki MCP 服务

LLM Wiki 现在也提供标准 Agent Plugin 和本地 MCP 服务：

```text
plugins/llm-wiki/
├── plugin.json                 # Agent Plugins 1.0 portable manifest
├── mcp.json                    # portable stdio MCP configuration
├── .codex-plugin/plugin.json   # Codex compatibility manifest
├── .mcp.json                   # Codex compatibility MCP configuration
├── skills/lw/
└── llm_wiki_mcp/               # local MCP server
```

完整安装、项目白名单、本地启动和 ChatGPT Secure MCP Tunnel 接入方式见 [`plugins/llm-wiki/README.md`](plugins/llm-wiki/README.md)。

## Claude Code

如果想安装成个人级 Claude Code skill，可以复制到：

```text
~/.claude/skills/<skill-name>/
```

```bash
mkdir -p ~/.claude/skills
cp -R skills/trekmind-ui-style ~/.claude/skills/
cp -R skills/mini-app-evaluator ~/.claude/skills/
cp -R skills/lw ~/.claude/skills/
```

## Codex

Codex 和其他 Agent Skills-compatible 客户端的用户级安装位置是：

```bash
mkdir -p ~/.agents/skills
cp -R skills/trekmind-ui-style ~/.agents/skills/
cp -R skills/mini-app-evaluator ~/.agents/skills/
cp -R skills/lw ~/.agents/skills/
```

Codex 会扫描项目中的 `.agents/skills` 和用户级的 `~/.agents/skills`。安装后如果 skill 没有出现，再重启 Codex。

### LLM Wiki 配置

```bash
export DEEPSEEK_API_KEY="..."
```

在项目目录内初始化并更新：

```bash
python ~/.agents/skills/lw/scripts/wiki.py init
python ~/.agents/skills/lw/scripts/wiki.py update --episode "本轮对话里需要长期保留的结论"
python ~/.agents/skills/lw/scripts/wiki.py context "要查询的项目知识"
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

界面中显示为 `LLM Wiki`。技能注册名 `lw` 关闭了自动触发，只有显式输入 `/lw` 或 `$lw` 时才会运行。

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

skills/lw/
├── SKILL.md
├── agents/openai.yaml
├── references/architecture.md
└── scripts/wiki.py
```
