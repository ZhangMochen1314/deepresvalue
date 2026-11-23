# Local Execution & Privacy (Desktop)

> In one sentence: **nothing runs on your computer by default.** Only when you explicitly choose
> "run on this machine" does the desktop client touch your environment, files, or processes — and even then
> it is bounded by three permission tiers, a workspace directory, and a cancel button.

---

## 1. Why Local Execution Exists

Cloud isolated execution covers the vast majority of tasks, but it cannot see your computer. These cases need local execution:

- Working with **local files** (without uploading them);
- Calling **software already installed** on your machine (specialized tools, internal clients);
- Using **local environment variables and credentials** (corporate intranet, already-signed-in local services);
- **Long-running local jobs** (bulk conversion, long scripts).

That is the reason the desktop client exists — and the only extra capability it adds.

---

## 2. How to Enable

1. In the conversation, choose the execution location: **this machine** (cloud is the default).
2. On first use you confirm a workspace directory — local execution can only act inside it.
3. Send the task. The task card shows location, permission tier, and elapsed time.

**There is no "silently run locally" path.** Execution location is chosen per task; a new conversation does not inherit a previous authorization.

---

## 3. Three Permission Tiers

| Tier | Can do | Cannot do | When to use |
|------|--------|-----------|-------------|
| **Read-only** | Read workspace content, inspect environment | Write files, change config, install dependencies | You want the Agent to look, not touch |
| **Workspace write** (default) | Read/write inside the workspace, run scripts, install dependencies | Paths outside the workspace | Most local tasks |
| **Full access** | Read/write outside the workspace | — | When cross-directory work is genuinely required |

Tiers apply **per task**; there is no "authorize once, forever".

---

## 4. Boundary: The Workspace

- The workspace is a directory you choose. Under the default tier, reads and writes are confined to it.
- Paths outside the workspace require the **full access** tier, explicitly selected by you.
- Changing the workspace only changes where future work happens; it does not move or delete existing files.

---

## 5. Process Hygiene

Local execution is not "fire a command into your terminal and forget it":

| Mechanism | Behavior |
|-----------|----------|
| Timeout | Each task has a deadline; it is terminated on expiry with a readable reason |
| Cancel | Cancellable at any time; cancelling terminates the **whole process tree** spawned by the task, leaving no orphans |
| Background jobs | Long tasks run as jobs with progress, output, and stop controls |
| Output capture | stdout and stderr are logged separately and remain reviewable; errors are never swallowed |
| Audit | Each local run leaves a record in the task log card (command, directory, exit code, duration) |

---

## 6. Actions That Require Explicit Confirmation

The following **never happen silently**; they require confirmation and are otherwise rejected (fail-closed):

- Creating or modifying content **outside the workspace**;
- Creating or deleting local environments (e.g. a new Python or R environment);
- Installing system-level dependencies;
- Operations needing administrator privileges (Windows UAC prompt applies).

If a confirmation channel is unavailable in your environment (for example, dialogs disabled by policy), these actions are **rejected outright** rather than allowed by default.

---

## 7. Where Data Goes

| Data | Location | Visible across devices |
|------|----------|------------------------|
| Local files in your workspace | Your computer | No (unless you upload) |
| Local execution output | Local session log + conversation record | Conversation record syncs with the account |
| Files you upload to a conversation | Cloud storage | Yes |
| Deliverables (after return) | Cloud storage | Yes |

**Key point**: local files are not platform persistence. If you switch computers or uninstall the desktop client, your workspace files stay on your machine — but the platform does not keep a copy for you.

---

## 8. Privacy Boundaries (No Overclaiming)

- **Transport is fully encrypted** (HTTPS / WSS).
- **No end-to-end encryption claim**: cloud tasks must read file contents to analyze them; local tasks do not upload file contents, but task descriptions and execution records sync to the conversation.
- **No absolute "owner-only" claim**: sharing is link-level — anyone with the link can open it.
- **Your workspace files are not uploaded**: unless you explicitly upload them, or the Agent returns an artifact as a deliverable.

---

## 9. Recommended Safe Usage

1. Create a dedicated workspace directory for the Agent; do not point it at an entire disk or your home directory.
2. Keep the default "workspace write" tier and switch to "full access" only temporarily.
3. Keep sensitive credentials in local environment variables; never paste keys into the conversation.
4. Run long tasks as background jobs so you can inspect and stop them.
5. Cancel when done — do not leave tasks running overnight.

---

Related: [Install & Upgrade](./install.en.md) · [FAQ](./faq.en.md) · [Platform Architecture](../architecture/platform.en.md)
