# Andrew Azelton — Clinical AI Research · Austere & Operational Medicine

I design, build, and field-test **deterministic-first clinical AI** — decision
support systems where conventional software owns every computable decision and
language models handle only language, engineered for environments where
infrastructure cannot be assumed. Everything is published openly, including
what fails.

[AI in Austere Medicine Project (AI-AMP)](https://github.com/AI-in-Austere-Medicine-Project) ·
[Substack](https://aiamp.substack.com) ·
[LinkedIn](https://www.linkedin.com/in/andrew-azelton)

---

## Current Work — EdgeCDSS v4.0

Voice-driven clinical decision support grounded in Joint Trauma System Clinical
Practice Guidelines, built on a **deterministic-first architecture**: conventional
software owns every computable decision (dosing, contraindications, safety
gates); the language model handles only genuine language understanding.

**Status:** v4.0 in public beta · Operational field study, Tanzania, August 2026

### Architecture

```
VOICE / TEXT INPUT
        │
        ▼
DETERMINISTIC-FIRST PIPELINE
  clinical intent router (JSON-driven, 89 protocols)
  safety pre-gates · negation-aware detection
  weight-confirmed dose engine → final mL volumes
        │
        ▼
RETRIEVAL (RAG)
  ChromaDB · 7,186 chunks · 89 JTS CPGs
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
| Multi-turn context isolation | History informs facts; only the current query sets clinical intent |
| Auditability | Every response traceable to source CPG chunk; per-query session logs |
| Aligned frameworks | NIST AI RMF · NAM AI Code of Conduct-informed design |

Evaluation findings — including failures identified by external clinical
testers — are documented and published openly:
[evaluation reports](https://github.com/AI-in-Austere-Medicine-Project/pi-cloud-cdss/tree/main/docs).

### Deployment Tiers

| Tier | Status | Stack |
| --- | --- | --- |
| Cloud | Live (beta) | FastAPI · ChromaDB · GPT-4o-mini · OpenAI Whisper/TTS · self-hosted edge server (Jetson Orin Nano) · Cloudflare Tunnel |
| Offline | In development | Jetson Orin Nano 8GB · Ollama · 3B-class local models · zero-connectivity operation |
| Hybrid | Planned | Opportunistic cloud sync · Iridium SBD · LoRa mesh |

### Field Study — Tanzania 2026

An operational feasibility study of EdgeCDSS infrastructure in East Africa,
conducted alongside — and independent of — my MSc clinical placement. The system
travels on its own edge hardware and is evaluated on real-world operating
conditions: **no patient contact, no clinical use, no facility integration.**

Measured: off-grid solar power and voltage conversion · local LTE (Vodacom) and
satellite uplink behavior · decentralized communications options · GPS-tagged
uptime and connectivity logging · complete operational cost accounting.

Findings will be published openly through AI-AMP as an operations report.

---

## Additional Technical Work

**Resilient communications** — Starlink LEO integration with gRPC dish telemetry;
Iridium SATCOM degraded-mode uplink; HF/VHF/UHF, APRS, AX.25; WireGuard mesh
across heterogeneous links.

**Applied ML** — RAG pipeline design for safety-critical clinical corpora; LLM
evaluation methodology for low-bandwidth, high-stakes inference; CNN image
classification and transfer learning (InceptionV3).

**Systems** — Edge-to-cloud orchestration over intermittent uplinks; systemd
service hardening; network observability (ntopng); embedded systems security.

---

## Stack

| Domain | Tools |
| --- | --- |
| Languages | Python · Rust · Bash |
| AI / ML | OpenAI API · Anthropic API · Whisper · ChromaDB · Ollama · TensorFlow |
| Infra | Ubuntu Server · systemd · Docker · Cloudflare Tunnel · WireGuard · GCP |
| Edge hardware | NVIDIA Jetson Orin Nano · Raspberry Pi 5 · Starlink · Iridium · GL.iNet |

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
