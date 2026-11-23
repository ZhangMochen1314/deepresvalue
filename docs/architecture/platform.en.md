# Platform Architecture (Public View)

> This section describes only the **externally observable** architecture and boundaries of DeepResValue:
> what a user sees, where data flows, and how capabilities are scheduled.
> Server-side implementation is out of scope, and nothing here discloses internal design.

---

## 1. At a Glance: Five Design Trade-offs

| # | Trade-off | What it means for you |
|---|-----------|-----------------------|
| 1 | **Cloud-first, zero configuration** — the compute environment is not installed on your machine | Open a browser and start; phone, tablet, and desktop share the same capability |
| 2 | **One account, one dataset** — devices are entrances, not data silos | Switch devices without migration; sessions and artifacts follow the account |
| 3 | **Capability packaged by domain** — research experts bundle methods and tools | Describe the task; you do not assemble the toolchain yourself |
| 4 | **Traceable by design** — reasoning, code, execution, and artifacts are recorded step by step | A conclusion can be traced back to the exact code that produced a table |
| 5 | **Local execution is optional enhancement** — only after you explicitly opt in | Your machine is untouched by default; you grant access when needed |

---

## 2. End-to-End Path

```
 User
  │  one-sentence task (Chinese / English)
  ▼
┌──────────────────────────────────────────────────────┐
│ Surface layer   Web ／ Desktop ／ Mini-program         │
│                 (same account, same data, same UX)    │
└──────────────────────────────────────────────────────┘
  │
  ▼
┌──────────────────────────────────────────────────────┐
│ Platform service layer                                │
│   session orchestration · expert & skill scheduling   │
│   credit metering · file & artifact management        │
└──────────────────────────────────────────────────────┘
  │                                   │
  ▼                                   ▼
┌───────────────────────────┐   ┌──────────────────────┐
│ Isolated execution (default)│  │ Your own computer    │
│ allocated per task,         │  │ (optional)           │
│ reclaimed on completion     │  │ enabled only when    │
│ four kernels · typesetting  │  │ you explicitly opt in│
└───────────────────────────┘   └──────────────────────┘
  │                                   │
  └───────────────┬───────────────────┘
                  ▼
        ┌───────────────────────┐
        │ Cloud storage          │
        │ (the only persistence) │
        │ uploads · intermediates│
        │ · deliverables         │
        └───────────────────────┘
```

Three invariants:

1. **The execution surface is ephemeral** — environments are allocated per task and reclaimed when it ends.
2. **Persistence lives in exactly one place** — deliverables must return to cloud storage before other devices can see them.
3. **Local execution never happens by default** — the desktop client touches local files and environments only after the user explicitly chooses to run locally.

---

## 3. Surface Layer

| Surface | Form | Main role | Relationship to others |
|---------|------|-----------|------------------------|
| Web | Browser application | Full-featured primary entrance | Baseline |
| Desktop | Native client built on Chromium | Native window experience + optional **local execution** | Reuses the same web implementation, adds local capability |
| Mini-program | Lightweight entrance | Quick use on mobile | Reuses the web implementation, keeping only platform-mandated differences |

**Consistency principle**: the three surfaces are one product, not three implementations. UI, flows, and data model share a single source; differences come from *what a surface can do*, not from *how it is built*.

---

## 4. Capability Layer

### 4.1 Research Experts

129 domain experts. Each expert = **domain method + professional workflow + tool bundle**. After a task arrives, the platform matches a domain expert who guides execution.

### 4.2 Skills and Tools

- **System skills**: injected automatically by the platform, covering general research flows (search, analysis, writing, typesetting, reproducibility).
- **Custom / third-party skills**: installable and composable by users.
- **Tools**: the executable actions available to cloud tasks; the desktop client has a separate **local toolset**.

### 4.3 Compute Kernels

| Kernel | Use cases |
|--------|-----------|
| Python 3 | Data analysis, machine learning, NLP, visualization |
| R | Statistical modeling, econometrics, bioinformatics |
| MATLAB-compatible (Octave) | Signal processing, control systems, numerical computing |
| SPICE (ngspice) | Circuit simulation, analog/digital design verification |

### 4.4 Typesetting

- **Word**: institution-template report generation
- **LaTeX**: papers, equations, bibliography management

### 4.5 Data Connectors (MCP)

External data sources and tools are integrated over the MCP protocol, and the list keeps growing. Users enable connectors on demand and supply their own credentials.

### 4.6 BYOK (Bring Your Own Key)

Users may connect their own model service (OpenAI-compatible protocol). Billing between the user and the model provider stays between them.

---

## 5. Execution Model

### 5.1 Two Execution Paths

| Path | Trigger | Runs on | Typical scenarios |
|------|---------|---------|-------------------|
| **Cloud isolated execution** (default) | Default, no setup | A per-task isolated environment | Most analysis, computation, typesetting |
| **Local execution** (optional) | User explicitly opts in on the desktop client | The user's own computer | Tasks needing local files, local software, local environment variables, or intranet resources |

### 5.2 Task Lifecycle

```
accept task → match expert → plan steps → execute step by step
           → record every step (traceable) → return artifacts to cloud → reclaim environment
```

### 5.3 Failure and Degradation

- **Timeout**: each step has a deadline; on expiry the user gets a readable reason instead of an endless wait.
- **Cancel**: available at any time; cancelling terminates the whole process tree spawned by that task.
- **Visible failure**: failed steps carry raw output; there is no "silent success".
- **Degradation**: when a connector is unavailable, the task either continues or stops with an explicit message — the user decides.

---

## 6. Data and Retention

| Data | Location | Notes |
|------|----------|-------|
| Uploaded files | Cloud storage | Managed per session, visible across devices |
| Execution intermediates | Cloud storage | Still traceable after the task ends |
| Deliverables | Cloud storage | The only persistence layer; export to download |
| Desktop local files | Your computer | **Not persistence**; invisible to other devices unless returned |
| Account and session metadata | Platform database | Isolated per account |

**Access model**: data is isolated per account; sharing is link-level, so anyone holding the link can open it — do not share links to sensitive material.

**Retention**: files and artifacts are retained per product policy; users can export or delete them at any time.

---

## 7. Billing and Quota

- The unit is **credits**, consumed per task (complexity, execution time, model usage).
- New users receive a free quota on signup; top up when it runs out.
- Invite rewards have no cap.
- Under BYOK, model-side costs are settled directly between the user and the model provider.

---

## 8. Boundaries and Invariants

Stating what we do **not** do matters more than listing features:

1. **No end-to-end encryption claim**: transport is encrypted end to end; the platform must read file contents to analyze them.
2. **No offline full-function claim**: platform capability depends on cloud services; it is unavailable offline.
3. **Server-side implementation is not published**: this document and this repository describe the external architecture only.
4. **Local execution requires explicit authorization**: there is no path that silently runs on a user's computer.
5. **Cloud is the source of truth for artifacts**: a file that exists only on your machine is not a saved deliverable.
6. **Sharing is link-level**: anyone with the link can open it; the platform does not promise "owner-only" access.

---

## 9. Glossary (External Term → Meaning)

| Term | Meaning |
|------|---------|
| Isolated execution environment | A compute environment allocated per task and reclaimed afterward |
| Cloud storage | The platform's persistence layer |
| Surface | Web / desktop / mini-program entrance |
| Local execution | Running tasks natively on the user's own computer |
| Device channel | Long-lived connection between desktop and platform for dispatching tasks and returning results |
| Research expert | A bundle of domain method + workflow + tools |
| Skill | Reusable task knowledge and operating conventions |
| Connector | An external data source or tool integrated over MCP |
