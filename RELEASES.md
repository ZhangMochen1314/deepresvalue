# 版本发布 / Releases

桌面端的公开版本记录。安装包托管在 [GitHub Releases](https://github.com/ZhangMochen1314/deepresvalue/releases)，
**应用内升级仍走产品自身的更新通道**——GitHub 只是手动下载镜像，不影响已安装用户的自动更新。

| 版本 | 日期 | 安装包 | 大小 | SHA256 |
|------|------|--------|------|--------|
| [0.1.38](./docs/desktop/release-notes/v0.1.38.md) | 2026-11-23 | `DeepResValue-0.1.38-setup.exe` | 541,747,616 B（约 517 MB） | `34cf4d209c30a3d8d8112fce8de4962f364cfca1bb218c68ea28c5d39c65387e` |

> 校验方式：`Get-FileHash .\DeepResValue-0.1.38-setup.exe -Algorithm SHA256`，与上表逐字比对。

---

## 0.1.38（2026-11-23）

**这次更新做了什么**：精简设置页——移除只读的「本机环境」页（对用户没有可操作价值），
把「软件更新」并入账号页；导航项由 6 项减为 5 项。其余能力不变。

- 安装/升级方式不变，工作区文件不受影响
- 已安装用户可通过 **设置 → 账号页底部「软件更新」** 升级

完整说明：[release-notes/v0.1.38.md](./docs/desktop/release-notes/v0.1.38.md)

---

## 关于签名

安装包**未做代码签名**。Windows 首次运行会显示 SmartScreen 提示（"Windows 已保护你的电脑"），
处理方式：**更多信息 → 仍要运行**。这是预期行为，不是文件损坏。

由于未签名，**SHA256 校验是判断安装包真伪的唯一手段**，请务必比对。

## 关于自动更新

- 应用内检查更新与下载走产品自身的更新通道，与 GitHub 无关。
- 从 GitHub 下载安装的用户，安装后同样走产品更新通道，无需回来手动下载。
- 本仓库不保存任何安装包二进制（只在 Releases 中挂载），因此仓库可以安全地 `git clone`。

---

返回：[首页](./README.md) · [桌面端](./docs/desktop/README.md) · [平台架构](./docs/architecture/README.md) · [文档中心](./docs/README.md)
