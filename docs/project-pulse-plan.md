# Project Pulse dashboard implementation plan

## Summary

Mona's Project Pulse dashboard will be a lightweight static frontend that helps contributors quickly understand which projects are active, who owns them, their status, recent activity, and risk level. The work will be coordinated by the Orchestrator, with the Planner identifying the implementation flow, the Designer shaping the information hierarchy and visual treatment, and the Coder building the actual dashboard files. The final output should be a polished static app with a working VS Code launch configuration that opens the dashboard in a browser instead of the repository directory listing.

## Ordered implementation steps

1. Review the Project Pulse brief and repository constraints.
   - Confirm the required files: app/index.html, app/styles.css, app/project-data.json, and .vscode/launch.json.
   - Confirm the dashboard should be a static, contributor-friendly page rather than a server app.

2. Define the content model and file ownership.
   - Decide on the projects array structure in app/project-data.json.
   - Use the required fields: name, owner, status, recentActivity, and priority.
   - Keep the data sample realistic enough to demonstrate status badges, activity summaries, and project cards.

3. Shape the dashboard UX and visual hierarchy.
   - The Designer should define the layout, spacing, card design, and the priority or status treatment.
   - The page should read clearly at a glance, with strong heading structure and readable project summaries.
   - Focus on accessible contrast, readable typography, and mobile-friendly spacing.

4. Implement the static app structure.
   - Build app/index.html with the Project Pulse title, the project grid, and the semantic structure needed for accessible browsing.
   - Connect the page to app/styles.css and app/project-data.json.
   - Use consistent project-card markup so CSS and data can be updated independently.

5. Add the dashboard styling.
   - Create app/styles.css with a clean card-based dashboard aesthetic.
   - Use status badges and visual indicators for active, at-risk, or healthy workstreams.
   - Ensure the layout improves readability across screen sizes.

6. Add the launch configuration.
   - Create .vscode/launch.json so VS Code can run the dashboard with the configuration name Run Project Pulse Dashboard.
   - Set the launch target to serve the app directory and open index.html.
   - Avoid a directory listing by ensuring the browser opens the actual app page.

7. Validate the complete dashboard.
   - Open the dashboard via the VS Code launch configuration.
   - Check that the page title matches Project Pulse and that all project data appears in cards.
   - Confirm interaction states, styling, and layout are stable in the browser.

## File assignments

- app/project-data.json
  - Ownership: Coder
  - Responsibility: Define the top-level projects array and ensure each project object contains the required fields: name, owner, status, recentActivity, and priority.
  - Dependency: This file is the data source that the HTML and CSS rely on.

- app/index.html
  - Ownership: Coder, with design review from Designer
  - Responsibility: Create the semantic structure for the dashboard, including project cards, status badges, and a readable information hierarchy.
  - Dependency: This file depends on the final data structure and should align with the Designer's visual layout decisions.

- app/styles.css
  - Ownership: Designer, with implementation by Coder
  - Responsibility: Implement the dashboard styling, including spacing, card shapes, shadows, badge treatments, typography, and layout polish.
  - Dependency: This sheet depends on the finalized HTML classes and the approved design treatment.

- .vscode/launch.json
  - Ownership: Coder
  - Responsibility: Create the VS Code launch configuration named "Run Project Pulse Dashboard" that serves the app directory and opens index.html.
  - Dependency: This depends on the final app structure and the accepted run target.

## Designer responsibilities

The Designer is responsible for the product-facing quality of the dashboard:

- Define the visual hierarchy so contributors can scan project health quickly.
- Shape the card layout, spacing, and readability across the dashboard.
- Establish the style language for status badges, project cards, and consistent visual rhythm.
- Guide decisions such as border radius, shadows, contrast, and overall polish.
- Review the final HTML and CSS against the desired "clean and contributor-friendly" dashboard experience.

The Designer's role is to create the experience blueprint, while the Coder translates that into implementation details.

## Coder responsibilities

The Coder is responsible for turning the design and data contract into a working static app:

- Build the project data source in app/project-data.json.
- Create the semantic HTML structure and card rendering in app/index.html.
- Implement the styling in app/styles.css to match the approved direction.
- Ensure the project fields render correctly and the cards are readable.
- Create .vscode/launch.json so the app runs from VS Code as expected.
- Validate the app before reporting completion.

## Dependencies between steps

- The data structure in app/project-data.json must be defined before the dashboard markup can reliably render.
- The HTML structure in app/index.html must align with the classes and markup the CSS expects.
- The CSS depends on the final HTML structure and the approved visual design.
- The launch configuration depends on knowing the exact app directory and target page to open.
- Final validation depends on all of the above files being present and working together as a single dashboard.

## Parallel work decisions

Parallel work is appropriate only where file ownership and data dependencies do not create merge risk.

- Good parallel setup:
  - The Designer can draft the visual direction while the Coder prepares the projects data shape.
  - The Coder can create the initial folder structure and JSON contract while the Designer finalizes the visual system.
- Sequential work:
  - The dashboard markup should be finalized before the CSS is fully implemented, because the HTML structure and CSS selectors need to be aligned.
  - The launch configuration should be created after the app directory structure is stable.
  - The final validation should run only after the HTML, CSS, JSON, and launch file are integrated.

The key decision is to avoid parallelizing HTML and CSS edits without a shared class and markup contract, because that creates unnecessary rework and inconsistency.

## Validation expectations

The dashboard is considered complete only when all of the following checks pass:

- app/project-data.json is valid and contains a top-level projects array with the required fields.
- app/index.html renders the project cards and displays names, owners, statuses, recent activity, and priority information.
- app/styles.css provides a polished visual treatment with readable spacing, card styling, and status emphasis.
- .vscode/launch.json exists and starts the app from the app directory.
- Opening the dashboard via "Run Project Pulse Dashboard" loads index.html, not a directory listing.
- The design remains readable, accessible, and contributor-friendly after the whole dashboard is assembled.

## Open questions

- Should the dashboard use realistic sample project names and owners, or should it be fully synthetic for demonstration purposes?
- Are there preferred status labels beyond the standard active, at risk, and healthy states used in the brief?
- Does the team want additional filtering or sorting in a future iteration, or is this first version a simple contributor overview only?

This plan keeps the work small, sequenced, and aligned with the Project Pulse brief while still making the Orchestrator, Designer, and Coder responsibilities explicit and testable.
