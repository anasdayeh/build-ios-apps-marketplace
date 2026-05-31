---
name: ios-debugger-agent
description: Build, run, and debug iOS apps on Simulator with XcodeBuildMCP. Use when launching an app, inspecting simulator UI or logs, or diagnosing runtime behavior.
---

# iOS Debugger Agent

## Overview
Use XcodeBuildMCP to build and run the current project scheme on a booted iOS simulator, interact with the UI, and capture logs. Prefer the MCP tools for simulator control, logs, and view inspection.

## Core Workflow
Follow this sequence unless the user asks for a narrower action.

### 1) Discover the simulator target
- Use the XcodeBuildMCP simulator listing tool and prefer a simulator already in state `Booted` when the task depends on an existing runtime state.
- If none are booted and the requested flow is a normal build/run path, prefer XcodeBuildMCP's simulator build-and-run flow because it can boot the simulator automatically.
- If the task depends on a specific booted simulator and none are booted, ask the user before choosing one.

### 2) Establish project defaults
- If this Claude runtime exposes XcodeBuildMCP session-default tools, inspect and set them before the first build/run/test call.
- Otherwise, rely on the target repo's `.xcodebuildmcp/config.yaml` when present, or pass the project/workspace path, scheme, simulator, and debug configuration explicitly to each XcodeBuildMCP action.
- Prefer `Debug` configuration unless the user asked for another build configuration.

### 3) Build + run (when requested)
- Use the XcodeBuildMCP simulator build-and-run flow.
- **If the build fails**, inspect the error output, retry with the most direct xcodebuild-backed route if available, and only then escalate.
- **After a successful build**, verify the app launched by using the UI snapshot or screenshot tool before proceeding to UI interaction.
- If the app is already built and only launch is requested, use the simulator app launch tool.
- If the bundle id is unknown, resolve it from the built simulator app path first and then query the bundle identifier.

## UI Interaction & Debugging
Use these when asked to inspect or interact with the running app.

- **Snapshot UI**: use the XcodeBuildMCP UI snapshot/describe tool before tapping or swiping.
- **Tap**: prefer the UI-automation tap tool by accessibility id or label; use coordinates only if needed.
- **Type**: use the text-entry tool after focusing a field.
- **Gestures**: use the gesture or swipe tools for common scrolls and edge swipes.
- **Screenshot**: capture screenshots for visual confirmation.

## Logs & Console Output
- If this Claude runtime exposes XcodeBuildMCP logging tools, start log capture with the resolved app bundle id and stop it when enough evidence has been gathered.
- If dedicated logging tools are not exposed, relaunch with console capture enabled when that option is available, then summarize the important lines.

## Troubleshooting
- If build fails, retry with the most direct xcodebuild-backed route that XcodeBuildMCP exposes before escalating.
- If the wrong app launches, confirm the scheme and bundle id.
- If UI elements are not hittable, refresh the UI snapshot after layout changes.
