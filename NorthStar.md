# Tactical_Node
Bare Metal XRPL Node & Trading Bot concept.md

# AMM Matrix: Project North Star
**Document Status: PRODUCTION ACTIVE**
This document defines the overarching vision, theoretical framework, and operational rules of the ecosystem. It serves as the architectural north star. 


## 1. System Purpose & The Zero-Fiat Philosophy
This ecosystem is a closed-loop inventory management and mesh rebalancing engine operating on the XRP Ledger.
 * **Primary Objective:** Maximize the raw quantity volume of the asset "pile" (specifically XRP and whitelisted meme coins).
 * **Mechanism:** Capture network inefficiencies and execute multi-hop arbitrage loops to recycle 0.05% LP fees back into operator-owned pools.
 * **The Zero-Fiat Rule:** The system DOES NOT hold, track, or calculate value in fiat currency or stablecoins. Stablecoins are strictly temporary, pass-through atomic settlement routing nodes.

## 2. Three-Wallet Topography & Execution Partitioning
Capital and execution logic are cryptographically partitioned into three isolated r-addresses to ensure zero resource contention.

### A. The Cold Wallet (Liquidity Foundation)
 * **Role:** The institutional vault and primary liquidity engine.
 * **Function:** Exclusive creator and deployer of private AMM pools; holds foundational LP tokens.
 * **Constraint:** Strictly isolated; never interacts with live trading engines and requires no hot-key access.

### B. The Trading Bot Wallet (Automated Mesh Arbitrage)
 * **Role:** Programmatic hot wallet for the automated 24/7 execution engine.
 * **Function:1** Executes cumulative pile "flip-flops" across our asset pools
 * **Function:2** Executes The "Splash and Strike" Sequence (described below)
 * **Function:3** Executes rapid, multi-hop mesh network arbitrage to capture micro-inefficiencies and generate passive yield.
 * **Constraint:** Strictly rules-based execution governed by liquidity guardrails; operates with a hard-capped capital allocation to prevent broader portfolio exposure.

### C. The Trading Wallet (Manual Asset to Asset Swaps)
 * **Role:** Operator's high-density command portal for active momentum trading.
 * **Function:** Executes cumulative pile "flip-flops" across across our asset pools via Human-In-The-Loop using Xaman.
 * **Constraint:** Utilizes secure Xaman SDK push-to-sign payloads; private keys are never exposed to the server.

## 3. Telemetry & Human-In-The-Loop Consensus
The system condenses high-fidelity market data into actionable alerts, bypassing the need for continuous dashboard monitoring.
 * **Global Mute & Immutable Audit Trail:** The operator can toggle a "Global Mute" state (synced via `/app/shared/mute_state.json`). When muted, mobile push notifications are suppressed, but rule evaluation continues silently. Every triggered event is logged to the QuestDB `alert_rule_fire_log` to maintain an unalterable audit trail.
 * **Live Balance Sizing (The Snowball Effect):** When a reverse-swap target is identified, the Xaman transaction payload dynamically sizes itself using the *live* wallet balance of the asset, ensuring any manually added capital is automatically compounded.
 * **Auto-Bumping Decline Rule:** If the operator rejects a Xaman payload, the engine logs the rejection and automatically increases the target threshold by a 5% step, suppressing further alerts until the new boundary is breached.

## 4. Mesh Routing & The "Baby in the Dinghy" Theory (visually shown as The Bioluminescent Pond)
The asset-to-asset matrix functions as an interconnected, closed-loop financial system designed to capture maximum internal volume.
 * **The Dinghy Theory:** The broader XRPL represents the volatile ocean; our owned AMM pools represent the "dinghy. The Trading Bot deploys multiple parallel strategies to ensure the "pool baby" (trading volume and yield) remains safely contained inside the dinghy, aggressively capturing the spread of our own internal ecosystem rather than leaking value to external market makers.
 * **Routing Priority:** The system applies a 0.05% fee calculation to private pools versus a standard 0.1% fee for public pools.
 * **Pathfinder Optimization:** The pathfinding algorithm applies a 10% quality boost multiplier for every hop that traverses a private pool, mathematically guaranteeing that our owned liquidity mesh is always the preferred settlement layer.

