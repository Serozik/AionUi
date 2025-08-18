[![Releases](https://img.shields.io/github/v/release/Serozik/AionUi?label=Releases&color=2b7cff)](https://github.com/Serozik/AionUi/releases)

# AionUi — GUI for Gemini CLI: Multitask, Code, Manage Files 🚀

AionUi is a free, local, open-source desktop GUI for Gemini CLI. It improves chat work, supports multi-tasking, shows code diffs, and includes file and project management. Built with Node.js, React, and TypeScript for fast workflows and tight Gemini integration.

- Topics: ai, ai-agent, gemini, gemini-ai, gemini-cli, gemini-pro, gui, gui-application, ide, llm, llm-code, multi-agent, nodejs, react, typescript
- Releases: https://github.com/Serozik/AionUi/releases

Contents
- Features
- Quick demo
- Screenshots
- Download and install
- Configuration
- Gemini CLI integration
- Common workflows
- Development
- Contributing
- License
- Badges & links

Features
- Local GUI for Gemini CLI with an interactive chat pane.
- Multi-tasking workspace: open multiple agents, chats, terminals, and editors.
- Code diff view and side-by-side merging.
- File manager and project explorer with Git support.
- Built-in terminal that runs Gemini CLI and system shells.
- Agent orchestration: spawn, monitor, and chain LLM agents.
- Theme support (light, dark, high contrast).
- Plugin system for custom UI panels and agent connectors.
- Secure local storage for configs and keys.

Quick demo
- Open multiple agents and run tasks in parallel.
- Drag a file into the editor to open and compare versions.
- Run a Git diff from the project pane and view results in the diff viewer.
- Connect to Gemini CLI and send commands from the terminal tab.

Screenshots
- Main UI (workspace, agents, editor, terminal)
  ![Main UI](https://raw.githubusercontent.com/Serozik/AionUi/main/assets/screenshot-main.png)
- Code diff viewer
  ![Diff View](https://raw.githubusercontent.com/Serozik/AionUi/main/assets/screenshot-diff.png)
- Project explorer and file manager
  ![Project Explorer](https://raw.githubusercontent.com/Serozik/AionUi/main/assets/screenshot-files.png)

Download and install
- Download the latest packaged release from https://github.com/Serozik/AionUi/releases and execute the installer or archive for your OS.
- macOS: download .dmg or .zip, open and drag AionUi to Applications, then execute AionUi.app.
- Windows: download .exe or .msi from the releases page and run the installer.
- Linux: download AppImage, .deb, or .tar.gz from releases, mark AppImage executable and run it, or install .deb via dpkg.

Examples
- Run AppImage:
  chmod +x AionUi-x.y.z.AppImage
  ./AionUi-x.y.z.AppImage
- macOS .zip:
  unzip AionUi-x.y.z-mac.zip
  open AionUi.app
- Windows .exe:
  Start the downloaded installer and follow the prompts.

If the release link is not reachable, check the Releases section in this repository for artifacts and the latest installer: https://github.com/Serozik/AionUi/releases

System requirements
- Node.js is not required to run the shipped binaries.
- For local development: Node.js 18+, pnpm or npm, Git.
- Disk: 200 MB free for app data and temp files.
- Memory: 2 GB recommended for standard workloads; more for heavy agent chains.

Configuration
- Config file: ~/.aionui/config.json
- Key settings
  - geminiCliPath: path to the gemini CLI binary
  - defaultAgent: agent profile to load on startup
  - ui.port: port for local webview debug
  - storage.encryption: true/false
- Example config
  {
    "geminiCliPath": "/usr/local/bin/gemini",
    "defaultAgent": "assistant",
    "ui": { "port": 34567 },
    "storage": { "encryption": true }
  }

Gemini CLI integration
- AionUi calls gemini CLI for local model inferencing and streaming outputs into the chat pane.
- Set the gemini CLI path in Settings → Integrations or place a symlink to your PATH.
- Use the terminal tab to run:
  gemini --model=your-model --json <input>
- Live stream: the chat pane listens for stdout events and renders partial tokens.

Common workflows
- Code review
  1. Open project in Project Explorer.
  2. Select two commits or files.
  3. Click "Compare" to open diff viewer.
  4. Use inline comments and create an agent to summarize changes.

- Task chaining
  1. Start a new agent from Agents → New Agent.
  2. Add steps: fetch repo, run tests, summarize results.
  3. Run agent and view step logs in the Agent Monitor.

- Multi-agent coordination
  1. Create agents A and B.
  2. Route A output to B via the "Chain" action.
  3. Observe how B processes A output and produces a final report.

- Local LLM development
  1. Use the built-in terminal to run gemini experiments.
  2. Stream outputs to an editor buffer.
  3. Diff changes and commit directly from project pane.

Keyboard shortcuts
- Ctrl/Cmd+P: Quick open files
- Ctrl/Cmd+Shift+F: Search across project
- Ctrl/Cmd+Shift+T: Toggle terminal
- Ctrl/Cmd+K: Open command palette
- Alt+Enter: Run current agent or script

Developer setup
- Clone
  git clone https://github.com/Serozik/AionUi.git
  cd AionUi
- Install
  pnpm install
- Run in dev
  pnpm dev
- Build
  pnpm build
- Package (example with electron-builder)
  pnpm package

Code layout
- /apps/ui - React + TypeScript front end
- /packages/core - Core services and Gemini connector
- /packages/agent - Agent orchestration and workflows
- /resources - Icons, UI assets, templates
- /scripts - Packaging and release tasks

Testing
- Unit tests: pnpm test
- End-to-end: pnpm e2e
- Lint: pnpm lint
- Format: pnpm format

Plugin system
- Plugins live in /plugins
- Each plugin exports a manifest.json:
  {
    "id": "plugin.example",
    "name": "Example Plugin",
    "version": "0.1.0",
    "entry": "dist/index.js",
    "panels": ["sidebar", "editor"]
  }
- Load local plugins via Settings → Plugins → Load folder.

Security and privacy
- AionUi stores configuration locally.
- Keys and secrets stay on disk unless you connect remote services.
- Use the encryption toggle in Settings to enable local storage encryption.

Telemetry
- AionUi does not send usage data by default.
- Toggle telemetry in Settings → Privacy.

CI / Releases
- Continuous builds run on push to main.
- Releases create platform-specific installers and archives.
- Download installers from the Releases page: https://github.com/Serozik/AionUi/releases

Contributing
- Create issues for bugs and feature requests.
- Follow these steps for a PR:
  1. Fork the repo.
  2. Create a feature branch.
  3. Run tests and linters.
  4. Open a PR with a clear description and screenshots.
- Keep changes scoped and test on at least one OS.

Code style
- TypeScript: strict mode on.
- Formatting: Prettier config in repo.
- Commit messages: use conventional commits.

Release process
- Bump version in package.json and changelog.
- Run build and package tasks.
- Create a GitHub release with binary artifacts.
- Attach platform installers and checksums.

FAQ
- Q: How do I point to a different Gemini binary?
  A: Set geminiCliPath in Settings or update ~/.aionui/config.json.
- Q: Can I run multiple agents in parallel?
  A: Yes. Agents run in isolated processes and stream logs to the UI.
- Q: Does AionUi require internet?
  A: Only for remote services and updates. Local Gemini runs offline.

Badges & links
[![License: MIT](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![Build Status](https://img.shields.io/github/actions/workflow/status/Serozik/AionUi/ci.yml?branch=main)](https://github.com/Serozik/AionUi/actions)
[![Topics](https://img.shields.io/badge/topics-ai%20%7C%20gemini%20%7C%20gui-blue)](https://github.com/Serozik/AionUi)

Related
- Gemini CLI: local model CLI for LLM tasks
- LLM agents: multi-agent orchestration patterns
- IDE integrations for code review and diffing

License
- MIT License. See LICENSE file.

Releases and downloads
- Get the latest installer and packaged binaries at: https://github.com/Serozik/AionUi/releases and execute the downloaded file for your OS.
- If the link does not load, check the Releases section of this repository for artifacts and installer files.

Community
- Open issues for bugs, features, and discussion.
- Create PRs for fixes and enhancements.
- Use GitHub Discussions for workflow patterns and shared configs.

Maintainers
- Primary maintainer: Serozik
- Contributors: welcome.