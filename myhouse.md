### System Profile: Primary Core Server (The Mainframe)
| Specification | Details |
|---|---|
| **Core Hardware** | Dell Precision 7910 Tower |
| **System Memory** | 32GB RAM |
| **Storage Array** | Dual 256GB SSDs (Drive 1: Dedicated "Rippled" environment; Drive 2: General storage & operations) |
| **Primary Role** | Heavy compute, local state management, memory integration, and backend routing |
### I. Cognitive & Processing Core
 * **Local Backend Operations:** Acts as the primary processing engine, handling incoming voice text and contextual triggers sent by Miss Pi to manage state without relying on external cloud latency.
 * **Asymmetric Data Processing:** Receives the transcribed rich_daily_context.json logs from Miss Pi. Runs routine distillation tasks to extract core preferences, updating the central behavior_lib.json file.
 * **Spatial Math Offloading:** Handles the heavy trigonometric calculations required to translate Miss Pi's raw X/Y/Z coordinate data into actionable WebGL camera movements, ensuring zero bottlenecking on the Raspberry Pi.
### II. State Management & Hosting
 * **Holodeck Asset Hosting:** Serves the localized WebGL assets, 3D models, and the Matrix dashboard UI out to the X17 Command Terminal.
 * **Global State Synchronization:** Maintains the master state of the living room UI. If Miss Pi triggers a "Tactical Hold" (amber standby), the server instantly pushes that state change to the X17's display.
 * **Secure Biometric Vault:** Houses the master facial recognition profiles and authorization tokens, keeping all physical security data strictly local.
### System Profile: Command Terminal (Alienware X17)
| Specification | Details |
|---|---|
| **Core Hardware** | Alienware X17 Laptop |
| **Compute & Graphics** | NVIDIA GeForce RTX 3080 Ti (16GB GDDR6 VRAM) |
| **System Memory** | 32GB RAM |
| **Primary Display** | 32-inch Alienware QD-OLED Monitor |
| **Primary Role** | High-fidelity WebGL rendering, primary operator dashboard, and manual override |
### I. Visual Operations & The Holodeck
 * **Matrix Dashboard Rendering:** Dedicates its massive 16GB VRAM payload to rendering the 3D WebGL spatial interface smoothly.
 * **Dynamic Z-Axis Scaling:** Seamlessly transitions the UI from a localized "Radar" view to a deep-focus "Pulse" view when the server relays proximity alerts.
 * **Visual Telemetry Display:** Provides the operator with real-time visual feedback on system health, open audio gates, and localized network traffic.
### II. Tactical Command & Override
 * **Hardline Administration:** The X17 maintains absolute physical control over the server environment.
 * **Development Sandbox:** Acts as the primary staging ground for the operator to write, test, and deploy new Python scripts, OpenCV modules, and UI updates before pushing them to the Dell 7910 or Miss Pi via SSH in VS-Code
### System Profile: Miss Pi (Tactical Co-Pilot)
| Specification | Details |
|---|---|
| **Core Hardware** | Raspberry Pi 5 |
| **Display Array** | 27" Dell monitor on an articulating arm + Freenove case OLED screen for micro-UI states |
| **Vision Array** | Dual-camera array enabling stereoscopic depth perception |
| **Audio Output** | USB Dell soundbar |
| **Primary Role** | Local UI coordination, voice processing, and spatial tracking bridge |
### I. Security & Sentry Protocols
 * **Passive Door Sentry:** Monitors the front door zone utilizing OpenCV background subtraction to detect motion.
 * **Silent Biometric Capture:** When an unrecognized person enters the frame, silently captures a high-resolution snapshot and logs a pending-identification event without interrupting the operator.
 * **Debrief & Address Book Updates:** Upon the operator's return, verbally debriefs the logged visitor. Once the operator verbally provides a name, permanently binds it to the facial profile in local storage for future recognition.
### II. Biometric & Spatial Gesture Controls
 * **Wake-Up Salute:** Detects a physical salute gesture from the operator to wake the system from monitor dark mode, triggering a welcome protocol with a soft system chime and an assertive salute animation.
 * **Z-Axis Proximity (Deep Focus):** Expands the holographic terminal overlay when the operator physically leans in close to the 27-inch monitor, and seamlessly returns the Holodeck to the idle state when the operator leans back.
 * **Desk Zone Hardware Token:** Tracks a physical object placed in a designated desk square, acting as a hard toggle switch to instantly shift UI states.
 * **Tactical Hold (Open Palm Interrupt):** Registers an open palm gesture to act as a physical "Global Mute." Pauses the text-to-speech engine and throws the UI into a deep-amber standby state until verbally cleared.
 * **Biometric Push-To-Talk (Throat Switch):** Tracks the back of the operator's fully extended hand hovering within a localized throat zone to open the software audio gate, utilizing a 2-second debounce timer to prevent accidental disconnections.
### III. 3D Spatial Air Mouse & Interface Navigation
 * **Smartphone Object Tracking:** Visually locks onto a paired smartphone held within a 3-foot spatial dome anchored to the operator's face.
 * **Line-of-Sight Latch:** Dynamically activates Air Mouse controls only when the phone physically intersects the straight line of sight between the operator's face and the camera.
 * **Spatial Translation:** Translates the phone's physical movements into X/Y panning and orbiting, utilizing stereoscopic depth mapping to control Z-axis zooming on the Matrix.
 * **The "Double Donk" Selection:** Monitors for specific forward velocity spikes on the Z-axis. Two rapid forward thrusts within a 300-millisecond window register as a spatial mouse click to select and isolate asset nodes.
### IV. Asymmetric Memory & Object Learning
 * **Asymmetric Data Distillation:** Transcribes and logs only the operator's side of conversations to a local log. This eliminates bloat by allowing the server to extract core facts and preferences.
 * **Proximity Object Learning:** Learns and tracks entirely new physical objects when held within a 36-inch radial search zone. Upon verbal command, captures the object's visual feature map, assigns an ID, and saves it for macro-key interactions.
### V. Tactical Audio-Visual Feedback
 * **OLED Expressions:** Utilizes the Freenove dedicated OLED screen to reflect system states, displaying wide, attentive eyes when listening, animated waveforms when speaking, and an amber standby icon during a tactical hold.
 * **Auditory Telemetry:** Provides instantaneous mechanical UI sounds via the Dell soundbar, including comm-badge chirps for open microphones, tricorder trills for successful scanning, and mechanical door swooshes for sentry alerts.
