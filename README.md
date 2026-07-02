<p align="center">
  <img src="https://img.shields.io/badge/skills-18-blue?style=flat-square" alt="18 skills">
  <img src="https://img.shields.io/badge/license-MIT-green?style=flat-square" alt="MIT">
  <img src="https://img.shields.io/badge/platform-agnostic-purple?style=flat-square" alt="platform agnostic">
</p>

# Content Creator Pipeline

> **Give your AI agent a complete content creation brain.**
>
> 18 skills. One folder. Zero platform lock-in.
> From raw inspiration to calibrated publishing — every step, every decision, every file in the right place.

<br>

```
                    ┌──────────────────────────────────────────────────────────────────────┐
                    │                        CONTENT CREATOR PIPELINE                        │
                    └──────────────────────────────────────────────────────────────────────┘

  ┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐
  │  💡      │    │  ✍️      │    │  🎯      │    │  🔮      │    │  🎬      │    │  🚀      │
  │  SPARK   │───▶│  SEED    │───▶│  SCORE   │───▶│ PREDICT  │───▶│  SHOOT   │───▶│ PUBLISH  │
  │  火花固化 │    │  深挖写稿 │    │  盲打分   │    │  预测落盘 │    │  拍摄登记 │    │  发布登记 │
  └──────────┘    └──────────┘    └──────────┘    └──────────┘    └──────────┘    └──────────┘
       │               │               │               │               │               │
       │          ┌────────┐     ┌──────────┐    ┌──────────┐         │               │
       │          │humanizer│     │  cheat-   │    │  dbs-    │         │               │
       │          │ 去 AI 味 │     │  score-   │    │  hook    │         │               │
       │          └────────┘     │  blind    │    │ 开头优化  │         │               │
       │                         │  隔离打分  │    └──────────┘         │               │
       │                         └──────────┘                          │               │
       │                                                                │               │
       ▼                                                                ▼               ▼
  ┌──────────┐                                                   ┌──────────┐    ┌──────────┐
  │  📋      │                                                   │  📊      │    │  🔄      │
  │  INBOX   │                                                   │  RETRO   │───▶│ CALIBRATE│
  │  灵感库   │                                                   │  T+N 复盘 │    │  校准升级 │
  └──────────┘                                                   └──────────┘    └──────────┘
       │                                                                │               │
       │                                                                │         ┌─────┴─────┐
       │                                                                │         │ cheat-bump│
       │                                                                │         │ rubric升级│
       │                                                                │         ├───────────┤
       │                                                                │         │cheat-persona
       │                                                                │         │ 受众画像   │
       │                                                                │         ├───────────┤
       └────────────────────────────────────────────────────────────────┘         │cheat-recommend
                                                                         │ 选题推荐   │
                                                                         └───────────┘

     🔥 SPARK          ✍️ CREATE          🎯 EVALUATE         🚀 SHIP            📊 LEARN
  灵感→标题→盲打分   深挖角度→写稿     盲打分离→预测落盘   拍摄→发布→复盘   校准→画像→推荐
```

<br>

---

## What is this?

A **self-contained skill pack** that turns any AI agent into a professional content creation workflow engine.

No external dependencies. No platform assumptions. Just copy the folder and your AI knows:

- How to capture inspiration and turn it into scored, tracked ideas
- How to blind-score content against a calibrated rubric (agent isolation — no self-grading)
- How to write immutable prediction logs before publishing
- How to run post-publish retro analysis and evolve the scoring system

**Works with:** Hermes Agent · Claude Code · Codex · Cline · any AI that reads markdown skill files.

<br>

---

## Quick Start

```bash
# 1. Clone
git clone https://github.com/SamuelKwj/content-creator-pipeline.git

# 2. Install (Hermes)
cp -r content-creator-pipeline/ ~/.hermes/skills/creative/

# 3. Start
# In your AI chat, just say:
"初始化"
```

That's it. The AI loads the pipeline and guides you through everything.

**Not using Hermes?** Copy the folder to your project root. Your AI reads `SKILL.md` → understands the full workflow → loads skills from `skill/` on demand.

<br>

---

## How Your AI Agent Uses This

> This section is for **you** (the AI reading this README). Follow these rules.

### On First Load

1. Read `SKILL.md` — it's the master workflow document
2. If the user hasn't initialized: load `skill/cheat-init/SKILL.md` and guide them through setup
3. Ask: *"What type of content do you create?"* — never assume

### During a Session

