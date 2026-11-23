# Desktop Install & Upgrade (Windows)

## 1. Download

| Channel | Address |
|---------|---------|
| **Version & checksum (authoritative)** | [RELEASES.md](../../RELEASES.md) 鈥?lists versions whose Release is published, with size and SHA256 |
| GitHub Releases | <https://github.com/ZhangMochen1314/deepresvalue/releases> |
| Official website | <https://deepresvalue.com/> |

> If the Releases page does not show a version listed in `RELEASES.md` (or shows one it does not list), **treat `RELEASES.md` as authoritative**; for immediate needs, use the official website.

The file is named like `DeepResValue-<version>-setup.exe`. The current public version, size, and SHA256 are listed in [RELEASES.md](../../RELEASES.md).

> Download only from the two channels above. Mirrors operated by third parties cannot guarantee the installer was not tampered with.

## 2. Verify (recommended, 30 seconds)

In the download folder, open PowerShell:

```powershell
Get-FileHash .\DeepResValue-0.1.38-setup.exe -Algorithm SHA256
```

Compare the output character by character with the value for that version in [RELEASES.md](../../RELEASES.md). **If it does not match, do not install** 鈥?download again or switch channels.

## 3. System Requirements

| Item | Requirement |
|------|-------------|
| OS | Windows 10 (1809 or later) / Windows 11 |
| Architecture | x64 |
| Memory | 8 GB recommended (4 GB minimum) |
| Disk | ~2 GB free (installer ~517 MB; installed size is larger) |
| Network | Required; `deepresvalue.com` must be reachable |
| Privileges | Standard user (per-user install, no administrator needed) |

## 4. Install

1. Double-click the installer.
2. **SmartScreen prompt**: the installer is **not code-signed**, so Windows shows "Windows protected your PC".
   Click **More info** 鈫?**Run anyway**. This is expected, not a corrupted installer.
3. Choose the install directory (per-user by default; the path can be changed).
4. Wait for completion. The installer does **not** auto-launch the app 鈥?start it from the Start menu or the desktop shortcut.

> In environments with application allowlists or endpoint protection, the installer may need to be allowed by policy. The platform does not provide a way to bypass system security policies.

## 5. First Launch

1. Start DeepResValue.
2. Sign in with the **same account you use on the web**.
3. Choose a **workspace directory** 鈥?the default working directory for local execution and where your local files live.
   You can change it later in settings; changing it does not move existing files.
4. You land in the main UI: sessions on the left, conversation in the middle, files and artifacts on the right.

## 6. Upgrade

- In-app: **Settings 鈫?bottom of the Account page 鈫?Software Update**.
- Or download the new installer and install over the old one; the install directory is reused and workspace files are untouched.
- Upgrading does not require signing in again.

## 7. Uninstall

- Option 1: Windows **Settings 鈫?Apps 鈫?Installed apps 鈫?DeepResValue 鈫?Uninstall**.
- Option 2: `Uninstall DeepResValue.exe` in the install directory.

**What is removed and what is not**:

| Item | After uninstall |
|------|-----------------|
| Program files and bundled runtime | Removed |
| App configuration and session cache (user data) | May remain; can be cleaned manually |
| **Your workspace directory (local files)** | **Not removed** |
| Cloud sessions and artifacts | Unaffected; sign in again to see them |

## 8. Common Installation Issues

| Symptom | What to do |
|---------|------------|
| SmartScreen blocks the installer | More info 鈫?Run anyway (see section 4) |
| Antivirus flags/quarantines it | Add an exception and reinstall; if it persists, re-download from the official channel and verify SHA256 |
| Install fails halfway | Check free disk space and directory permissions; close programs using that directory and retry |
| Blank window / stuck loading after launch | Check that `deepresvalue.com` is reachable; restart the app; otherwise see [FAQ](./faq.en.md) |
| Hash mismatch | Do not install; download again |

---

Related: [Local Execution & Privacy](./local-execution.en.md) 路 [FAQ](./faq.en.md) 路 [Desktop Overview](./README.md)
