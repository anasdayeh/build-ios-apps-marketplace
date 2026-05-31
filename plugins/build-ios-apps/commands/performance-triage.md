---
description: Route a SwiftUI performance, launch latency, or memory issue to the correct preserved iOS workflow
argument-hint: '[symptom, screen, or reproduction flow]'
---

Choose the narrowest preserved workflow that matches the symptom:
- `swiftui-performance-audit` for invalidation storms, layout thrash, broad view updates, image/render cost, or UI jank rooted in SwiftUI code structure.
- `ios-ettrace-performance` for launch latency, runtime CPU hotspots, or trace-backed simulator flow analysis.
- `ios-memgraph-leaks` for leaks, memory growth, retain cycles, or before/after leak proof.
- `ios-debugger-agent` when simulator build/run/setup or UI driving is required before collecting evidence.

Rules:
- Do not mix all workflows at once. Start with the most likely one.
- Keep captures focused on one user-visible flow.
- Distinguish suspicion from evidence.
- If the issue is ambiguous, explain which workflow you are choosing and why.

Return:
- chosen workflow
- why it fits the symptom
- what evidence you will collect or review
- next step after the first pass
