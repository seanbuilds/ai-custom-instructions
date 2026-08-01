# Custom Instruction Suite v3+
> **Multi-Platform AI System Prompt Suite** · Gemini Flash · Grok MoE · Antigravity 2 IDE

**Final Score: 95/100** | Reviewed by a 3-manager council across 5 dimensions | ✅ Cleared for deployment

---

## What This Is

A production-ready set of platform-specific AI custom instructions built to a common v3+ specification. Every variant shares a unified behavioral contract (stamps, verbosity ladder, slash commands, RISEN audit) while being optimized for its target platform's native capabilities.

The suite was built across 3 build iterations with a formal review rubric scored by 3 independent manager agents:

| Build | Score | Verdict |
|:---:|:---:|:---|
| Build 1 | 49/100 | ❌ REJECT — 4 of 6 files never produced |
| Build 2 | 89/100 | ⚠️ REVISE — 10 critical findings patched |
| Build 3 | 94/100 | ✅ SHIP — all critical findings resolved |
| + Polish | **95/100** | ✅ SHIP — Grok expansion layer scale aligned |

---

## Files

```
custom_instructions_v3/
├── README.md                     ← you are here
├── gemini_flash_tier_a.md        ← Gemini Web UI (paste directly)
├── gemini_flash_tier_b.md        ← Gemini Flash API / full spec
├── grok_tier_a.md                ← Grok Custom Agent (paste directly)
├── grok_tier_b.md                ← Grok API / full MoE spec
├── antigravity2_tier_b.md        ← Antigravity 2 IDE rules (full spec)
└── cross_platform_comparison.md  ← Feature parity reference table
```

---

## Quick Deployment

### Gemini Web (Flash) — Tier A
1. Open **Gemini** → Settings → **Custom Instructions**
2. Paste the full content of `gemini_flash_tier_a.md`
3. Save — **1,192 characters** (budget: ≤1,200 ✅)

### Grok (xAI) — Tier A
1. Open **Grok** → **Create Agent** → System Prompt
2. Paste the full content of `grok_tier_a.md`
3. Save — **3,974 characters** (budget: ≤4,000 ✅)
4. The final line `MoE ORCHESTRATION LAYER ONLINE...` is the activation trigger — keep it

### Antigravity 2 IDE
- Use `antigravity2_tier_b.md` as the global system rules file
- No compressed tier — the full spec is the only variant
- Includes planning gate, tool priority, and `[CONFIRM]` guard out of the box

### API / Developer Use
- Use the `*_tier_b.md` variants for programmatic system prompt injection
- All Tier B files use XML tag delimiters for reliable section parsing

---

## What Every Variant Does

All three platforms enforce the same behavioral contract:

| Rule | Behavior |
|:---|:---|
| **Dual Stamps** | Every response begins and ends with `` `[YYYY-MM-DD HH:MM AM/PM - REQ-YYYYDDD-HHMMSS - <Title>]` `` |
| **Priority Order** | Stamps (1) > Doc Workflow (2) > Expert Protocol (3) — always |
| **Expert Context Table** | Rendered on every response (Keywords row active at V≥4 only) |
| **Verbosity Ladder** | V=0 (one line) through V=5 (exhaustive multi-turn). Set with `v=[0-5]` |
| **Ambiguity Gate** | Ask exactly ONE clarifying question before answering unclear intent |
| **No AI Filler** | Never opens with "Certainly!", "Great question!", "As an AI..." |
| **RISEN Audit** | `/review` triggers a Red-Team Critic pass — never output verbatim |
| **Expansion Layer** | V≥3 appends `### 🔗 See Also` + `### 🕳️ Rabbit Holes` (specific named entries only) |
| **/status** | One-line session state: `📊 V=[n] \| tone: [x] \| mode: [x] \| stamps: on \| keywords: [on/off]` |
| **/pdf** | Document Processing Workflow: OCR → structure → export → path-only reply |

---

## Shared Slash Commands

All three platforms respond to these commands:

| Command | Behavior |
|:---|:---|
| `/help` | Operational guide: protocols, commands, V-ladder |
| `/summary` | Executive summary + key takeaways |
| `/q` | Generate 3–5 actionable follow-up questions |
| `/redo [framework]` | Re-render last response (e.g. `/redo ELI5`, `/redo bullet-only`) |
| `/review` | Trigger RISEN Red-Team Critic audit |
| `/more` | Drill deeper into current topic |
| `/alt` | Alternative approaches, options, or trade-offs |
| `/arg` | Devil's advocate / counter-argument |
| `/joke` | SFW topic-relevant joke |
| `/status` | Current session state (V, tone, mode, stamps, keywords) |
| `/pdf` | Document OCR → structured export → local path |
| `v=[0-5]` | Set verbosity for rest of session |

---

## Platform Differences at a Glance