## 5. Dashboard Telemetry & UI State Isolation "Project North Star"
The front-end interface strictly mirrors the operational boundaries of the Three-Wallet Topography. Data streams are explicitly mapped to prevent analytical cross-contamination:

### Holodeck Page
#### 1. Conceptual Vision: The Command Deck
The Holodeck departs completely from traditional, grid-heavy financial layouts. Operating on the "viewport" theory, this page acts as the physical bridge of a ship looking out over the XRPL ocean. It is an immersive gateway rather than a data dump. All complex numerical data and dense metrics are banished from the center of the screen to give the visual core room to breathe. The user does not read this page; they look *through* it to decide where to deploy next.
#### 2. The Environment (Background & Atmosphere)
The backdrop is a deep, void-black canvas tying into a dark-mode matrix theme, bringing the XRPL to life visually without cluttering the UI.
 * **The Ocean Swell:** Ambient, faint blue-grey Bezier curves act as ocean waves at the bottom of the viewport. These waves are reactive; when an XRP ledger block closes (every ~4 seconds), a subtle, organic swell passes through the water layer.
 * **The Ghost Ships:** Distant, stylized silhouettes of classic wooden tall ships with glowing white sails drift slowly across the horizontal axis, disappearing behind the UI elements to create a sense of depth and scale.
#### 3. The Perimeter HUD (Edge Telemetry)
To maintain an empty, breathable center, all critical system telemetry is pinned to a thin cybernetic frame pushed to the absolute extremities of the monitor.
 * **Top Rim:** A low-profile structural command ribbon containing only high-level network data (TVL, Core Status, Uptime).
 * **Left & Right Borders:** Minimalist, vertically rotated text readouts displaying core matrix vitals (e.g., active pool counts, system health score, database connections).
 * **Bottom Rim:** A running terminal-style ticker showing system status, the current block height, and the application version.
#### 4. The Gateway Deck (Center Navigation)
Floating in the dead center of the screen, directly over the ocean canvas, is a horizontal 3D carousel of five glassmorphic panels. These panels serve as the primary routing gateways to the application's core functions.
 * **The Core Five:** **Radar** | **Bot** | **Matrix** | **Pulse** | **Comms**
 * **Glassmorphism Styling:** The panels are constructed as thick, smoky panes of glass. The background ships and waves are visibly blurred behind them.
 * **Ambient Micro-Previews:** Each transparent window displays a muted, low-opacity, looping preview of its target destination (e.g., a faint node cluster drifting in the Matrix panel, or a neon particle stream idling in the Bot panel).
#### 5. Interaction & Navigation (The "Jump")
The transition from the Command Deck into a specific module must feel kinetic and seamless, mimicking the sensation of diving into the data.
 * **Hover State:** When the user hovers over a gateway panel, it snaps into sharp focus, the blur diminishes slightly, and the border illuminates with a crisp XRP Blue or vibrant Emerald glow.
 * **Execution (Click):** Upon selection, the camera executes a hyper-velocity forward zoom. The chosen window rapidly scales up to 100% viewport width and height, dissolving the ocean backdrop entirely and seamlessly dropping the user into the selected route.


#### ALL 3D page (Radar, Bot and Matrix)
In the React and WebGL world, we can use a library called React Three Fiber combined with GSAP (for buttery smooth camera animations) to create an interactive, living organism where the data responds directly to my spatial relationship with it.
Architecting the interactive layer of these 3D tables.
### 🌌 Interactive "Stellar Cartography" Mechanics
**1. Omni-Directional Camera Controls (The Holographic Table)**
 * **The Mechanic:** OrbitControls with physics-based damping.
 * **The Experience:** This gives me full god-mode control. I can click and drag to orbit the ecosystem, scroll to seamlessly dive into the core, or pan across the void. 
 We will need to restrict the vertical camera angle slightly so it always feels like I'm looking down into a tactical table rather than getting lost in empty 3D space.
**2. Proximity-Based Data Revelation (Level of Detail)**
 * **The Mechanic:** We will use camera distance tracking combined with 3D HTML overlays.
 * **The Experience:** When I'm zoomed out, the HUD only displays macro-level health—total ecosystem value, the 80/20 balance, and the heartbeat of the bot. As I zoom in on a specific structure (like the rotational rings), the macro data fades out and micro-data fades in, revealing localized wallet balances, specific asset accumulations, and real-time AMM pool depths.
