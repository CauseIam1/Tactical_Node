# Tactical_Node

**![Bot Page](Screen.png)**

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

### A. COLD_WALLET_ADDRESS (Liquidity Foundation - AMM Pools)
 * **Role:** The institutional vault and primary liquidity engine.
 * **Function:** Exclusive creator and deployer of private AMM pools; holds foundational LP tokens.
 * **Constraint:** Strictly isolated; never interacts with live trading engines and requires no hot-key access.

### B. MPT_RPN_WALLET_ADDRESS (Bot Page - ALL Trading Bot Controls on remain on this page)
 * **Role:** Programmatic hot wallet for the automated 24/7 execution engine.
 * **Function:1** Executes cumulative pile "flip-flops" across our asset pools
 * **Function:2** Executes The "Splash and Strike" Sequence (described below)
 * **Function:3** Executes rapid, multi-hop mesh network arbitrage to capture micro-inefficiencies and generate passive yield.
 * **Constraint:** Strictly rules-based execution governed by liquidity guardrails; operates with a hard-capped capital allocation to prevent broader portfolio exposure.

### C. TRADING_WALLET_ADDRESS (Radar Page - Copy of Bot Page but Controls manual swap Nodes)
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
### Interactive "Stellar Cartography" Mechanics
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
Since XRP is our baseline bedrock and we measure the "global displacement mass" purely in xrp_equivalent, the visual size of our ecosystem should be driven by the actual, mathematical weight of the assets, not a hardcoded ratio (Except Active Nodes which are hardcoded in size only).
### Unified Architecture, Distinct Atmospheres & Universal Node Identity
To ensure maximum component reusability without sacrificing situational awareness, build a single, modular Node3D and 3DCanvas component that accepts a theme prop. 
**1. Universal Node Identity (The Hex-to-Color Engine)**
 * **Idle / Base State:** All idle asset nodes derive their color strictly from a deterministic Hex-to-Color algorithm based on their unique XRPL currency code. This ensures every whitelisted asset (e.g., meme coins) retains a permanent, universal visual identity across all modules (Radar, Bot, and Matrix), building instant operator muscle memory. 
 * **The Anchor:** XRP is permanently hardcoded to Canonical Blue (#00A8FF) as the ecosystem's core gravity well.
**2. Action States (Universal Muscle Memory)**
 * The core tactical states dynamically override the node's base hex color: Vibrant Green for **Expanding**, Flashing White/Cyan for **Apex**, Warning Orange for **Compression**, and Tactical Magenta for **Override/Manual**.
**3. Unified Ambient Atmospheres (The "Visual Twin" Architecture)**
To embrace DRY principles and maintain a premium visual standard, the Bot Page and Radar Page function as exact visual clones. Both utilize the same high-fidelity 3D aesthetic and node animations. The context of the operator's viewport is determined entirely by the routing and the isolated data streams for the active nodes:
 * **Matrix Page (The Vault):** Deep XRP Blues (#00A8FF) and stark Silvers. Represents cold, hard structural mass.
 * **Bot Page & Radar Page (The Active Decks):** Both share a unified, premium visual identity (e.g., The Bioluminescent Pond aesthetic). They are exact UI clones, with the Bot Page strictly rendering the programmatic hot wallet's active nodes, and the Radar Page strictly rendering the manual Xaman wallet's sniper nodes. 

### Bot Page & Radar Page (The Visual Twins - Radar is twin of Bot but for manual snipe nodes instead of mpt nodes)
#### 1. Objective & Core Paradigm
Both pages serve as full-fledged **Tactical Command Decks**. They adhere strictly to the "viewport" philosophy, utilizing identical 3D glassmorphic interfaces and node architectures to track **asset-to-asset relative exchange ratios**. 
The fundamental rule of this architecture is strict data isolation:
* **The Bot Page Route:** Feeds strictly from the Bot's `r-address` (via the `amm_balances` QuestDB table) to visualize automated, 24/7 ecosystem health.
* **The Radar Page Route:** Feeds strictly from the Manual Trading `r-address` (via the `trading_balances` QuestDB table) to visualize manual Human-In-The-Loop momentum targets.
#### 2. Layout & Control Architecture (Perimeter HUD)
Both pages utilize the exact same structural layout to keep the central 3D canvas completely unobstructed, but have different left and right panels for both pages as they will be controlling different wallets: 
(LeftHudPanel, LeftHudPanel_R, RightHudPanel, RightHudPanel_R, StatusBar and StatusBar_R)
 * **Left Panel (The Tactical Dials):** Houses system sliders, spacing configurations, and visual force-field thresholds. 
 * **Right Panel (Injection Console):** Houses the manual override tools / Swap Injection, asset selection, and execution switches.
 * **Center Stage (The Bioluminescent Pond):** The viewport is a full-screen, unobstructed 3D canvas displaying the tactical nodes in their deterministically generated hex-seed colors.
#### 3. Data Integration & State Mapping
The unified frontend hooks into the dynamic 60-ledger window ratio tracking streams, mapping the exact same visual states regardless of which wallet is being viewed:
 * **Outside Watch Zone (Universal Hex Color):** Exchange rate is below the HOT zone threshold. Nodes idle in their deterministically generated base color.
 * **Expanding (Vibrant Green Blip):** Exchange rate is actively widening; accumulating unrealized asset volume potential.
 * **Apex (Flashing White / Cyan):** Exchange rate expansion has flattened at its local maximum. Maximum swap yield is active.
 * **Compression (Warning Orange Flashing):** Ratio prints its first confirmed down-tick from the peak. The reverse swap window is open.

## Live Telemetry & QuestDB Schema Bridge
To eliminate all mock data and drive the 3D canvas with live production metrics, the frontend telemetry endpoints must query QuestDB using `LATEST BY` time-series collapses:
### Data-to-UI Mapping Table
| UI Module / Target | QuestDB Table | SQL Query | Visual Engine Mapping |
| :--- | :--- | :--- | :--- |
| **Bot Page (3D Ring)** | `amm_balances` | `SELECT * FROM amm_balances LATEST BY currency, capital_partition;` | Drives **True-Mass logarithmic scaling** and feeds currency codes into the **Hex-to-Color algorithm**. |
| **Bot Page (Engine States)** | `mpt_state_snapshot` | `SELECT * FROM mpt_state_snapshot LATEST BY pair_key;` | Triggers **Expanding (Green)**, **Apex (White)**, and **Compression (Orange)** visual overrides + tracer lines. |
| **Radar Page (Manual Swaps)** | `trading_balances` | `SELECT * FROM trading_balances LATEST BY asset;` | Isolates current manual wallet positions to render active sniper nodes. |
| **Matrix & Pulse HUDs** | `xrp_stack_snapshots` | `SELECT * FROM xrp_stack_snapshots ORDER BY timestamp DESC LIMIT 1;` | Feeds the **80/20 Redline visualizer** and proportion models across Cold, Trading, and Bot wallets. |
**Developer Implementation Note:** All live balance updates must use standard `LATEST BY` state collapses to ensure historical snapshot rows do not duplicate active 3D nodes.


#### Matrix Page (The Living Organism / Asset Pile Console)
### The visual Page of all wallet balances viewed in 3D Graphical view.
* **Matrix Page of Dashboard:** (Asset-pile) The aggregate view. These page synthesize the combined telemetry of the Cold Wallet, Trading Bot Wallet, and Manual Trading Wallet to provide a holistic measure of the total ecosystem "The Organism"
#### 1. Objective & Core Paradigm
The Matrix Page (Asset Pile Console) completely reimagines static asset data grids as a kinetic, biomechanical "living organism" ecosystem that leverages local GPU rendering capabilities. Instead of isolating token pairs in rigid, unreadable raw-text rows, all whitelisted assets are treated as floating, interdependent visual nodes within a shared mesh network. This layout provides an immediate, instinctual view of the system's central nervous system, visualizing real-time capital flow, multi-hop routing, and asset depth without text clutter.
#### 2. Visual Topography & Kinetic Event Streams
 * **The Mesh Network:** Built utilizing React Three Fiber, individual assets drift and hover as floating graphical nodes. The visual density and physical proximity of nodes reflect their current liquidity scaling and active network relationships.
 * **Biomechanical Tracers (The Live Tape):** Raw market transactions are translated into immediate particle emissions across the canvas. Asset-to-asset multi-hop execution fires kinetic energy pulse vectors traveling from the source node to the target node.
 * **Dynamic Sizing & Bounding Spheres:** Node volume and scaling are driven by the Adaptive Liquidity Scaling engine. Capital partitions are bound by dynamic geometric spheres, instantly visualizing the 80/20 split between core operational capital and sidelined assets.
#### 3. State Coloration & Ambient HUD Mechanics
The entire page operates in an ACTIVE_IDLE state by default, shrinking text data away until explicitly engaged. System health is communicated through ambient color pulses across the node cluster:
 * **Emerald Tracers / Pulses:** Active BUY actions or successful execution events pulse green across the corresponding node pathways.
 * **Red Tracers / Pulses:** Active SELL actions, SKIP flags, or engine CLAMP events radiate a warning red pulse down the asset network path.
 * **Amber Overrides:** When manual deviations or dry-run simulations are actively injected into the system, affected nodes and control modules emit a localized amber glow.
#### 4. Interaction Architecture: Focus Zoom Isolation
To preserve cognitive clarity and maximize visual efficiency, all deep-level technical metrics are hidden behind a strict click-to-expand data hierarchy.
 * **The Ambient Overlay:** Hovering over an asset node gently reveals its real-time relative token velocity and tracking state.
 * **Holographic Node Expansion:** Clicking directly on a specific asset node freezes ambient movement and expands the node into a comprehensive holographic terminal overlay. This panel brings forward critical data including exact net volume, transaction histories, and active guardrails (such as MINIMUM_POOL_DEPTH_XRP metrics).
 * **Tactile Engine Controls:** The interface incorporates 3D kinetic dials and throttle sliders to manage simulated overrides and stress tests, converting standard flat HTML inputs into highly responsive, tactile objects.



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


Other files of references
tradingbot.md
BotPage.md 
RadarPage.md
MatrixPage.md
PulsePage.md
CommsPage.md
