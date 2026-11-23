# 平台架构 / Platform Architecture

DeepResValue 的**对外**架构说明。只描述用户可观测的链路、能力与边界，不含服务端实现。

> The **public** architecture of DeepResValue: observable flows, capabilities, and boundaries only — no server-side implementation.

| 语言 / Language | 文档 |
|-----------------|------|
| 中文 | [platform.zh.md](./platform.zh.md) |
| English | [platform.en.md](./platform.en.md) |

## 你会读到什么

- 五条设计取舍（为什么是云端零配置 + 可选本机执行）
- 端到端链路：端形态 → 平台服务 → 执行面 → 云端存储
- 能力层：科研领域专家、技能与工具、四大计算内核、排版引擎、数据连接器、BYOK
- 执行模型：默认云端隔离执行；桌面端本机执行为显式可选
- 数据与留存：云端存储是唯一持久化层
- **边界与不变量**：哪些事平台明确不承诺

## 你不会读到什么

服务端实现、内部模块划分、部署拓扑、第三方基础设施专名、任何密钥与凭据。这些不在公开范围，也不在本仓库讨论。

---

相关文档：[桌面端](../desktop/README.md) · [文档中心](../README.md) · [返回首页](../../README.md)
