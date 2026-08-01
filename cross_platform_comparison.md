# Cross-Platform Custom Instructions Parity & Differentiation Matrix (v3+)

| Feature | Gemini Flash | Grok | Antigravity 2 |
|:---|:---:|:---:|:---:|
| Header structure | Context Table | MoE Routing Matrix | Hybrid Matrix |
| Default V | V=2 | V=3 | V=2 |
| Keywords threshold | V≥4 | V≥4 | V≥4 |
| Dual stamps | ✅ | ✅ | ✅ |
| /debate command | ❌ | ✅ GROK-ONLY | ❌ |
| /compare command | ❌ | ✅ GROK-ONLY | ❌ |
| /optimize command | ❌ | ✅ GROK-ONLY | ❌ |
| /links command | ❌ | ✅ GROK-ONLY | ❌ |
| /plan command | ❌ | ❌ | ✅ AGY2-ONLY |
| MoE 5-step protocol | ❌ | ✅ | ❌ (hybrid) |
| MoE activation line | ❌ | ✅ | ❌ |
| Agentic tool rules | ❌ | ❌ | ✅ AGY2-ONLY |
| Planning gate | ❌ | ❌ | ✅ AGY2-ONLY |
| Destructive action guard | ❌ | ❌ | ✅ AGY2-ONLY |
| Hyperlink protocol | Conditional | Full Google Search | ❌ (use grep/gopls) |
| Expansion Layer | ✅ | ✅ (richer) | ✅ (tool-scoped) |
| /status command | ✅ | ✅ | ✅ |
| /pdf command | ✅ | ✅ | ✅ |
| RISEN on /review | ✅ | ✅ | ✅ |
| Ambiguity gate | ✅ | ✅ | ✅ |
| No-filler constraint | ✅ | ✅ | ✅ |

---

## Architectural & Feature Parity Detailed Notes

### 1. Key Architectural Differences Between Platforms

- **Gemini Web (Flash)**:
  - **Environment & Runtime**: Web-based conversational chatbot interface backed by Gemini Flash models, optimized for high throughput, minimal latency, and broad consumer accessibility.
  - **Interaction Model**: Standard single-turn or multi-turn conversational loop without direct local filesystem or IDE integration. Tooling is restricted to inline search/browsing and document export (e.g., PDF or Google Docs generation).
  - **Prompt Execution & Header**: Uses a streamlined **Context Table** header. Operates with a default verbosity of **V=2** (concise) to balance token efficiency with response depth.
  - **Extension & Integration**: Supports conditional hyperlink protocols and standard expansion layers for document export and search result formatting.

- **Grok Heavy (MoE)**:
  - **Environment & Runtime**: Multi-agent Mixture-of-Experts (MoE) architecture running on xAI infrastructure, dynamically routing prompt tokens to domain-specialized expert sub-networks.
  - **Interaction Model**: Analytical engine capable of deep multi-perspective debate, comparative syntheses, algorithmic optimization, and live external web integration via Google Search tool calls.
  - **Prompt Execution & Header**: Requires an **MoE Routing Matrix** header and an explicit **MoE Activation Line** (`[MoE Routing: Active | Experts: Domain Specialist, Auditor, Synthesis Engine]`) to activate sparse routing layers. Operates with a default verbosity of **V=3** (detailed) to accommodate multi-expert synthesis.
  - **Extension & Integration**: Supports dedicated analytical slash commands (`/debate`, `/compare`, `/optimize`, `/links`) and richer expansion layers.

- **Gemini Antigravity 2 IDE (AGY2)**:
  - **Environment & Runtime**: Local IDE-integrated agentic development framework operating directly within a local workspace filesystem and terminal execution environment. Executes actions via tool calls (e.g., `run_command`, `replace_file_content`, `view_file`, `gopls-mcp-server`, `github-mcp-server`).
  - **Interaction Model**: Autonomous agentic execution model governed by safety protocols, planning gates, and tool-scoped boundaries. Works directly on user repositories and codebases.
  - **Prompt Execution & Header**: Utilizes a **Hybrid Matrix** header combining conversational context with tool execution metadata. Operates with a default verbosity of **V=2** to keep code edits concise and actionable.
  - **Extension & Integration**: Features dedicated agentic commands (`/plan`), strict planning gates before mutating codebase state, destructive action guards (protecting critical files and commands), and deterministic local symbol lookup (`grep`/`gopls`) instead of external web hyperlinking.

---

### 2. Rationale for GROK-ONLY Features

- **`/debate` Command**:
  - *Rationale*: Grok's MoE architecture natively supports routing sub-queries to opposing expert models (e.g., Proponent vs. Opponent vs. Neutral Auditor) within a single turn. The `/debate` command triggers this multi-perspective synthesis, which is unavailable in standard single-model inference loops.
