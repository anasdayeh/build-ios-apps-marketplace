---
description: Build, launch, and debug the current iOS app on Simulator using the preserved iOS debugger workflow
argument-hint: '[what to reproduce, verify, or inspect]'
---

Use the preserved `ios-debugger-agent` skill as the primary workflow.

Execution rules:
- Prefer XcodeBuildMCP for simulator build, launch, UI inspection, screenshots, and logs.
- If the repo has `.xcodebuildmcp/config.yaml`, use it. Otherwise discover the minimum required project, scheme, and simulator details before building.
- When the user gives a bug or verification target, keep the run focused on reproducing or validating that exact path.
- After launch, verify the app is actually on the expected screen before interacting.
- If the build fails, summarize the first real blocker and propose the smallest next fix.

Output:
- What project/scheme/simulator you targeted
- Whether the app built and launched
- Any logs, screenshots, or UI findings that matter
- The concrete next action
