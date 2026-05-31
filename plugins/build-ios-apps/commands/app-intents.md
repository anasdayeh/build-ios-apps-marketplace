---
description: Design or refine App Intents, entities, and App Shortcuts using the preserved iOS App Intents workflow
argument-hint: '[feature, action, or system surface]'
---

Use the preserved `ios-app-intents` skill as the primary workflow.

Rules:
- Start from the smallest useful external action, not from screens.
- Prefer a narrow App Intents surface with clear runtime handoff into the app when needed.
- Use Context7 for current Apple/App Intents behavior when API details, availability, or system-surface guidance matter.
- Keep intent types thin and route business logic back into app services/models.

Return:
- proposed actions
- proposed entities or enums
- whether the action completes inline or opens the app
- the smallest initial implementation slice
