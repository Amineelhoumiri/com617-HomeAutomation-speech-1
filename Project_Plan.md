# Project Plan — MDAR Velbus Voice-Assistive Home Automation

> **Module:** COM617 Industrial Consulting Project  
> **Group:** Group 7  
> **Members:** Ilyass Athmani · Amine El Houmiri · Praveen Navodya Jayawardana
> **Supporting Tutor:** Craig Gallen  
> **Project Sponsor:** Stuart Hanlon — MDAR  
> **Submission:** AE1 — 8th May 2026 | AE2 Pitch — TBC

---

## 1. Project Overview

This project was commissioned by MDAR, a UK building automation company working with the Velbus ecosystem. The objective is to demonstrate how Velbus building automation hardware can be integrated with Home Assistant running on a Raspberry Pi 5, using MQTT as a monitoring and reporting layer, and adding a voice assistant capability using locally-hosted speech recognition and synthesis.

The system is intended as a proof-of-concept and tutorial for housing and office landlords who want centralised, voice-controllable building automation.

---

## 2. Team Roles

| Member | Role | Responsibilities |
|--------|------|-----------------|
| Ilyass Athmani | Lead Technical Engineer | Home Assistant configuration, Velbus integration, VelbusLink programming, voice pipeline (Whisper/Piper), AI integration (OpenRouter, Ollama), Node-RED flows, bug fixing |
| Amine El Houmiri | Technical Support & Documentation Lead | Assisted with implementation, research, documentation authoring, GitHub documentation |
| Praveen Navodya Jayawardana  | Research Analyst | Technology research (Velbus, Home Assistant, MQTT, Node-RED, OpenRemote), requirements gathering, AI model evaluation |

---

## 3. Sprint Schedule

### Sprint 1 — Gather Requirements (Weeks 1–3)

**Goal:** Define the technical scope and establish the project foundation.

| Week | Tasks | Status |
|------|-------|--------|
| Week 1 | Established GitHub repository. Reviewed project brief from MDAR. Conducted initial research into Velbus, Home Assistant, and Wyoming Protocol. | ✅ Complete |
| Week 2 | Created user persona. Drafted point-by-point requirements. Evaluated AI model options for voice assistant (Whisper vs other STT engines). Produced AI model research document. | ✅ Complete |
| Week 3 | Finalised outline solution proposal. Confirmed technology stack (HAOS, Velbus, MQTT, Node-RED, Wyoming). Presented to supporting tutor. | ✅ Complete |

**Sprint 1 Deliverables:**
- `requirements/` — point-by-point requirements
- `solution_proposal.md` — outline solution
- `user_persona.md` — user persona (Arthur)
- `ai_model_research.md` — AI model research
- `Project_Plan.md` — this document

---

### Sprint 2 — Initial Proof of Concept (Weeks 4–7)

**Goal:** Achieve basic hardware-software connectivity and demonstrate voice control.

| Week | Tasks | Status |
|------|-------|--------|
| Week 4 | Flashed Home Assistant OS to Raspberry Pi 5. Completed onboarding and initial dashboard setup. Connected Pi to network via ethernet (internet sharing from laptop). | ✅ Complete |
| Week 5 | Installed add-ons: Mosquitto, Node-RED, Wyoming Whisper, Wyoming Piper. Configured Wyoming Protocol connections using `core-whisper:10300` and `core-piper:10200`. Created MDAR Assistant voice pipeline. | ✅ Complete |
| Week 6 | Simulated Velbus devices using Home Assistant helpers (virtual light toggles) while awaiting hardware. Tested voice commands with simulated entities. Fixed browser microphone access using Chrome flags. | ✅ Complete |
| Week 7 | Received Velbus hardware kit. Programmed modules using VelbusLink on Windows PC (VMB4DC dimmers, VMB4RYLD relays, VMBGPOD-2 button actions). Connected USB interface back to Pi. Re-added Velbus integration — entities appeared. Presented PoC to tutor and sponsor. | ✅ Complete |

**Sprint 2 Deliverables:**
- Working Home Assistant instance on Raspberry Pi 5
- Wyoming Whisper and Piper connected and tested
- MDAR Assistant voice pipeline created
- Velbus hardware integrated with 8 named entities

---

### Sprint 3 — Minimal Viable Product (Weeks 8–15)

