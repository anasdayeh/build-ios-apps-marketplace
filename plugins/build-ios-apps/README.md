# Build iOS Apps

`build-ios-apps` is a Claude Code plugin for iOS development. It packages preserved iOS-focused skills for SwiftUI, App Intents, simulator debugging, ETTrace profiling, and memgraph leak analysis, then adds Claude-native commands and agents on top.

## Core guarantee

This plugin preserves the core behavior of the earlier Claude-compatible port:

- the same 8 core skills remain intact
- the same `xcodebuildmcp` command is used
- the same XcodeBuildMCP workflow set is enabled
- the same bundled scripts, references, and assets are retained

The Claude-specific additions are additive only. They do not replace or rewrite the preserved core skills.

## Core skills

- `ios-app-intents`
- `ios-debugger-agent`
- `ios-ettrace-performance`
- `ios-memgraph-leaks`
- `swiftui-liquid-glass`
- `swiftui-performance-audit`
- `swiftui-ui-patterns`
- `swiftui-view-refactor`

## Claude-native commands

- `/build-ios-apps:doctor`
- `/build-ios-apps:run-simulator`
- `/build-ios-apps:performance-triage`
- `/build-ios-apps:swiftui-refactor`
- `/build-ios-apps:app-intents`

## Claude-native agents

- `ios-workflow-orchestrator`
- `swiftui-refactor-reviewer`
- `ios-performance-triager`

## Install

Install this plugin from the `build-ios-apps-marketplace` marketplace:

```bash
claude plugin install build-ios-apps@build-ios-apps-marketplace
```

## MCP behavior

This plugin preserves the original MCP setup:

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

## Compatibility note

Do not activate this marketplace-installed plugin at the same time as a local skills-dir copy of `build-ios-apps`. Use one active copy only.
