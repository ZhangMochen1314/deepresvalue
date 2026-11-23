# Desktop FAQ

## Installation

**Q: Windows shows "Windows protected your PC" when I run the installer. Is it broken?**
A: No. The installer is **not code-signed**, so SmartScreen blocks it by default. Click **More info → Run anyway**.
If you would rather verify first, compare the SHA256 as described in the [install guide](./install.en.md).

**Q: My antivirus quarantined the installer.**
A: Add an exception and reinstall. If it keeps getting quarantined, re-download from the official channel and verify the SHA256; if the hash matches and it is still blocked, the cause is your local security policy — the platform does not provide ways to bypass it.

**Q: Do I need administrator rights?**
A: No. The default install is per-user. Only a few local tasks (installing system-level dependencies) trigger UAC.

**Q: How large is the installer?**
A: About 517 MB for the current version (bundled runtime included); allow roughly 2 GB of free disk after installation.

**Q: Is macOS / Linux supported?**
A: The current public release is Windows x64 only. On other platforms, use the web or mini-program surface.

---

## Launch and Sign-in

**Q: Blank window or endless spinner after launch.**
A: Check in order: (1) can you open `deepresvalue.com` in a browser; (2) disable proxy software and retry; (3) quit and relaunch the app; (4) reboot.
If it persists, send the log files from the app directory to support.

**Q: Sign-in fails.**
A: Desktop shares the same account as the web. Confirm you can sign in through a browser first; if the browser works and desktop does not, the cause is usually local network or proxy policy.

**Q: Can I open multiple windows or instances?**
A: Only one instance runs per user-data directory; launching again focuses the existing window. This prevents two instances from fighting over the same workspace.

---

## Usage

**Q: What is the difference between desktop and web?**
A: UI and features share one source. Only two differences: (1) native window experience (notifications, multitasking); (2) the optional **local execution** capability.
If you do not need local execution, the web is enough.

**Q: Does it run anything on my computer by default?**
A: No. Execution location is chosen per task, and the default is cloud. See [Local Execution & Privacy](./local-execution.en.md).

**Q: Will the Agent read my whole disk?**
A: No. The default tier confines reads and writes to the workspace you chose; paths outside it require the full-access tier that you select explicitly.

**Q: I picked the wrong workspace / want to change it.**
A: Change it in settings. It only changes where future work happens; existing files are not moved or deleted.

**Q: Are locally processed files uploaded?**
A: Not automatically. Only when you upload them, or when the Agent returns an artifact as a deliverable.

**Q: Does it work offline?**
A: No. Platform capability depends on cloud services; offline you can only view already-cached local content.

**Q: Can I leave long tasks running?**
A: Yes. Long tasks run as jobs with progress, output, and stop controls; closing the window does not automatically kill background jobs.

---

## Upgrade and Uninstall

**Q: How do I upgrade?**
A: Settings → bottom of the Account page → Software Update; or download the new installer and install over the old one. Upgrading requires no re-login and does not affect workspace files.

**Q: The upgrade failed.**
A: Fully quit the app and retry; if it still fails, download the latest installer manually and install over. Sessions and workspace files are unaffected.

**Q: Will uninstalling delete my files?**
A: Not your workspace files. Uninstall removes program files and the bundled runtime; the user-data directory may remain and can be cleaned manually.
Cloud sessions and artifacts are unaffected — sign in again to see them.

**Q: Any leftovers after uninstall?**
A: Possibly: the user-data directory (config and session cache) and your own workspace files. The former can be deleted manually; the latter is your data and the platform will not delete it for you.

---

## Data and Privacy

**Q: Can the platform see my local files?**
A: It cannot reach anything outside your workspace, and reads/writes inside it depend on the tier you grant. Commands and output of local runs are recorded in the conversation log.

**Q: Are share links safe?**
A: Sharing is **link-level**: anyone with the link can access it. Do not share links to sensitive material.

**Q: Where are sessions and artifacts stored?**
A: Cloud storage, synced with your account. Local files in your workspace are not persistence.

---

**Still stuck?** Search the [documentation hub](../README.md) first; if that does not help, contact us through the official website with: version, Windows version, reproduction steps, and log files.
