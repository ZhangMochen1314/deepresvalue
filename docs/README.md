# DeepResValue 深度研值 — 文档中心

> **让科研回归本质，让工具服务于思想，让创造不被重复所困。**

欢迎查阅 DeepResValue（深度研值）的开源用户文档。本仓库包含产品介绍、完整用户指南、分册帮助中心文档，以及**桌面端使用文档**与**对外平台架构说明**，涵盖平台所有核心功能的使用说明与可观测架构边界。

---

## 文档目录

### 📖 产品介绍

| 语言 | 文件 | 说明 |
|------|------|------|
| 🇨🇳 中文 | [product-intro.zh.md](./product-intro.zh.md) | 产品定位、核心能力、学科场景、验证里程碑 |
| 🇬🇧 English | [product-intro.en.md](./product-intro.en.md) | Product positioning, core capabilities, discipline scenarios, milestones |

### 📘 用户指南

| 语言 | 文件 | 说明 |
|------|------|------|
| 🇨🇳 中文 | [user-guide.zh.md](./user-guide.zh.md) | 完整使用指南（快速开始/界面/核心功能/文件专家/溯源/对话管理/积分/FAQ/扩展能力） |
| 🇬🇧 English | [user-guide.en.md](./user-guide.en.md) | Complete user guide (Quick Start / Interface / Core Features / Files & Experts / Traceability / Conversation / Credits / FAQ / Extensions) |

### 🖥️ 桌面端与架构

| 分类 | 中文 | English |
|------|------|---------|
| **桌面端** | [总览](./desktop/README.md) · [安装与升级](./desktop/install.zh.md) · [本地执行与隐私](./desktop/local-execution.zh.md) · [常见问题](./desktop/faq.zh.md) | [Overview](./desktop/README.md) · [Install](./desktop/install.en.md) · [Local execution & privacy](./desktop/local-execution.en.md) · [FAQ](./desktop/faq.en.md) |
| **平台架构** | [架构总览](./architecture/README.md) · [平台架构（对外）](./architecture/platform.zh.md) | [Architecture](./architecture/README.md) · [Platform architecture (public)](./architecture/platform.en.md) |
| **版本发布** | [RELEASES.md](../RELEASES.md)（版本 / 大小 / SHA256） | [RELEASES.md](../RELEASES.md) (version / size / SHA256) |

> 架构文档只描述**对外可观测**的链路与边界；服务端实现、部署拓扑与基础设施标识不在公开范围。

### 📋 帮助中心（分册）

按功能模块拆分的详细文档，双语页面共存于同一目录（`<页>.<lang>.md`），适合按需查阅。

| 分类 | 中文 | English |
|------|------|---------|
| **快速开始** | [入门](./getting-started/index.zh.md) · [快速开始](./getting-started/quick-start.zh.md) · [界面概览](./getting-started/interface-overview.zh.md) | [Welcome](./getting-started/index.en.md) · [Quick Start](./getting-started/quick-start.en.md) · [Interface](./getting-started/interface-overview.en.md) |
| **核心功能** | [数据分析](./features/data-analysis.zh.md) · [数据源](./features/data-sources.zh.md) · [文献综述](./features/literature-review.zh.md) · [学术写作](./features/academic-writing.zh.md) · [降 AIGC](./features/aigc-detection.zh.md) · [排版](./features/typesetting.zh.md) · [文件上传](./features/file-upload.zh.md) · [专家](./features/skills.zh.md) · [溯源](./features/reproducibility.zh.md) · [竞赛](./features/competition-modeling.zh.md) | [Analysis](./features/data-analysis.en.md) · [Sources](./features/data-sources.en.md) · [Literature](./features/literature-review.en.md) · [Writing](./features/academic-writing.en.md) · [AIGC](./features/aigc-detection.en.md) · [Typesetting](./features/typesetting.en.md) · [Upload](./features/file-upload.en.md) · [Experts](./features/skills.en.md) · [Traceability](./features/reproducibility.en.md) · [Competition](./features/competition-modeling.en.md) |
| **使用模式** | [导师](./modes/mentor.zh.md) · [学术](./modes/academic.zh.md) · [专业](./modes/professional.zh.md) | [Mentor](./modes/mentor.en.md) · [Academic](./modes/academic.en.md) · [Professional](./modes/professional.en.md) |
| **账户相关** | [积分](./account/credits.zh.md) · [邀请](./account/invites.zh.md) · [设置](./account/settings.zh.md) · [大使](./account/ambassador.zh.md) | [Credits](./account/credits.en.md) · [Invites](./account/invites.en.md) · [Settings](./account/settings.en.md) · [Ambassador](./account/ambassador.en.md) |
| **常见问题** | [FAQ](./faq/index.zh.md) | [FAQ](./faq/index.en.md) |

---

## 文档结构图

```
docs/
├── README.md                              ← 本文件（文档索引）
├── product-intro.{zh,en}.md               ← 产品介绍
├── user-guide.{zh,en}.md                  ← 用户指南（完整版）
├── desktop/                               ← 桌面端
│   ├── README.md                          ← 桌面端总览
│   ├── install.{zh,en}.md                 ← 安装与升级
│   ├── local-execution.{zh,en}.md         ← 本地执行与隐私
│   ├── faq.{zh,en}.md                     ← 常见问题
│   └── release-notes/                     ← 版本发布说明
├── architecture/                          ← 对外平台架构
│   ├── README.md
│   └── platform.{zh,en}.md
├── getting-started/                       ← 快速开始
│   ├── README.md                          ← 分册索引
│   ├── index.{zh,en}.md
│   ├── quick-start.{zh,en}.md
│   └── interface-overview.{zh,en}.md
├── features/                              ← 核心功能
│   ├── README.md
│   ├── data-analysis.{zh,en}.md
│   ├── data-sources.{zh,en}.md
│   ├── literature-review.{zh,en}.md
│   ├── academic-writing.{zh,en}.md
│   ├── aigc-detection.{zh,en}.md
│   ├── typesetting.{zh,en}.md
│   ├── file-upload.{zh,en}.md
│   ├── skills.{zh,en}.md
│   ├── reproducibility.{zh,en}.md
│   └── competition-modeling.{zh,en}.md
├── modes/                                 ← 使用模式
│   ├── README.md
│   ├── mentor.{zh,en}.md
│   ├── academic.{zh,en}.md
│   └── professional.{zh,en}.md
├── account/                               ← 账户相关
│   ├── README.md
│   ├── credits.{zh,en}.md
│   ├── invites.{zh,en}.md
│   ├── settings.{zh,en}.md
│   └── ambassador.{zh,en}.md
└── faq/                                   ← 常见问题
    ├── README.md
    └── index.{zh,en}.md
```

> 仓库根目录另有 `RELEASES.md`：版本索引、安装包大小与 SHA256。

---

## 关于 DeepResValue

**DeepResValue（深度研值）** 是面向全学科科研工作者的 AI 科研助手，基于先进的大语言模型构建。

- 🌐 官方网站：[https://deepresvalue.com/](https://deepresvalue.com/)
