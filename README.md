# explain2me

用一则临近结尾才显露含义的寓言，解释一个研究生水平的概念。

先读故事，再揭晓概念、解释隐喻对应和类比的边界。可以指定概念、只给领域，或让技能自动选择领域与概念；默认在对话中直接输出文字。

这是一个基于 Markdown 指令的 Agent Skill 项目，采用单插件、单技能结构。

## 目录

```text
explain2me/
├── .claude-plugin/
│   └── plugin.json          # Claude Code 插件元数据
├── skills/
│   └── explain2me/
│       ├── SKILL.md         # 技能入口与解释流程
│       └── agents/
│           └── openai.yaml  # Codex 展示信息与示例提示词
├── .gitattributes           # 文本换行约定
├── .gitignore              # 忽略本地产物、凭据和编辑器文件
├── LICENSE
└── README.md
```

技能指令以 `skills/explain2me/SKILL.md` 为唯一入口。仓库目前没有运行时依赖；只有安装工具或宿主 Agent 需要各自的运行环境。

## 安装与使用

以下终端命令在 PowerShell 7 中运行。`npx` 安装方式需要 Node.js。

在仓库根目录为当前项目安装技能，按实际使用的 Agent 选择一条：

```powershell
npx skills add . --skill explain2me -a codex
npx skills add . --skill explain2me -a claude-code
```

也可以从远程仓库安装：

```powershell
npx skills add Dr-DanDan/explain2me --skill explain2me -a codex
```

远程仓库当前设为私有，需要具备访问权限，并让 Git 使用已授权的身份。

安装后，在 Agent 对话中使用：

```text
# Codex
$explain2me 自选一个研究生水平的概念，用寓言解释，临近结尾再揭晓。

# Claude Code，按独立技能安装时
/explain2me 从统计学中选择一个研究生水平的概念，用寓言解释。
```

若要按 Claude Code 插件方式本地加载，在仓库根目录运行：

```powershell
claude --plugin-dir .
```

随后在该会话中使用：

```text
/explain2me:explain2me 用寓言解释拉格朗日对偶，故事后说明每个关键隐喻的对应关系。
```

两种加载方式选择一种即可。

## 本地验证

```powershell
claude plugin validate .
git diff --check
```

修改技能后，可用上面三种请求检查自动选题、领域内选题和指定概念是否正确。重点检查：标题和开场是否保留悬念，故事末段是否体现关键机制，以及故事后的解释、隐喻映射和类比边界是否准确。结构检查通过不代表叙事效果和学术准确性已经验收。

## 结构参考

参考核对日期：2026-10-27。

- [HumanLayer show-me](https://github.com/humanlayer/skills/tree/main/plugins/show-me)：初始化时参考插件清单与 `skills/show-me/SKILL.md` 布局。
- [Anthropic 社区 ELI5](https://github.com/anthropics/claude-plugins-community/tree/main/eli5)：初始化时参考单技能插件结构。
- [Claude Code 插件规范](https://code.claude.com/docs/en/plugins-reference)与 [Skills CLI](https://github.com/vercel-labs/skills)：用于核对目录、插件清单和安装命令。

本项目的技能指令根据“先讲寓言、临近结尾才显露概念、故事后解释隐喻”的要求独立编写。

## 许可证

[MIT](LICENSE)
