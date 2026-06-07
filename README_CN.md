<div align="center">
  <h1>📚 开源文档全家桶</h1>
  <p><strong>14 个 Claude Code 技能——专业、一致、不纠结地写出开源项目所需的每一份文档。</strong></p>

  [![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
  [![Skills](https://img.shields.io/badge/Skills-14-blue.svg)](#技能列表)

  🌐 [English](README.md) | **中文**
</div>

## 🚀 快速开始

### 1. 安装
复制 `skills/` 文件夹到 `~/.claude/skills/`：
```bash
cp -r skills/* ~/.claude/skills/
```

### 2. 使用
直接告诉 Claude 你需要什么：
> "帮我写一个项目的 README"
> "创建一个安全策略"
> "帮我把这个项目上传到 GitHub"

每个技能在提到对应领域时会自动触发。

## 📋 技能列表

| # | 技能 | 产出 |
|---|-------|----------|
| 1 | `readme-writer` | README.md — 项目门面 |
| 2 | `github-upload` | 仓库初始化 + 首次推送 |
| 3 | `contributing-writer` | CONTRIBUTING.md — 贡献指南 |
| 4 | `template-writer` | Issue/PR YAML 表单模板 |
| 5 | `architecture-writer` | ARCHITECTURE.md — 系统设计 |
| 6 | `release-writer` | CHANGELOG.md — 版本发布 |
| 7 | `roadmap-writer` | ROADMAP.md — 未来规划 |
| 8 | `coc-writer` | CODE_OF_CONDUCT.md — 社区准则 |
| 9 | `security-policy-writer` | SECURITY.md — 漏洞报告 |
| 10 | `support-writer` | SUPPORT.md — 求助渠道 |
| 11 | `maintainers-writer` | MAINTAINERS.md — 维护者名单 |
| 12 | `governance-writer` | GOVERNANCE.md — 决策机制 |
| 13 | `citation-writer` | CITATION.cff — 学术引用 |
| 14 | `opensource-publish` | Weblate/Codecov/Zenodo 集成 |

## ✨ 特性

| 特性 | 说明 |
|---------|-------------|
| 🧠 **结构化工作流** | 每个技能遵循：硬门 → 问答 → 起草 → 自审 → 用户审查 |
| 🌍 **平台无关** | 适用于 GitHub、GitLab、Gitee、npm、PyPI、独立文档 |
| 🎯 **可视化选择** | 使用 AskUserQuestion 弹窗——告别纯文本 A/B/C |
| 📝 **实战模板** | 基于 Contributor Covenant、Keep a Changelog、arc42、C4、MVG |
| 🔄 **渐进式披露** | 简单项目得简单文档，复杂项目得完整深度 |

## 🏗️ 架构

```mermaid
graph LR
    A[项目起步] --> B[readme-writer + github-upload]
    B --> C[开发中]
    C --> D[release-writer]
    C --> E[contributing-writer + template-writer]
    C --> F[architecture-writer]
    E --> G[社区成长]
    G --> H[coc-writer + support-writer]
    G --> I[security-policy-writer]
    H --> J[maintainers-writer + governance-writer]
    J --> K[走向成熟]
    K --> L[roadmap-writer + citation-writer + opensource-publish]

    style B fill:#3FB950,stroke:#238636
    style D fill:#58A6FF,stroke:#1F6FEB
    style G fill:#E3B341,stroke:#9A7D1A
    style K fill:#DA3633,stroke:#B62324
```

## 📄 协议

MIT — 自由使用，自由修改，欢迎署名。

## 🙏 致谢

构建过程中参考了：
- [Contributor Covenant](https://www.contributor-covenant.org/)（行为准则模板）
- [Keep a Changelog](https://keepachangelog.com/)（更新日志格式）
- [arc42](https://arc42.org/)（架构文档）
- [C4 Model](https://c4model.com/)（架构图）
- [MVG](https://github.com/github/MVG)（最小可行治理）
- [Diátaxis](https://diataxis.fr/)（文档框架）
- [othneildrew/Best-README-Template](https://github.com/othneildrew/Best-README-Template)
