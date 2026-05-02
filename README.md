# Andrew — Clinical AI Engineer · Austere & Operational Medicine


---

## Focus

I design and deploy **AI-driven clinical decision support systems** for environments where infrastructure cannot be assumed — austere field operations, disaster response, and remote medical missions.

My work integrates **large language model inference**, **RAG-based clinical knowledge retrieval**, and **resilient edge architecture** under the constraint that degraded or absent connectivity is the operational baseline, not the exception.

---

## Primary System — Field-Deployable Edge CDSS

A production-oriented, voice-driven clinical decision support system architected for austere operational environments. Designed against real-world constraints: intermittent SATCOM uplinks, no local IT support, and clinicians whose hands are occupied.

### Architecture

```
┌─────────────────────────────────────────────────────┐
│ FIELD LAYER                                         │
│   Compute       Raspberry Pi Zero 2W                │
│   Networking    GL.iNet Beryl AX (WireGuard endpoint)│
│   Uplink        Starlink LEO (primary)              │
│                 Iridium SATCOM (degraded-mode)      │
├─────────────────────────────────────────────────────┤
│ CLOUD BACKEND                                       │
│   Orchestration Google Cloud VM                     │
│   Vector Store  ChromaDB                            │
│   CPG Corpus    JTS Clinical Practice Guidelines    │
│                 (ingested, chunked, embedded)        │
│   STT           OpenAI Whisper                      │
│   LLM / TTS     OpenAI · Anthropic Claude           │
├─────────────────────────────────────────────────────┤
│ GOVERNANCE                                          │
│   Framework     NIST AI RMF                         │
│   Functions     GOVERN · MAP · MEASURE · MANAGE     │
└─────────────────────────────────────────────────────┘
```

### Engineering Constraints

| Constraint | Design Response |
|---|---|
| Connectivity-degraded operations | Offline inference fallback; sync-on-reconnect |
| Hands-busy, eyes-occupied clinician | Primary I/O via voice (Whisper STT / Claude TTS) |
| Output auditability | All responses traceable to source CPG chunk |
| Deployment cost | Full field stack under $300 USD hardware |
| AI risk posture | NIST AI RMF mapped across all four core functions |

📄 [*AI at the Edge: Clinical Decision Support for Austere Medicine*](https://drive.google.com/file/d/18fzn9DlboeUK9aZB7tEnhJnpZGTfZuzi/view)

🔗 [AI in Austere Medicine Project]([https://github.com/](https://github.com/AI-in-Austere-Medicine-Project/pi-cloud-cdss) — GitHub organization


---

## Additional Technical Work

**Resilient Communications Architecture**
- Starlink LEO integration with gRPC dish telemetry and real-time link quality monitoring
- Iridium SATCOM as secondary uplink for true connectivity-independent operations
- RF communications: HF/VHF/UHF, APRS, AX.25 packet — operational comms design in non-permissive RF environments
- WireGuard mesh VPN across heterogeneous uplinks

**Applied ML**
- RAG pipeline design for constrained, high-stakes clinical corpora
- CNN image classification; transfer learning (InceptionV3); NLP sequence modeling
- LLM evaluation methodology for low-bandwidth, safety-critical inference contexts

**Systems & Network Engineering**
- Edge-to-cloud orchestration across intermittent SATCOM and LTE uplinks
- Network observability: traffic analysis, anomaly detection, flow monitoring (ntopng)
- IoT hardening and embedded systems security

---

## Stack

| Domain | Tools & Technologies |
|---|---|
| **Languages** | Python · Rust · Bash |
| **AI / ML** | Whisper · ChromaDB · LangChain · TensorFlow · Keras · OpenAI API · Anthropic API |
| **Cloud & Infra** | Google Cloud · Docker · Ubuntu Server · WireGuard VPN |
| **Networking** | GL.iNet · ntopng · WireGuard · APRS · AX.25 |
| **Hardware** | Raspberry Pi Zero 2W · GL.iNet Beryl AX · Starlink Terminal · Iridium modem |
| **Clinical / Education** | · LP · FP-C · WP-C | MSc Austere Critical Care

---

## Background

Advanced Practice Paramedic and CoROM MSc candidate working on AI-enabled clinical decision support for austere medicine. Focused on improving how clinicians make decisions when the environment is working against them. 
---

<sub>Available for collaboration on field-deployable clinical AI, austere medicine tooling, operational SATCOM integration, and edge ML systems.</sub>
