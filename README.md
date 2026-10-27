# explain2me

用简明文字、直观图解和生活类比，解释概念、代码流程与方案差异。

这是一个基于 Markdown 指令的 Agent Skill 项目，采用单插件、单技能结构。初版根据问题选择伪代码、结构树、Mermaid、对比表或独立 HTML 页面；HTML 产物默认写入 `output/`。

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
$explain2me 用一个生活中的例子和流程图解释缓存命中与失效。

# Claude Code，按独立技能安装时
/explain2me 用调用树解释当前项目的请求处理流程。
```

若要按 Claude Code 插件方式本地加载，在仓库根目录运行：

```powershell
claude --plugin-dir .
```

随后在该会话中使用：

```text
/explain2me:explain2me 用图解比较同步和异步执行。
```

两种加载方式选择一种即可。

## 本地验证

```powershell
claude plugin validate .
git diff --check
```

修改技能后，可用上面的概念解释、代码流程和方案比较三个请求试用，检查图文是否一致；生成 HTML 时再检查桌面与窄屏布局。结构检查通过不代表解释效果已经验收。

## 结构参考

参考核对日期：2026-10-27。

- [HumanLayer show-me](https://github.com/humanlayer/skills/tree/main/plugins/show-me)：参考插件清单与 `skills/show-me/SKILL.md` 布局，以及按问题选择图示的方式。
- [Anthropic 社区 ELI5](https://github.com/anthropics/claude-plugins-community/tree/main/eli5)：参考单技能插件结构，以及以图为主的入门解释思路。
- [Claude Code 插件规范](https://code.claude.com/docs/en/plugins-reference)与 [Skills CLI](https://github.com/vercel-labs/skills)：用于核对目录、插件清单和安装命令。

本项目的技能指令独立编写，仓库按单插件组织，后续有具体需要时再增加脚本、模板或参考资料。

## 许可证

[MIT](LICENSE)
