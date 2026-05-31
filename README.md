# Build iOS Apps Marketplace for Claude Code

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![GitHub stars](https://img.shields.io/github/stars/anasdayeh/build-ios-apps-marketplace?style=social)](https://github.com/anasdayeh/build-ios-apps-marketplace)

A public Claude Code marketplace repository for `build-ios-apps`, a plugin for iOS development with SwiftUI, App Intents, simulator debugging, performance profiling, leak analysis, and XcodeBuildMCP workflows.

This repository packages a Claude-optimized port of the OpenAI Build iOS Apps plugin. It preserves the core iOS skills and MCP behavior, then adds Claude-native commands and agents for smoother day-to-day use in Claude Code.

## Why use this plugin

Use `build-ios-apps` when you want Claude Code to help with:

- SwiftUI UI design and refactoring
- App Intents and App Shortcuts design
- iOS Simulator build, launch, and UI inspection
- runtime performance triage
- ETTrace profiling for focused simulator flows
- memgraph-based leak investigation
- XcodeBuildMCP-backed iOS workflows inside Claude Code

## What this repository includes

- a Claude marketplace manifest at `.claude-plugin/marketplace.json`
- one installable plugin at `plugins/build-ios-apps`
- the preserved core iOS skillset
- Claude-native commands for common entry points
- Claude-native agents for orchestration and triage

## What the plugin preserves

The packaged plugin keeps the core behavior intact:

- the same 8 core iOS skills
- the same `xcodebuildmcp` launch command
- the same enabled XcodeBuildMCP workflows
- the same bundled references, assets, and helper scripts

The preserved MCP configuration is:

```json
{
  "mcpServers": {
    "xcodebuildmcp": {
      "command": "npx",
      "args": ["-y", "xcodebuildmcp@latest", "mcp"],
      "env": {
        "XCODEBUILDMCP_ENABLED_WORKFLOWS": "simulator,ui-automation,debugging,logging"
      }
    }
  }
}
```

## Added Claude-native surfaces

### Commands

- `/build-ios-apps:doctor`
- `/build-ios-apps:run-simulator`
- `/build-ios-apps:performance-triage`
- `/build-ios-apps:swiftui-refactor`
- `/build-ios-apps:app-intents`

### Agents

- `ios-workflow-orchestrator`
- `swiftui-refactor-reviewer`
- `ios-performance-triager`

## Install from GitHub

After this repository is public, add it as a Claude marketplace and install the plugin:

```bash
claude plugin marketplace add https://github.com/anasdayeh/build-ios-apps-marketplace
claude plugin install build-ios-apps@build-ios-apps-marketplace
```

## Install from a local checkout

```bash
claude plugin marketplace add /path/to/build-ios-apps-marketplace
claude plugin install build-ios-apps@build-ios-apps-marketplace
```

## Important coexistence note

If you already have a local skills-dir copy at `~/.claude/skills/build-ios-apps`, do not keep both active at once. Use either the marketplace-installed version or the skills-dir copy, not both.

## Repository layout

```text
build-ios-apps-marketplace/
├── .claude-plugin/
│   └── marketplace.json
├── docs/
│   └── plans/
├── plugins/
│   └── build-ios-apps/
│       ├── .claude-plugin/
│       │   └── plugin.json
│       ├── commands/
│       ├── agents/
│       ├── skills/
│       └── .mcp.json
├── CHANGELOG.md
└── README.md
```

## Development notes

Validate the marketplace:

```bash
claude plugin validate .
```

Validate the packaged plugin:

```bash
claude plugin validate plugins/build-ios-apps
```

## License

MIT