**Goal:** Complete all integrations, automations, and documentation for AE1 submission.

| Week | Tasks | Status |
|------|-------|--------|
| Week 8–9 | Renamed and assigned all Velbus entities to correct areas (Living Room, Kitchen, Bedroom, Toilet). Enabled and exposed VMBPIRM motion sensor. Exposed all entities to Assist. | ✅ Complete |
| Week 10–11 | Integrated OpenRouter as AI conversation agent. Tested Claude Sonnet 3.5 (tool-calling errors), switched to GPT-4o-mini (working). Tested local Ollama (Working). Finalised system prompt for MDAR Assistant. | ✅ Complete |
| Week 12 | Built Node-RED flows: motion-triggered lighting, all-lights-off, night mode, MQTT landlord reporting. Created Disco Light Show YAML script. Fixed entity ID issues in scripts. | ✅ Complete |
| Week 13 | Completed MQTT end-to-end testing. Verified Node-RED flows. Final system testing. | 🔄 In Progress |
| Week 14 | Final documentation: setup guide, problems and solutions, system architecture, AI usage declaration, PID. Upload all docs to GitHub. | 🔄 In Progress |
| Week 15 | AE1 submission (PID on SOL). AE2 pitch preparation. Final GitHub repo tidy-up. | ⏳ Upcoming |

**Sprint 3 Deliverables:**
- All 8 Velbus entities named, assigned to areas, exposed to Assist
- AI conversation agent (GPT-4o-mini via OpenRouter) working
- Node-RED flows built and tested
- MQTT reporting to `mdar/landlord/report`
- Disco Light Show script
- Full documentation suite
- PID (AE1) submitted

---

## 4. Technology Stack

| Technology | Purpose | Status |
|------------|---------|--------|
| Home Assistant OS | Central automation platform on Raspberry Pi 5 | ✅ Running |
| Velbus (VMB4DC, VMB4RYLD, VMBPIRM, VMBGPOD-2) | Physical building automation hardware | ✅ Integrated |
| Wyoming Whisper | Speech-to-text (STT) | ✅ Working |
| Wyoming Piper | Text-to-speech (TTS) | ✅ Working |
| Mosquitto MQTT Broker | Device state messaging | ✅ Running |
| Node-RED | Automation flow builder | ✅ Flows built |
| OpenRouter / GPT-4o-mini | AI conversation agent | ✅ Working |
| Ollama (local LLMs) | Local AI alternative (evaluated) | ✅ Working |
| VelbusLink | Velbus module programming (Windows) | ✅ Used |

---

## 5. Risk Register

| Risk | Impact | Mitigation | Status |
|------|--------|------------|--------|
| Velbus hardware unavailable for Sprint 2 | High | Simulated with Home Assistant helpers until hardware arrived | ✅ Resolved |
| Wyoming connection failing on localhost | Medium | Used internal container hostnames (core-whisper, core-piper) | ✅ Resolved |
| Browser blocking microphone on HTTP | Medium | Used Chrome flags to whitelist HA URL as trusted origin | ✅ Resolved |
| AI model tool-calling errors (Claude Sonnet) | Medium | Switched to GPT-4o-mini — more reliable for HA tool calling | ✅ Resolved |
| Local LLM too slow for voice (Ollama) | Medium | Documented as alternative; GPT-4o-mini used for production | ✅ Resolved |
| MQTT reporting not fully verified | Medium | Testing in progress — priority before submission | 🔄 In Progress |
| Submission deadline 8th May | High | All core deliverables on track | ⏳ Monitoring |

---

## 6. Issues Resolved

For a full log of all technical problems encountered and how they were fixed, see:
[docs/problems-and-solutions.md](docs/problems-and-solutions.md)

---

## 7. Key Dates

| Date | Milestone |
|------|-----------|
| January 2026 | Project brief issued |
| Weeks 1–3 | Sprint 1 — Requirements and research |
| Weeks 4–7 | Sprint 2 — Proof of concept |
| Weeks 8–15 | Sprint 3 — MVP and documentation |
| 8th May 2026 (16:00) | **AE1 submission deadline — PID on SOL** |
| TBC | AE2 pitch to tutor and sponsor |
| 1st July 2026 | Resit deadline (if applicable) |

---

*Last updated: March 2026 — COM617 Group 7 — Southampton Solent University*
