
# Outline Solution Proposal: Autonomous Voice-Assistive System

## 1. System Architecture Overview

The proposed solution uses a **Raspberry Pi 5** as the central automation hub, running **Home Assistant (HA)** and **Node-RED**. The system is designed to be entirely local (no cloud) to ensure tenant privacy and operational reliability.

### Key Components:

* **Hardware Control:** Velbus modules for physical lighting and power actuation.
* **Local AI "Brain":** Whisper (STT) and Piper (TTS) running via the Wyoming Protocol.
* **Communication:** MQTT for reporting status to a central landlord dashboard.

---

## 2. Technical Data Flow

The system operates through a circular feedback loop to ensure the user always knows the status of their home:

### Step 1: Input & Interpretation

* **Voice Capture:** A local microphone captures Arthur's command.
* **Speech-to-Text (STT):** OpenAI Whisper (Base-en) processes the audio locally on the Pi 5 and converts it to text.
* **Natural Language Processing:** Home Assistant's *Assist* engine identifies the intent (e.g., "Turn on Kitchen Light").

### Step 2: Actuation & Hardware Interface

* **Command Transmission:** Home Assistant sends the command to the **Velbus USB Interface**.
* **Physical Action:** The Velbus Relay module switches the high-voltage circuit to power the light.
* **State Confirmation:** The Velbus module sends a confirmation signal back through the CAN-bus to the Pi 5.

### Step 3: Output & Reporting

* **Text-to-Speech (TTS):** Piper generates a spoken confirmation: *"Kitchen light is now ON"*.
* **Landlord Update:** The system simultaneously publishes an **MQTT message** (e.g., `landlord/unit01/kitchen_light: ON`) to a HiveMQ or Mosquitto broker.
* **Visual Overlay (Optional):** If a TV is present, a notification is pushed via the TV-Overlay API.

---

## 3. Accessibility Features

* **Flash Cards:** A high-contrast dashboard allows Arthur to trigger pre-set phrases or Velbus scenes without speaking.
* **Verification:** The mandatory TTS feedback ensures visually impaired users aren't left guessing if a command worked.