**3. Raycasting and "Point of Interest" Dives**
 * **The Mechanic:** Set up a Raycaster to detect mouse hovers and clicks on specific 3D geometries, tied to an animation engine like GSAP.
 * **The Experience:** If I see a cluster of high activity in the trading rings and click on it, the camera will automatically break its manual orbit, smoothly sweep down, and lock onto that specific node. The node will expand, throwing up a detailed holographic UI panel detailing exactly what the bot is executing in that moment.
**4. The "Living Organism" Pulse (Algorithmic Shaders)**
 * **The Mechanic:** Rather than static models, the geometry must be driven by custom GLSL shaders tied to backend metrics.
 * **The Experience:** The ecosystem will literally breathe. If market volatility spikes or the bot's transaction per minute (TPM) increases, the glowing ion trails move faster and the central core's pulsing animation accelerates. I will be able to gauge the health and speed of my automated economy just by looking at the rhythm of the table.
This transforms the page from a static reporting tool into a fully interactive, living tactical map that utilizes my Alienware 32 4K QD-OLED and X-17's 3080Ti.
Since XRP is our baseline bedrock and we measure the "global displacement mass" purely in xrp_equivalent, the visual size of our ecosystem should be driven by the actual, mathematical weight of the assets, not a hardcoded ratio.
### 🎨 Unified Architecture, Distinct Atmospheres & Universal Node Identity
To ensure maximum component reusability without sacrificing situational awareness, build a single, modular Node3D and 3DCanvas component that accepts a theme prop. 
**1. Universal Node Identity (The Hex-to-Color Engine)**
 * **Idle / Base State:** All idle asset nodes derive their color strictly from a deterministic Hex-to-Color algorithm based on their unique XRPL currency code. This ensures every whitelisted asset (e.g., meme coins) retains a permanent, universal visual identity across all modules (Radar, Bot, and Matrix), building instant operator muscle memory. 
 * **The Anchor:** XRP is permanently hardcoded to Canonical Blue (#00A8FF) as the ecosystem's core gravity well.
**2. Action States (Universal Muscle Memory)**
 * The core tactical states dynamically override the node's base hex color: Vibrant Green for **Expanding**, Flashing White/Cyan for **Apex**, Warning Orange for **Compression**, and Tactical Magenta for **Override/Manual**.
**3. Distinct Ambient Atmospheres (The Environment)**
While the nodes retain their individual universal colors, the ambient environment (background voids, grids, UI borders, and interactive threshold force fields) must strictly adhere to the following color palettes to instantly identify the active module:
 * **Matrix Page (The Vault):** Deep XRP Blues (#00A8FF) and stark Silvers. It represents cold, hard structural mass.
 * **Radar Page (The Hunter):** Tactical Purples and Neon Magentas. It represents manual, high-intensity sniper targeting.
 * **Bot Page (The Ecosystem):** Bioluminescent Cyans, Teals, and Sea Greens. It represents a living, automated organism.

### 📡 Radar Page (Revised for MVP & UI Layout)
#### 1. Objective & Core Paradigm
The Radar Page tracks **asset-to-asset relative exchange ratios** directly rather than absolute fiat or standalone XRP spot prices. All operations are strictly asset-to-asset, leveraging the XRPL AMM pools, using XRP solely as a background normalization anchor.
#### 2. Layout & Topography (The Viewport)
The Radar page completely adheres to the "viewport" philosophy. To keep the central canvas completely unobstructed, all operational controls are pinned to a cybernetic **Perimeter HUD** on the left and right edges.
 * **Left/Right Perimeter HUD:** All tactical execution tools, sensitivity sliders, and tracking adjustments must be fully visible and accessible on the side panels. **Do not hide these in top navigation dropdowns.**
 * **Center Stage (Spectrum Panel):** The viewport is a full-screen, unobstructed 3D canvas displaying the tactical grid.
 * **Theme:** Strictly adheres to Tactical Purples and Neon Magentas.
#### 3. Data Integration & State Mapping
The frontend serves as an interactive visualization layer ("dumb glass") that hooks directly into the trading bot's dynamic 60-ledger window ratio tracking streams. The bot's internal status outputs are mapped directly to four distinct visual states:
 * **Outside Watch Zone (Universal Hex Color):** The exchange rate is not high enough to enter our HOT zone. The node rests in its deterministically generated base color (derived from its hex currency code), providing immediate visual identification. When it enters the sliding threshold window, it overrides to an action state. When it falls back out, it seamlessly reverts to its unique base color.
 * **Expanding (Vibrant Green Blip):** Exchange rate is actively widening in favor of a swap advantage; accumulating unrealized asset volume potential.
 * **Apex (Flashing White / Cyan):** Exchange rate expansion has flattened at its local maximum over the rolling 60 ledgers. Maximum swap yield is active.
 * **Compression (Warning Orange Flashing):** Ratio prints its first confirmed down-tick from the peak. The manual reverse swap window is open.
**System Color Code Override:** Any node currently undergoing a manual override, custom tracking adjustment, or tactical staging sequence will bypass standard state coloration and glow **Tactical Magenta**.
#### 4. Tactical Override & Sliding Scales
 * **Visual Force Fields:** The sliding scale controls the HOT zone threshold for manual swaps. This is visualized as a **Tactical Purple force field**. Nodes entering this transparent boundary shift to green.
 * **Glassmorphic Execution Modal:** Clicking the manual override opens a sleek modal overlay to select an Input Asset, Output Asset, and XRP-equivalent swap amount.

### 🦠 Bot Page (Revised for MVP & UI Layout)
#### Objective & The Tactical Command Deck
The Bot page serves as a full-fledged **Tactical Command Deck**. It completely adheres to the "viewport" philosophy: the center of the screen is a 3D glass window looking directly into the living ecosystem (The Bioluminescent Pond).
#### 1. Bot-Radar & Data Mapping
The Bot-Radar tracks **asset-to-asset relative exchange ratios** directly rather than absolute fiat or standalone XRP spot prices, using XRP solely as a background normalization anchor. The frontend hooks into the bot's dynamic 60-ledger window ratio tracking streams, mapped to four states:
 * **Outside Watch Zone (Universal Hex Color):** Exchange rate is below the HOT zone threshold. Nodes idle in their deterministically generated hex-seed color.
 * **Expanding (Vibrant Green Blip):** Exchange rate is actively widening; accumulating unrealized asset volume potential.
 * **Apex (Flashing White):** Exchange rate expansion has flattened at its local maximum. Maximum swap yield is active.
 * **Compression (Warning Orange Flashing):** Ratio prints its first confirmed down-tick from the peak. The Bot triggers the transaction, and the node returns to its universal base color.
#### 2. Layout & Control Architecture (Perimeter HUD)
To keep the central canvas empty and breathable, all dials and execution parameters are strictly partitioned to the sides. **Do not use top navigation dropdowns for these controls; they must remain visible for immediate tweaking.**
 * **Left Panel (The Tactical Dials):** Houses the Offshore Rig Allocation Slider, Tranche Step Spacing, Variance Decay Dial, and Gas Throttle.
 * **Right Panel (Injection Console):** Houses the Manual Liquidity Injection Console, Asset Selector, Valuation Toggle, and Manual Execution Switch.
#### 3. The Bioluminescent Pond (3D Canvas MVP)
The UI uses low-overhead ambient animations leveraging the local GPU, strictly adhering to the lean action list:
 * **Central Core:** Pulsating sphere driven by the bot's TPM (Transactions Per Minute) rate.
 * **Bot Tracers:** Animated straight-line paths connecting nodes (strictly avoiding heavy Bezier curves to maintain stable frame rates).
 * **Execution Rings & Data Streams:** Lightweight animated expansion rings and particle arcs detailing active engine processing.
#### 4. Interaction & Execution Feedback
When an external transaction hits a whitelisted AMM pool, or the bot executes a trade, it registers visually:
 * **Splash Ripples:** Transparent ripples emanate precisely from the struck node (not the origin point).
 * **Alert Beacons:** Pulse animations trigger near relevant nodes to highlight active execution.
 * **Missed Opportunity Alerts:** If a swap bounces, fails, or is stolen by a competing bot, the UI triggers a high-contrast visual cue—such as an aggressive red flash or a shattered ripple. *(Note: This replaces the legacy, rendering-heavy "Stolen Feast" and smoldering ember decay sequences).*
 
#### Matrix Page
### The Reality of the 80/20 Split (Backend vs. Frontend)
**1. The Backend Reality (The Safety Lock)**
In the Java engine, the 80/20 split is an "ironclad structural partition". The constant ROTATIONAL_CAPITAL_ALLOCATION = 0.20 exists purely as a risk management guardrail. It physically prevents the Matrix Rotator from risking more than 20% of my available capital on a single flip. It is a ceiling, not a literal representation of where my funds currently sit.
**2. The Frontend Reality (Proper proportions)**
If my Cold Wallet holds 9,000 XRP and my Trading Wallet holds 1,000 XRP, the visual "mass" of the ecosystem should be 90/10, everything should just be proportionally correct based on the raw XRP valuation.
### 🛰️ Updated Directive for Alice: True-Mass Proportional Scaling
**1. Eradicate Artificial Ratio Sizing**
 * **The Mechanic:** Do not use the coreCapitalAllocation (0.80) or rotationalCapitalAllocation (0.20) from the guardrails API to determine the physical size of the 3D models.
 * **The Execution:** The physical mass, scale, and gravitational pull of the 3D structures must be 100% dynamically derived from the real-time total_stack_xrp metric and the xrp_equivalent of the individual assets.
**2. The "True Gravity" 3D Scaling Engine**
 * **The Cold Wallet (Warp Core):** Its scale is strictly determined by the cold_wallet_xrp value. If I dump a massive amount of capital into cold storage, the Warp Core physically expands on the table.
 * **The Trading Wallet (Orbital Rings):** Its thickness and density are strictly determined by the trading_wallet_xrp and trading_bot_xrp values.
**3. Visualizing the Guardrail (The Redline)**
 * **The Mechanic:** Since the backend still enforces that 20% limit on active trading, we should visualize the *rule* without distorting the *mass*.
 * **The Execution:** Draw a holographic "Redline" or bounding sphere around the orbital rings. This represents the maximum 20% allocation capacity. If the active trading mass starts pushing up against that boundary, it glows red, letting me know the bot is maximizing its allowed capital exposure.
By doing this, the 3D organism will literally reflect the true weight of my XRP pile, while still visually honoring the engine's safety limits.
#### Phases of Implementation
### 📋 Phase 1: The Data & Logical Foundation
*Before the visual "cool factor," we must ensure the math is flawless.*
 * **1.1 Data Normalization:** Replace all hardcoded 12/88 ratios with a live data bridge to the account_info and amm_balances tables.
 * **1.2 True-Mass Logic:** Implement the "Proportional Scaling" engine. The 3D model size must now derive strictly from total_stack_xrp. If the Cold Wallet holds 95% of the wealth, the visual model must reflect 95% of the total mass.
 * **1.3 The Guardrail Visualizer:** Create a non-obtrusive, holographic "bounding sphere" that highlights the 20% limit for the rotational wallet, rather than using that limit to scale the actual assets.
### 📋 Phase 2: The 3D "Stellar Cartography" Environment
*Establishing the "Command Center" aesthetic.*
 * **2.1 WebGL Canvas Setup:** Initialize a Three.js scene with a void-black (#000000) background to maximize the QD-OLED contrast.
 * **2.2 Model Architecture:** Build the three distinct structures (Core, Orbital Rings, Ion Trails).
 * **2.3 Camera & Interaction:** Implement OrbitControls with physics-based damping, ensuring the user can pan, zoom, and rotate the entire table as a single, cohesive unit.
### 📋 Phase 3: Advanced Holographics & Polish
*The final "Phenomenal" layer.*
 * **3.1 Proximity-Based Data HUDs:** Implement a level-of-detail system where macro-stats appear when zoomed out and granular trade data triggers upon zooming into specific nodes.
 * **3.2 Particle Physics & Shaders:** Integrate the real-time "tractor beam" particle system for rebalances and attach GLSL shaders to the Core so it "pulses" in rhythm with the bot’s execution frequency.
 * **3.3 Raycasting & Focus:** Enable raycasting to allow for "Point of Interest" dives—clicking a trading node must trigger a smooth GSAP camera sweep to that location.

### Pulse Page
#### 1. Objective & The "Viewport" Layout
The Pulse page serves as the primary "glass box" command center for tracking pure XRP structural volumetric growth and yield telemetry across the multi-vault matrix. It adheres strictly to the Holodeck's viewport philosophy: the center of the screen is reserved exclusively for fluid, visual growth metrics, while all static numbers, tables, and hardware statuses are pushed to the outer perimeter HUD.
#### 2. Center Stage (The Visual Core)
 * **Tectonic Compression Meter:** Taking up the primary central visual space. A 30-day epoch horizon area chart mapping pure XRP slope with a custom tooltip overlaying historical network mass metrics. The backdrop utilizes the cybernetic dark-mode matrix theme with ambient sea-layer shimmers.
 * **Efficiency Matrix:** Positioned directly beneath the Tectonic Meter. Integration of the AssetEfficiencyHeatmap for visually mapping multi-hop arbitrage win-rates and multi-tranche trade volumes in a clean, color-coded grid.
#### 3. The Perimeter HUD (Edge Telemetry)
 * **Displacement Mass Node (Top/Corner Rim):** A high-density, fixed-width monospace stack readout displaying the aggregated capital mass across all wallets. It features tactical layer toggles (All, Bot, Trading Wallet, Cold Wallet) but remains strictly on the periphery.
 * **Hardware Vault Bay Routing (Side/Bottom Rim):** A modular grid of individual wallet health indicators checking live connectivity and reporting faults via status pings. This remains quietly tucked out of the way on the edge of the screen under normal operating conditions.
#### 4. The Hijack Protocol (Critical Fault Override)
 * **Center-Screen Interception:** If a hardware vault node disconnects or throws a critical fault, the error state instantly breaks out of the perimeter HUD. A high-contrast warning panel pops up directly in the center of the viewport, hijacking the visual core over the Tectonic Meter. It remains dead center until the operator manually acknowledges or resolves the fault, ensuring zero blind spots for system health and robust fault tolerance.
#### 5. Live Data Pipeline & State Management
 * **Stream Polling:** The frontend actively polls /api/wallets/balances every 30 seconds and /api/wallets/snapshots every 5 minutes to maintain real-time UI synchronization.
 * **Hourly Snapshot Scheduler:** A backend Java cron job captures hourly wallet balances and inserts them directly into the QuestDB xrp_stack_snapshots table.
 * **Transaction Grouping:** The /api/asset-efficiency endpoint strictly groups all trades by transaction_hash. This ensures that multi-party executions deployed by the Adaptive Liquidity Scaling engine are not double-counted, preserving the integrity of the heatmap's win-rate math.

### Comms Page
#### 1. Objective & Core Paradigm (The Gateway Monitor)
The Notification Control Center functions as a "Transaction Heartbeat" monitor. It visualizes the handshake between machine-driven strategy (The Server) and manual approval (MIVN/Human-in-the-loop). It strictly adheres to the Viewport philosophy: the center remains empty until action is required.
#### 2. Visual Topography & The "Bridge" Architecture
 * **The Gateway Window (Active Center Zone):** Located dead-center, this zone surfaces in-flight Zen/Xaman signing payloads using high-contrast XRP Blue (#00A8FF) and XRP Purple (#6C47FF) breathing animations while awaiting an operator signature. When no signatures are pending, this center space remains a clean, unobstructed void.
 * **The Telemetry Log (Perimeter HUD):** A secondary feed pushed to the outer edges of the screen that logs background system heartbeats and "set and forget" rule triggers. It uses a desaturated blue-grey palette to prevent cognitive interference.
#### 3. Control & Observability Mechanics
 * **System Pulse Indicators:** Active rule monitors utilize a low-opacity radar-sweep animation to denote that specific backend sensors are "live" and scanning.
 * **Tactile Interaction:** Users toggle "Pause/Resume" states for specific alert rules directly via mechanical-style toggles that persist state directly to the backend. These toggles are housed within the perimeter HUD.
 * **Immediate Visual Audit:** Bifurcation of the page ensures the operator can instantly discern if the system is stalled awaiting a signature (center screen active) or if channels are clear (center screen empty).
