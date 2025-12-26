# Copilot Instructions for Check-List Project

## Overview
This is a progressive web application for event pre-show checklists. It evolved from static HTML checklists to an interactive JavaScript app with role-based task management, timed blocks, and localStorage persistence.

## Architecture
- **Vanilla JavaScript**: No frameworks, pure DOM manipulation and event handling
- **State Management**: Single `state` object with fields, checks, and roleId
- **Persistence**: localStorage with JSON serialization
- **Theming**: CSS custom properties (variables) for dark theme
- **Layout**: CSS Grid and Flexbox for responsive design

## Key Files
- `index03.html`: Main interactive version with full functionality (roles, timeline, KPIs)
- `index.html`: Original static checklist template
- Other `index*.html`: Iterations and variants

## Patterns & Conventions
- **State Structure**: `state = { roleId, onePage, fields: {...}, checks: { roleId: { blockKey: { idx: boolean } } } }`
- **DOM Access**: `const $ = (id) => document.getElementById(id);` for concise element selection
- **Event Binding**: Direct `addEventListener` calls, no delegation
- **Rendering**: Imperative DOM creation in render functions (renderTabs, renderTimeline, renderKPI)
- **Time Calculations**: Minutes-based arithmetic with `parseTimeToMinutes` and `minutesToHHMM`
- **Role-Specific Logic**: Each role has a `build()` function that filters/modifies `blocksBase`
- **Print Support**: CSS `@media print` and `window.print()` for PDF generation

## Workflows
- **Role Switching**: Tabs update `state.roleId` and re-render timeline/KPIs
- **Task Checking**: Checkbox changes update `state.checks[roleId][blockKey][idx]` and save
- **Time-Based Blocks**: Blocks computed relative to `showTime` field (e.g., T-90 min)
- **One-Page Mode**: Toggle class for print-friendly layout
- **Reset**: Confirms before clearing localStorage and reloading

## Development Notes
- **No Build Process**: Direct HTML/JS editing, open in browser
- **Testing**: Manual in browser, check localStorage persistence
- **Print Testing**: Use browser print to PDF for checklist output
- **Responsive**: Viewport meta and grid layouts for mobile
- **Accessibility**: Basic labels, but no ARIA attributes

## Examples
- Adding a new role: Define in `roles` array with `build()` function that returns modified blocks
- New timed block: Add to `blocksBase` with `key`, `title`, `offsetMin`, `who`, `tasks` array
- Custom field: Add to `inputs` array and `state.fields`, bind in init loop</content>
<parameter name="filePath">c:\Users\EDY\Music\Time _Agosto\Time agosto 01\check-list\.github\copilot-instructions.md