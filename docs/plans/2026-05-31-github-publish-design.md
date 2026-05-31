# GitHub publish design for build-ios-apps-marketplace

## Goal

Prepare this repository for public GitHub sharing under `anasdayeh/build-ios-apps-marketplace` without changing the plugin's preserved core behavior.

## Approach

Use one public repository with one marketplace manifest and one packaged plugin. Keep the preserved iOS skills and MCP configuration unchanged. Add only the materials required for public sharing: a cleaner public-facing README, a repository license, an initial commit, and explicit publish instructions.

## Why this approach

This route keeps installation simple. Users add one marketplace and install one plugin. It also avoids the complexity of splitting the core plugin from the Claude-specific layer across multiple repositories.

## Repository outcomes

- public-facing root README
- plugin-specific README for users inspecting the packaged plugin
- root LICENSE file
- initial git commit on the local repository
- `origin` remote prepared for `https://github.com/anasdayeh/build-ios-apps-marketplace.git`
- publish instructions using `gh repo create ... --public --source=. --remote=origin --push`

## Non-goals

- no change to the preserved iOS skill behavior
- no forced publish without an explicit final publish step
- no extra plugins or speculative repository automation
