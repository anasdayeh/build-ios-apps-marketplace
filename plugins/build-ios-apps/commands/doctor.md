---
description: Validate local iOS tooling, XcodeBuildMCP readiness, and repo setup before using the Build iOS Apps workflows
argument-hint: '[optional path or repo focus]'
---

Goal: determine whether this machine and the current repo are ready for the Build iOS Apps plugin workflows without making behavior-changing edits.

Core behavior:
- Stay read-only unless the user explicitly asks you to fix something.
- Prefer the plugin's preserved skills and XcodeBuildMCP-backed workflows over inventing new iOS guidance.
- Use Context7 for current Claude Code, XcodeBuildMCP, or Apple API/tooling details when those details matter.

Checklist:
1. Confirm the active working directory and whether it contains an Xcode project, Xcode workspace, Swift package, or `.xcodebuildmcp/config.yaml`.
2. Check host prerequisites such as `xcode-select -p`, `xcodebuild -version`, and whether `npx -y xcodebuildmcp@latest --help` works.
3. If the repo looks like an Xcode project, inspect likely schemes/projects/workspaces and note what the user should target first.
4. Report blockers as a short ordered list: missing Xcode, missing simulator target, missing scheme, missing config, or unknown project path.
5. End with the next best action, usually one of:
   - use `/build-ios-apps:run-simulator`
   - use `/build-ios-apps:performance-triage`
   - use `/build-ios-apps:swiftui-refactor`
   - or use the relevant preserved skill directly.
