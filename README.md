# Andrew Azelton — Clinical AI Research · Austere & Operational Medicine

I design, build, and field-test **deterministic-first clinical AI** — decision
support systems where conventional software owns every computable decision and
language models handle only language, engineered for environments where
infrastructure cannot be assumed. Everything is published openly, including
what fails.

[AI in Austere Medicine Project (AI-AMP)](https://ai-in-austere-medicine-project.github.io) ·
[LinkedIn](https://www.linkedin.com/in/andrew-azelton)

---

## Current Work — EdgeCDSS v4.3

Voice-driven clinical decision support grounded in Joint Trauma System Clinical
Practice Guidelines, built on a **deterministic-first architecture**: conventional
software owns every computable decision (dosing, contraindications, safety
gates); the language model handles only genuine language understanding.

**Status:** v4.3.0 in public beta · Operational field study, Tanzania, underway
August 2026

### Architecture

```
VOICE / TEXT INPUT
        │
        ▼
DETERMINISTIC-FIRST PIPELINE
  clinical intent router (JSON-driven, 89 protocols)
  safety pre-gates · negation-aware detection
  patient context · vitals with per-reading age · derived MAP
  weight-confirmed dose engine → final mL volumes
        │
        ▼
CLINICIAN-AUTHORED CARDS
  served verbatim, never generated · unsigned card = absent card
        │
        ▼
RETRIEVAL (RAG)
  ChromaDB · 8,559 passages · 89 JTS CPGs
  source attribution on every response
        │
        ▼
LLM NARRATION (constrained)
  may copy validated doses — never calculate them
        │
        ▼
TWO-PASS VALIDATOR (fail-closed)
  response blocked if it contradicts deterministic result
        │
        ▼
SESSION AUDIT LOG (JSONL, PHI-free)
```

### Safety Engineering

| Principle | Implementation |
| --- | --- |
| Never ask an LLM to do what code can do with certainty | Deterministic dose engine; LLM copies validated values only |
| Fail closed | Two-pass validator rejects output that contradicts rules |
| An unsigned clinical statement is an absent one | The card engine refuses any card still holding a signoff placeholder, and no debug flag or override can reach that gate |
| Multi-turn context isolation | History informs facts; only the current query sets clinical intent |
| Auditability | Every response traceable to source CPG chunk or signed card; per-query session logs |
| Aligned frameworks | NIST AI RMF · NAM AI Code of Conduct-informed design |

Evaluation findings — including failures identified by external clinical
testers — are documented and published openly:
[evaluation reports](https://github.com/AI-in-Austere-Medicine-Project/pi-cloud-cdss/tree/main/docs) ·
[v4.3 release notes](https://ai-in-austere-medicine-project.github.io/pi-cloud-cdss/web/release-notes-4.3.html).

### What v4.3 Added — Authorship as a Safety Control

Retrieval can only return what somebody already wrote down. A standing
160-scenario evaluation harness measured the consequence: **0 of 4 DKA
ventilator phrasings returned any of tidal volume, rate, PEEP or FiO2** —
100% reproducible — against 4 of 4 for traumatic brain injury, which the corpus
happened to cover well. The system produced fluent prose that never reached a
number, which is the most dangerous kind of answer because it looks like help.

The fix was not a better prompt. It was a third source of truth alongside the
guideline corpus and the labelled general-reference fallback: a **clinical card**
a clinician writes, dates, references, and signs — served verbatim — plus a gate
that makes an unsigned card indistinguishable from an absent one.

- **DKA is now 4 of 4**, with TBI held at 4 of 4 as the control
- **5 of 13 cards signed and live**; the other 8 are authored, unsigned, dark,
  and invisible to the pipeline — partial deployment is the normal state, not a
  migration step
- **No override exists.** A test asserts the project's debug-downgrade flag does
  not appear in the module and that the servability check takes no parameter a
  bypass could ride in on
- **Tidal volume dosed on Devine ideal body weight**, not actual weight; a
  missing height falls back and says so rather than guessing

### System Design — Hybrid by Default

EdgeCDSS is one system, not separate products: a self-hosted edge server that
uses cloud inference opportunistically and falls back to local inference when
connectivity drops. The same hardware deploys to the field.

| Component | Status | Detail |
| --- | --- | --- |
| Edge server | Live | Jetson Orin Nano 8GB, self-hosted · FastAPI · ChromaDB · Cloudflare Tunnel |
| Cloud inference | Live (beta) | Multi-provider grid — OpenAI, Anthropic, Google Gemini, xAI — models are configuration, not code |
| Local inference | In development | Ollama · 3B-class models — zero-connectivity fallback, wired into the same provider grid |
| Opportunistic sync | In development | Automatic cloud/local routing on link state |
| Field configuration | In the field, Aug 2026 | Solar power · LTE (Vodacom) / satellite uplink · GPS-tagged logging |

### Verification

| | |
| --- | --- |
| Offline regression suite | 859 tests, ~8s — no network, no API key, no vector database |
| Evaluation harness | 160 scenarios replayed against a pinned server snapshot; before/after published with every fix |
| Round-1 result | Hard safety failures 1 → 0 · refusal rate 15.6% → 1.9% · human-review banner rate 68.1% → 16.9% · 23 scenarios changed outcome, none toward unsafe |

The working rule is one fix, one commit, one regression test — with a mutation
check on each, where the fix is reverted, the named test is confirmed to fail,
and the fix restored.

### Field Study — Tanzania 2026

An operational feasibility study of EdgeCDSS infrastructure in East Africa,
conducted alongside — and independent of — my MSc clinical placement. The system
travels on its own edge hardware and is evaluated on real-world operating
conditions: **no patient contact, no clinical use, no facility integration.**

Measured: off-grid solar power and voltage conversion · local LTE (Vodacom) and
satellite uplink behavior · encrypted LoRa mesh endurance · GPS-tagged
uptime and connectivity logging · complete operational cost accounting.

**Mesh endurance test** — an encrypted LoRa mesh network (Meshtastic) run
continuously for the duration of the study: a GPS-equipped base station plus two
T1000-E GPS tracker nodes carried during daily movement. A deliberately simple,
independent experiment measuring what matters first — uptime, battery drain, and
passive position tracking under real field conditions. Long-term direction,
beyond this study: converging mesh communications and the EdgeCDSS platform into
fully decentralized, open-source medical communications.

Findings will be published openly through AI-AMP as an operations report.

---

## Additional Technical Work

**Resilient communications** — Starlink LEO integration with gRPC dish telemetry;
Iridium SATCOM degraded-mode uplink; HF/VHF/UHF, APRS, AX.25; WireGuard mesh
across heterogeneous links. [netpath](https://github.com/AI-in-Austere-Medicine-Project/netpath)
— an open-source traceroute visualizer that enriches every hop with geolocation
and ASN data, built to characterize satellite versus terrestrial routing before
trusting a link.

**Applied ML** — RAG pipeline design for safety-critical clinical corpora;
evaluation-harness methodology for turning a clinical anecdote into a
reproducible defect with a control group; LLM evaluation for low-bandwidth,
high-stakes inference; CNN image classification and transfer learning
(InceptionV3).

**Systems** — Edge-to-cloud orchestration over intermittent uplinks; systemd
service hardening; secret redaction driven by provider declarations rather than
key-shape patterns; network observability (ntopng); embedded systems security.

---

## Stack

| Domain | Tools |
| --- | --- |
| Languages | Python · Rust · Bash |
| AI / ML | OpenAI API · Anthropic API · Google Gemini · xAI · Ollama · Whisper · ChromaDB · TensorFlow |
| Infra | Ubuntu Server · systemd · Docker · Cloudflare Tunnel · WireGuard · GCP |
| Edge hardware | NVIDIA Jetson Orin Nano · Raspberry Pi 5 · Starlink · Iridium · Meshtastic / LoRa · GL.iNet |

---

## Background — Why This Work

I'm a practicing Advanced Practice Paramedic with experience across urban,
austere, and special operations medicine — the environments this work is built
for. The systems I build are the tools I would have to trust in the field. I
mentor paramedics in advanced life support, clinical leadership, and critical
care transport, and lecture nationally on artificial intelligence in austere
medicine, critical care transport, and out-of-hospital clinical leadership.

I am an MSc candidate in [Austere Critical Care at the College of Remote and
Offshore Medicine (CoROM)](https://corom.edu.mt/msc-in-austere-critical-care/),
Malta. My thesis — *Artificial Intelligence for Diagnostic Accuracy and Clinical
Decision-Making in Austere Medical Environments: Clinician Perspectives from the
Field* — is an exploratory qualitative descriptive study examining how clinicians
with austere experience perceive the role, reliability, and limits of AI decision
support, and what shapes their trust in it.

---

## Education, Credentials & Affiliations

**Education** — MSc Austere Critical Care (candidate), College of Remote and
Offshore Medicine, Malta · BS Emergency Health Science, University of Texas
Health Science Center · AAS Emergency Medical Services, Oklahoma City Community
College

**Credentials** — Nationally Registered Paramedic (NRP) · Licensed Paramedic
(LP), Texas · Board-Certified Flight Paramedic (FP-C) · Certified Wilderness
Paramedic (WP-C) · EMS Instructor, Texas

**Professional organizations** — Wilderness Medical Society (WMS, active
committee member) · Special Operations Medical Association (SOMA) · National
Association of EMS Educators (NAEMSE) · International College of Advanced
Practice Paramedics (ICAPP) · World Extreme Medicine (WEM)

---

*EdgeCDSS is a research and education system — not validated for clinical use.
All AI-AMP work is independent research, MIT licensed, and does not represent
the views of my employer or affiliated institutions. Open to collaboration on
field-deployable clinical AI, austere medicine tooling, and edge ML systems.*
