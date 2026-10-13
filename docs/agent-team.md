# Agent team

For Mona's Project Pulse dashboard, I will use a four-agent team orchestrated from GitHub Copilot CLI inside a GitHub Codespace.

- Orchestrator — Target model: Claude Opus 4.7 (copilot). Responsibility: break the dashboard work into phases, delegate to specialist agents, coordinate planning/design/build/validation, and report progress. Definition path: `.github/agents/orchestrator.agent.md`.
- Planner — Target model: Claude Opus 4.7 (copilot). Responsibility: research the repository, identify dependencies and edge cases, and produce a practical implementation plan with file assignments and validation expectations. Definition path: `.github/agents/planner.agent.md`.
- Designer — Target model: Gemini 3.1 Pro (copilot). Responsibility: shape the dashboard UX, accessibility, information hierarchy, and visual styling so the page reads as a polished Project Pulse frontend. Definition path: `.github/agents/designer.agent.md`.
- Coder — Target model: GPT-5.5 (copilot). Responsibility: implement the dashboard logic and front-end files, create any required runnable app support, and validate the result before reporting completion. Definition path: `.github/agents/coder.agent.md`.

This setup uses GitHub Copilot CLI in a Codespace terminal as the orchestration layer so the workflow stays coordinated across planning, design, implementation, and final validation.
