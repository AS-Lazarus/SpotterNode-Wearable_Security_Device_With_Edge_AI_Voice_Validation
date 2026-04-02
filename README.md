# Sentinel: Wearable IoT Anti-Kidnapping System (Edge AI)

**Status:** System Design & Research Phase (Final Year EEE Thesis)

## Project Overview
A covert, wearable IoT security node disguised as a culturally ubiquitous neck ornament. Designed to bypass assailant scrutiny in high-risk zones, the system prioritizes a "Silent-First Protocol" to capture evidence and transmit real-time GPS coordinates under duress.

## Key Innovation: Algorithmic Gesture Trigger
Traditional panic buttons fail during a crisis because they require obvious, suspicious hand movements. This system utilizes a Non-Invasive Gestural Trigger based on the psychology of victimhood:

1. **The Mechanism:** An MPU-6050 IMU monitors cervical posture.

2. **The Trigger:** An Edge AI algorithm detects sustained cervical flexion (Chin-to-Chest "submission response" posture) of >45 degrees for 3 seconds.

3. **The Result:** Covert activation of the distress signal while the user appears entirely compliant.

## Proposed Hardware & Infrastructure Stack
1. **Core Compute:** Raspberry Pi Zero 2 W (embedded for Edge AI processing)
2. **Sensors:** MPU-6050 (Inertial Measurement Unit) & Pinhole Camera Module
3. **Connectivity:** GSM/LTE Module for 5-second cloud dashboard transmission
4. **Power Infrastructure:** Custom miniaturized Li-Po battery pack (applying CEID Hub/InnovateUK battery design principles)
5. **Security:** Data transmission pipeline secured using modern cloud cryptography standards.

## Expected Architecture Flow
1. **Event:** User enters sustained 45-degree cervical flexion for 3s.
2. **Compute:** Pi Zero processes IMU telemetry locally (Edge AI) to prevent latency.
3. **Action:** "Ghost Mode" initiates. Pinhole camera captures evidence.
4. **Network:** GSM/LTE module opens a secure connection and pushes JSON payload (GPS coordinates + media) to the cloud dashboard.
