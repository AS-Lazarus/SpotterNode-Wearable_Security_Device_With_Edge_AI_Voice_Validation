# SpotterNode: A Wearable Iot-Based Anti-Kidnapping System Featuring Edge Ai Voice Validation And Power-Gated Telemetry 

**Status:** System Design & Hardware Assembly (Final Year EEE Thesis)
Phase 1: Hardware Architecture and Component Procurement completed.
Phase 2: Breadboard validation and firmware development actively underway.

## Project Overview
A covert, wearable IoT security node disguised as a body sttrap. Designed to bypass assailant scrutiny in high-risk zones, the system prioritizes a "Silent-First Protocol" to capture evidence and transmit real-time GPS coordinates under duress.

##Key Innovation: Edge AI Voice Validation & Power-Gated Telemetry
Traditional panic buttons fail during a crisis because they require obvious, suspicious hand movements and are prone to false alarms. This system utilizes a covert, multi-modal trigger based on localized AI validation:

1. **The Mechanism:** A discrete tactile button press or kinematic anomaly (monitored by an MPU-6050 on a thigh strap) is monitored by the microcontroller.

2. **The Trigger:** An INMP441 microphone captures audio, and a pre-trained Edge AI model validates a specific distress wake-word locally on the microcontroller, eliminating false positives.

3. **The Result:** The system activates a custom IRF9540/2N7000 power gate to wake the high-current GSM module, covertly broadcasting GPS coordinates while the user appears entirely compliant with the assailants.

## Proposed Hardware & Infrastructure Stack
1. **Core Compute:** ESP32 Microcontroller (embedded for local Edge AI processing and hardware logic)
2. **Sensors:** INMP441 Omnidirectional Microphone, Tactile Button, & GY-521 MPU-6050 (Inertial Measurement Unit)
3. **Connectivity:** SIM800L GSM/GPS Module for direct SMS emergency transmission
4. **Power Infrastructure:** 3.7V 1800mAh Li-Po battery pack managed via TP4056, a boost converter, and a custom IRF9540/2N7000 asynchronous power gate to eliminate continuous baseline draw
5. **Security:** Offline-first architecture. All acoustic validation is processed strictly on the Edge AI model without cloud audio streaming, securing user privacy and ensuring functionality in disconnected environments.

## Expected Architecture Flow
1. **Event:** A kinematic anomaly (monitored by the GY-521 MPU-6050 on a thigh strap) or a discrete tactile button press wakes the ESP32 microcontroller from deep sleep.
2. **Compute:** The ESP32 captures audio via the INMP441 MEMS microphone and processes it locally using a pre-trained Edge AI model to validate a specific distress wake-word, eliminating false positives with zero latency.
3. **Action:**  Upon successful voice authentication, the ESP32 triggers the custom IRF9540/2N7000 asynchronous power gate, instantly booting the isolated SIM800L GSM/GPS module from a zero-power state.
4. **Network:** The SIM800L acquires a location lock and covertly broadcasts precise GPS coordinates via direct SMS to emergency contacts, ensuring a highly reliable, offline-first survival pipeline without relying on continuous cloud connectivity.