| Feature | Gemini Flash | Grok | Antigravity 2 |
|:---|:---:|:---:|:---:|
| Default V | **V=2** | **V=3** | **V=2** |
| Header | Context Table | MoE Routing Matrix | Hybrid Matrix |
| MoE multi-agent decomposition | ❌ | ✅ | ❌ |
| `/debate` `/compare` `/optimize` `/links` | ❌ | ✅ GROK-ONLY | ❌ |
| `tone [casual\|formal\|socratic]` | ✅ | ❌ | ❌ |
| `mode [code\|research\|doc]` | ✅ | ❌ | ❌ |
| Planning gate (`implementation_plan.md` required) | ❌ | ❌ | ✅ |
| `/plan` command | ❌ | ❌ | ✅ AGY2-ONLY |
| Destructive action guard (`[CONFIRM]`) | ❌ | ❌ | ✅ |
| Google Search hyperlinks | Conditional | Full DeepSearch | ❌ use grep |
| MoE activation line | ❌ | ✅ | ❌ |

---

## Verbosity Ladder (All Platforms)

| Level | Label | Behavior | Extras |
|:---:|:---|:---|:---|
| V=0 | Minimal | Single word or one line | Stamps only |
| V=1 | Terse | Brief bullet list | No keywords, no expansion |
| V=2 | Concise | Essential details only — **default** | Context table, no keywords |
| V=3 | Detailed/Thorough | Full explanation | Context table + Expansion Layer |
| V=4 | Comprehensive | Deep detail + examples | **Keywords row active** |
| V=5 | Exhaustive | Maximum depth, multi-turn | Keywords + max expansion entries |

> **Grok default is V=3** (not V=2) to support multi-agent attribution overhead.

---

## The Expert Context Table

Every response begins with a context table (format varies slightly by platform):

```
| Context Element | Details                                      |
|:--------------- |:---------------------------------------------|
| Expert(s)       | Lead domain specialist + secondary expert     |
| Keywords        | Technical CSV jargon — only at V≥4           |
| Refined Question| Actionable query directed to expert           |
| Response Plan   | Strategy and methodology                     |
```

---

## The Dual Stamp Format

Every response starts and ends with:

```
`[2026-08-01 07:11 PM - REQ-2026213-191154 - Document Title Here]`
```

**REQ-ID format:** `REQ-` + 4-digit year + 3-digit ordinal day (001–366) + `-` + HHMMSS (24hr)
Example: `REQ-2026213-191154` = Year 2026, day 213, time 19:11:54

---

## RISEN Audit Engine (`/review`)

RISEN is the behavioral spec for what happens when you type `/review`. It is **never output verbatim** — it is the internal logic of the critique:

- **R**ole: Adversarial Red-Team Lead
- **I**nstructions: Inspect for flaws, gaps, security issues, incorrect claims
- **S**teps: Identify defect → demonstrate failure mode → propose minimal fix
- **E**xpectation: Structured verdict with severity-bucketed findings
- **N**arrowing: Focus only on correctness, security, performance, integrity

Output: a structured audit report with PASS/FAIL verdict and actionable findings.

---

## Review Rubric (Reference)

The suite was scored across 5 dimensions:

| Dim | Name | Max | Build 3 Score |
|:---:|:---|:---:|:---:|
| D1 | Deployability & Technical Compliance | 25 | 24 |
| D2 | Prompt Engineering Quality | 25 | 24 |
| D3 | Platform Differentiation & Fit | 25 | 22 |
| D4 | Cross-Platform Consistency | 15 | 15 ✨ |
| D5 | UX & Command Design | 10 | 10 ✨ |
| | **TOTAL** | **100** | **95** |

---

## Future Improvements (Build 4 Candidates)

Low-effort patches that would push toward 100/100:

1. **F3.2** — Remove `<moe_activation>` XML wrapper from `grok_tier_b.md`; place bare activation line as final content line
2. **F3.4** — Compress `tone`/`mode` definitions in `gemini_flash_tier_b.md` to reduce byte count below Grok Tier B
3. **UX** — Add `/rollback` to AGY2 (surfaces the existing rollback procedure as a user command)
4. **UX** — Add `/reset` to all variants (restores session to platform defaults)
5. **UX** — Add `/help` output template (currently defined but with no output spec)
6. **P2.3** — Grok/AGY2 ambiguity gate: change "ask targeted clarifying questions" to "ask ONE targeted clarifying question"

---

## Build History

| Date | Event | Score |
|:---|:---|:---:|
| 2026-08-01 | User request: 3-platform custom instruction suite | — |
| 2026-08-01 | Build 1 delivered (Flash files only — 4 missing) | 49/100 ❌ |
| 2026-08-01 | Build 2 delivered (all 6 files) + 10 critical patches | 89/100 ⚠️ |
| 2026-08-01 | Build 3: 8 surgical patches applied | 94/100 ✅ |
| 2026-08-01 | POLISH-1: Grok expansion layer scale aligned | **95/100** ✅ |

---

*Suite version: v3+ · Last updated: 2026-08-01 · Reviewed by: 3-manager council*
