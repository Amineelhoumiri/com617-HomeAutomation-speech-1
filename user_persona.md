
# User Persona: Arthur Penhaligon

**Primary User for MDAR VELBUS Voice-Assistive System**

## 1. Profile Overview

* **Age:** 72
* **Location:** Assisted Living Managed Apartment, Southampton.
* **Background:** Retired Civil Engineer. Arthur is technically literate but suffers from age-related physical declines that hinder his interaction with standard home environments.
* **Condition:** * **Visual Impairment:** Advanced Macular Degeneration. Arthur has lost central vision, making it impossible to read small text on light switches, thermostats, or smartphone apps.
* **Vocal Health:** Occasional "vocal fatigue," meaning he requires non-verbal alternatives (Flash Cards) on days when his voice is weak.



---

## 2. Goals and Motivations

* **Independence:** To live without a 24/7 onsite carer by using technology to manage his environment.
* **Safety & Verification:** To receive immediate confirmation that an action has happened (e.g., knowing for sure that the oven or a heater is actually OFF).
* **Privacy:** He is highly skeptical of "Big Tech" (Amazon/Google) and does not want his private conversations recorded or sent to the cloud.

---

## 3. Pain Points

* **The "Invisible" Switch:** Traditional white-on-white light switches are invisible to him. He often leaves lights on in empty rooms, increasing his utility costs.
* **Complex Interfaces:** Touchscreen-only smart home hubs are useless to him because he cannot see the icons to press them.
* **The "Silent" House:** Standard homes provide no feedback. If he presses a button, he doesn't know if it worked unless he can physically see the light change.

---

## 4. Use Case Scenarios

### Scenario A: Verbal Interaction (Visual Impairment)

Arthur enters the kitchen at night. Instead of fumbling for a switch, he says: *"Turn on the kitchen light."*

* **System Action:** Whisper (STT) processes the command; Velbus toggles the relay.
* **Feedback:** Piper (TTS) announces: *"Kitchen light is now ON."* Arthur now has 100% certainty of the state of his home.

### Scenario B: Non-Verbal Interaction (Flash Cards)

On a day when Arthur's voice is strained, he uses a tablet mounted on his wall with high-contrast "Flash Cards."

* **Action:** He taps a large, high-contrast Red icon for "Help/Assistance."
* **System Action:** The system generates a spoken alert through the apartment speakers: *"Arthur requires assistance in the living room,"* and sends an **MQTT message** to the Landlord's central office.

---

## 5. Why the "Local AI" Selection Matters for Arthur

* **Whisper (Base-en):** Arthur has a slight regional accent; the "Base" model ensures his commands are understood correctly the first time.
* **Piper (British Female):** The clear, southern English accent is familiar and easy for him to hear over background noise like a radio.
* **Autonomous Operation:** Arthur feels secure knowing that his data stays inside his four walls, fulfilling the "Private-by-Design" requirement of the landlord.

---

## 6. Success Metrics for Arthur

1. **Latency:** The gap between Arthur speaking and the house responding must be **< 2 seconds**.
2. **Reliability:** The system must work even if the apartment's Wi-Fi goes down.
3. **Accuracy:** The system should correctly interpret Arthur's commands **95% of the time**.
