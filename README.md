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

**Languages**

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-4EAA25?style=for-the-badge&logo=gnubash&logoColor=white)

**On-device AI**

![Ollama](https://img.shields.io/badge/Ollama-000000?style=for-the-badge&logo=ollama&logoColor=white)
![llama.cpp](https://img.shields.io/badge/llama.cpp-30363D?style=for-the-badge)
![MLX](https://img.shields.io/badge/-MLX-30363D?style=for-the-badge)
![ChromaDB](https://img.shields.io/badge/ChromaDB-30363D?style=for-the-badge)

**Speech**

![Whisper](https://img.shields.io/badge/-Whisper-30363D?style=for-the-badge)
![Vosk](https://img.shields.io/badge/-Vosk-30363D?style=for-the-badge)
![Piper](https://img.shields.io/badge/Piper-30363D?style=for-the-badge)
![Kokoro](https://img.shields.io/badge/Kokoro-30363D?style=for-the-badge)

**Systems and networking**

![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
![systemd](https://img.shields.io/badge/-systemd-30363D?style=for-the-badge)
![Cloudflare Tunnel](https://img.shields.io/badge/Cloudflare_Tunnel-F38020?style=for-the-badge&logo=cloudflare&logoColor=white)
![Tailscale](https://img.shields.io/badge/Tailscale-242424?style=for-the-badge&logo=tailscale&logoColor=white)
![WireGuard](https://img.shields.io/badge/WireGuard-88171A?style=for-the-badge&logo=wireguard&logoColor=white)

**Hardware**

![Jetson Orin Nano](https://img.shields.io/badge/Jetson_Orin_Nano-76B900?style=for-the-badge&logo=nvidia&logoColor=white)
![Radxa Zero 3W](https://img.shields.io/badge/-Radxa_Zero_3W-30363D?style=for-the-badge)
![Raspberry Pi](https://img.shields.io/badge/Raspberry_Pi-A22846?style=for-the-badge&logo=raspberrypi&logoColor=white)

## Background

Advanced Practice Paramedic · MSc Candidate · Austere & Operational Medicine.

Thesis work focused on AI implementation in austere and resource-limited environments.

Lead in the dirt!
