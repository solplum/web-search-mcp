<!-- BADGE BAR -->
[![License](https://img.shields.io/badge/license-MIT-blue)](./LICENSE)
[![Python](https://img.shields.io/badge/Python-3.10+-blue)](https://python.org)

# web-search-mcp

> **多后端联网搜索 MCP Server。** 专为 CC+DeepSeek 用户设计。支持 DuckDuckGo(免费)/Brave/Google/Bing，自动检测最优后端。让 AI 能联网、会搜索。

[English](#english)

---

## 为什么需要 web-search-mcp？

- **AI 不能联网 = 闭眼编程。** LLM 的知识有截止日期，现实世界在变化。搜索能力是所有 Agent 的基础需求。
- **不是所有后端都能用。** Google API 要钱、Bing API 要配置、Brave 要 key。DuckDuckGo 免费但快慢不一。自动检测最优后端，不让你纠结选哪个。
- **DeepSeek 用户没有内置搜索。** Claude 有 web_search tool，但用 DeepSeek 的时候呢？这是弥补基础设施缺口。

## 核心能力

- 🌐 **多后端支持** — DuckDuckGo / Brave / Google / Bing，一键切换
- 🔍 **自动后端检测** — 按可用性 + 速度自动选最优，不让你手动试
- 📄 **结构化结果** — 标题 + URL + 摘要，不是一整段乱码
- 🐍 **Python MCP Server** — 标准 MCP 协议，任何支持 MCP 的 Agent 都能用

## 快速开始

### 安装

```bash
pip install web-search-mcp
# 或
git clone git@github.com:solplum/web-search-mcp.git
```

### 配置

在 Claude Code 的 `.mcp.json` 中添加：

```json
{
  "mcpServers": {
    "web-search": {
      "command": "python",
      "args": ["-m", "web_search_mcp"]
    }
  }
}
```

## 设计哲学

**免费优先，但不排斥付费。** 默认走 DuckDuckGo（免费 + 无需 API key），降低使用门槛。但如果用户配了 Brave/Google key，自动切过去——更好的质量不该被"免费优先"挡住。

**后端是细节，用户不该关心。** 自动检测最优后端的意义在于：用户不需要知道今天哪个搜索引擎更快。这是基础设施的基本素养——把复杂性藏在自己身后。

## 相关项目

| 项目 | 关系 |
|------|------|
| [skill-bootstrapper](https://github.com/solplum/skill-bootstrapper) | 下游 — 搜索市场上已有 Skill |
| 所有 Skill 生态项目 | 下游 — 为所有需要联网的 Skill 提供搜索能力 |

## License

MIT

---

## English

# web-search-mcp

> **Multi-backend web search MCP Server.** DuckDuckGo, Brave, Google, Bing — auto-detects the best available backend. Gives AI agents the ability to search the web.

### Why?

AI without web access codes blind. LLM knowledge has a cutoff date. This MCP server fills the infrastructure gap — especially for DeepSeek users who don't have built-in search.

### Design Philosophy

**Free-first, not free-only.** Default to DuckDuckGo (free, no API key) to lower the barrier. But if the user configures Brave/Google, auto-switch — better quality shouldn't be blocked by "free-first."

**Backends are details. Users shouldn't care.** Auto-detection means the user never needs to know which search engine is faster today. Hide the complexity.