| User says | You load | You do |
|-----------|----------|--------|
| "我有个想法" / "灵感" | `skill/cheat-spark/SKILL.md` | Give 3-4 title options → blind score → write to inbox |
| "我要口述" / "我说你记" | `skill/cheat-spark/SKILL.md` | Enter dictation mode: transcribe only, don't archive |
| "我想做一条关于X的" | `skill/cheat-seed/SKILL.md` | Deep-dive conversation → write draft outline |
| "打分这篇 [path]" | `skill/cheat-score/SKILL.md` | Delegate to blind sub-agent → display scores |
| "启动预测 [path]" | `skill/cheat-predict/SKILL.md` | Full prediction flow → immutable log |
| "拍了 [path]" | `skill/cheat-shoot/SKILL.md` | Create video folder, register shoot |
| "已发布 [url]" | `skill/cheat-publish/SKILL.md` | Write URL + timestamp to prediction header |
| "复盘 [path]" | `skill/cheat-retro/SKILL.md` | Collect data → compare prediction vs reality |
| "状态" / "看板" | `skill/cheat-status/SKILL.md` | Show calibration progress, buffer, pending retros |
| "升级 rubric" | `skill/cheat-bump/SKILL.md` | Re-score calibration pool → evolve rubric |
| "优化开头" | `skill/dbs-hook/SKILL.md` | Diagnose hook → generate alternatives |
| "去 AI 味" | `skill/humanizer/SKILL.md` | Strip AI tells, restore human voice |

### Critical Rules (DO NOT VIOLATE)

1. **Blind scoring only.** Never inline-score content. Always delegate to `cheat-score-blind` sub-agent.
2. **Predictions are immutable.** Once written, the prediction block cannot be changed. Retros append separately.
3. **Don't write the full script.** AI provides outlines and skeletons. The creator writes the final draft.
4. **Title options before archiving.** Never save a spark without offering 3-4 title angles first.
5. **Don't assume content type.** Always ask what kind of content the user creates.

### File Structure the AI Manages

```
<project>/
├── .cheat-state.json          # Global state (read/write)
├── rubric_notes.md            # Scoring dimensions
├── scripts/                   # Pre-shoot drafts
├── predictions/               # Immutable prediction logs
├── videos/                    # Post-shoot work dirs
├── archive/
│   ├── inbox.jsonl            # Scored spark inventory
│   └── good-articles/         # Curated reference articles
└── candidates.md              # Topic candidate pool
```

<br>

---

## Skill Inventory

### Core Pipeline (16 skills)

| # | Skill | Stage | What it does |
|---|-------|-------|-------------|
| 1 | `cheat-spark` | 💡 Spark | Capture inspiration → title options → blind score → inbox |
| 2 | `cheat-seed` | ✍️ Seed | Guided deep-dive → draft outline |
| 3 | `cheat-score` | 🎯 Score | Dispatch blind scoring to sub-agent |
| 4 | `cheat-score-blind` | 🎯 Score | **Isolated** sub-agent: reads only script + rubric |
| 5 | `cheat-predict` | 🔮 Predict | Immutable prediction log with anchor comparison |
| 6 | `cheat-shoot` | 🎬 Shoot | Register filming, create video folder |
| 7 | `cheat-publish` | 🚀 Publish | Write URL + platform + timestamp |
| 8 | `cheat-retro` | 📊 Retro | T+N data collection → prediction vs reality |
| 9 | `cheat-bump` | 🔄 Calibrate | Re-score pool → evolve rubric dimensions |
| 10 | `cheat-persona` | 🔄 Calibrate | Derive audience profile from comments |
| 11 | `cheat-recommend` | 🔄 Calibrate | Rank candidate topics by rubric |
| 12 | `cheat-trends` | 🔄 Calibrate | Fetch trending topics → rough-score → candidate pool |
| 13 | `cheat-status` | 📋 Monitor | Dashboard: progress, buffer, pending retros |
| 14 | `cheat-learn-from` | 📋 Setup | Import benchmark accounts → extract patterns |
| 15 | `cheat-migrate` | 📋 Setup | Upgrade .cheat-state.json schema |
| 16 | `cheat-init` | 📋 Setup | First-time project scaffolding |

### Utility (2 skills)

| # | Skill | What it does |
|---|-------|-------------|
| 17 | `humanizer` | Strip AI writing tells — restore human voice |
| 18 | `dbs-hook` | Diagnose and optimize opening hooks |

<br>

---

## Requirements

| Requirement | Notes |
|-------------|-------|
| AI agent with tool access | Hermes, Claude Code, Codex, Cline, etc. |
| LLM API key (OpenAI-compatible) | Used by skills for scoring, formatting, analysis |
| Data collection adapter | Optional — for auto-fetching play/comment stats |

<br>

---

## Philosophy

> **"厌蠢是赚钱的敌人 — 先发再优化"**
> *Hating imperfection is the enemy of making money. Ship first, optimize later.*

This pipeline is built on a simple insight: most creators fail not because their content is bad, but because they have no **calibration loop**. They ship, they feel, they guess.

This toolkit replaces guessing with a **scoring → prediction → retro → evolve** cycle. Every piece of content becomes a data point. Every data point sharpens the rubric. Every sharpened rubric makes the next prediction better.

It's not about being perfect. It's about getting better, measurably, every time.

<br>

---

## License

MIT · [github.com/SamuelKwj/content-creator-pipeline](https://github.com/SamuelKwj/content-creator-pipeline)
