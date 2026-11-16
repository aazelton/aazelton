# Andrew Azelton
**Clinical AI for austere and operational medicine**

I build and test deterministic-first clinical decision support: code owns every dose, check and safety gate, and AI handles only language. It runs offline on hardware you can carry. Everything is published, including what fails.

[AI-AMP](https://ai-in-austere-medicine-project.github.io) · [Substack](https://aiamp.substack.com) · [LinkedIn](https://www.linkedin.com/in/andrew-azelton)

## Current work

| Project | What it is |
| --- | --- |
| [EdgeCDSS Pocket](https://github.com/AI-in-Austere-Medicine-Project/edgecdss-pocket) v1.1 | Wearable voice dose assistant. Fixed vocabulary, read-back and confirm, clinician-signed doses, no language model. [Try it](https://cdss.arcanekg.com/pocket) |
| [EdgeCDSS](https://github.com/AI-in-Austere-Medicine-Project/pi-cloud-cdss) v5.1.0 | Offline guideline search and dose support on an NVIDIA Jetson. 89 Joint Trauma System guidelines, an on-device model, every dose signed and checked by code. [Portal](https://cdss.arcanekg.com) |

## What I do

- **Safety engineering for clinical AI.** Signed dose contracts traced to source pages, fail-closed gates, test-first fixes, and a replay of every stored answer before a change ships.
- **On-device AI.** Local model inference, retrieval over clinical guidelines, and speech in and out, on Jetson and single-board computers.
- **Model training and evaluation.** LoRA fine-tuning and quantization of small models, judged by clinician review, with benchmark scores as advisory. [Model card](https://huggingface.co/akaclinicalco/edgecdss-v3-research)
- **Resilient communications.** Starlink, Iridium, HF/VHF/UHF and WireGuard mesh for intermittent links.

## Stack

Python · Bash · Ollama · llama.cpp · MLX · ChromaDB · Whisper · Vosk · Piper · Kokoro · Ubuntu · systemd · Cloudflare Tunnel · Tailscale · WireGuard · Jetson Orin Nano · Radxa Zero 3W · Raspberry Pi

## Background

Advanced Practice Paramedic · MSc Candidate · Austere & Operational Medicine.

Thesis work focused on AI implementation in austere and resource-limited environments.

Lead in the dirt!


