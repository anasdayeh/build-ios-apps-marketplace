---
description: Refactor a SwiftUI view while preserving behavior using the preserved SwiftUI patterns and refactor skills
argument-hint: '<path-to-view> [goal]'
---

Use the preserved `swiftui-view-refactor` and `swiftui-ui-patterns` skills together.

Refactor rules:
- Preserve behavior unless the user explicitly asks for UI or UX changes.
- Prefer smaller dedicated subviews, explicit data flow, stable identity, and modern SwiftUI ownership patterns.
- Keep business logic out of the view body.
- If the view is large or performance-sensitive, also consult `swiftui-performance-audit`.
- If the requested change depends on current SwiftUI API behavior or availability, use Context7 first.

Deliver:
- a concise before/after structural summary
- the behavior-preserving refactor itself
- any risks or follow-up testing needed