- **`/compare` Command**:
  - *Rationale*: Designed to perform multi-vector trade-off analysis across competing technologies, frameworks, or architectural designs. Grok's high context capacity and MoE expert specialization make it uniquely equipped for generating structured side-by-side comparative matrices.
- **`/optimize` Command**:
  - *Rationale*: Leverages Grok's MoE performance-tuning sub-networks to perform algorithmic complexity, memory footprint, and concurrency optimization with estimated before/after benchmarks.
- **`/links` Command**:
  - *Rationale*: Grok features full live web integration via Google Search tool calls. The `/links` command instructs Grok to compile, validate, and summarize authoritative external references, official documentation, and live web sources.
- **MoE 5-Step Protocol & MoE Activation Line**:
  - *Rationale*: Grok requires explicit system instruction to trigger its multi-expert routing layers (Identify Experts -> Route Sub-Tasks -> Evaluate Discrepancies -> Synthesize Output -> Audit). Without the MoE Activation Line, the model defaults to standard dense inference.
- **Default Verbosity `V=3`**:
  - *Rationale*: MoE multi-expert synthesis requires sufficient output budget to display expert reasoning, trade-off analysis, and synthesized recommendations. Setting default verbosity to `V=3` prevents clipping of detailed technical breakdowns.

---

### 3. Rationale for AGY2-ONLY Features

- **`/plan` Command & Planning Gate**:
  - *Rationale*: Agentic IDE execution in Antigravity 2 carries high risk of unintended mutations across project files. The `/plan` command and Planning Gate enforce a strict two-stage process: the agent must construct, analyze, and present an actionable modification plan before executing any file modifications or terminal commands.
- **Agentic Tool Rules**:
  - *Rationale*: AGY2 agents interact with the operating system and workspace via tool calls (`write_to_file`, `replace_file_content`, `run_command`). Agentic tool rules enforce strict usage invariants (e.g., re-reading files before editing, minimal diff edits, no full-file overwrites for small edits, and mandatory post-edit linting and testing).
- **Destructive Action Guard**:
  - *Rationale*: Prevents automated destruction of user data, git history, or environment configurations. Restricts unprompted execution of `rm -rf`, force pushes, overwriting uncommitted git changes, or running unauthorized privilege-escalation scripts.
- **Local Symbol & Code Navigation (Grep / Gopls / `file://` references)**:
  - *Rationale*: AGY2 operates under strict local workspace boundaries and isolated developer network modes (`CODE_ONLY`). Web searches and external hyperlinking are disabled or restricted in favor of deterministic local symbol navigation using `grep_search`, `go_symbol_references`, `find_by_name`, and absolute file paths (`file://`).

---

### 4. Summary of Shared Cross-Platform Foundations

Despite platform-specific differentiation, all custom instructions (v3+) share a common core foundation to ensure predictable behavior, formatting consistency, and quality guarantees across all AI environments:

1. **Dual Stamps**: Every output begins and ends with an exact timestamped Request ID block (`[YYYY-MM-DD HH:MM AM/PM - REQ-YYYYDDD-HHMMSS - <Suggested Document Name>]`), ensuring auditability and output boundary integrity.
2. **Standardized Verbosity Ladder (V=0 to V=5)**: Provides explicit granular control over output length and depth across all platforms:
   - `V=0`: Single word or one-line answer only.
   - `V=1`: Terse (bullet points / single sentences).
   - `V=2`: Concise essential details (default for Gemini Web & AGY2).
   - `V=3`: Detailed comprehensive breakdown (default for Grok).
   - `V=4`: Comprehensive (highly detailed with full examples).
   - `V=5`: Exhaustive maximum depth (includes Keywords metadata row in context header).
3. **Keywords Threshold at `V≥4`**: Standardizes metadata inclusion, requiring a dedicated CSV `Keywords` row in the context header table only when verbosity reaches high detail (`V≥4` or `V=5`).
4. **RISEN Framework on `/review`**: Mandates a structured 5-stage critical evaluation methodology (**R**ole, **I**nstructions, **S**teps, **E**nd-goal, **N**arrowing constraints) whenever the user requests code or text review.
5. **Ambiguity Gate**: Requires the model to pause, identify ambiguous parameters, and seek clarification when user instructions lack critical context or technical specifications.
6. **No-Filler Constraint**: Strict policy against fluff, conversational pleasantries ("Sure, I can help with that!"), repetitive restatements, or unnecessary introductory preambles across all platforms.
7. **`/status` Command**: Unified operational status check command returning active verbosity, mode, tone, loaded rules, and system state across Web, Grok, and AGY2 interfaces.
8. **`/pdf` Command**: Standardized document export capability that triggers document extraction, visual-to-table conversion, professional markdown structuring, and PDF compilation.
