# Changelog

All notable changes to this project will be documented in this file.

---

## [0.8.0] - 2025-12-31
### Added
- Industry Planner (New Module)
  - Full end to end manufacturing and reactions planner built from EVE SDE and ESI data.
  - Supports both Manufacturing and Reactions, including mixed dependency chains.
  - Calculates everything based on runs, system, facility, and rig setup.
- Blueprint Dependency Tree
  - Automatically builds a full production tree from the selected root blueprint.
  - Clearly shows what needs to be built, what must be bought, and what feeds into what.
  - Expand and collapse controls with depth presets.
  - Tree filtering by blueprint or material name.
  - Optional toggle to hide raw inputs for cleaner views.
  - Per node icons, group tags, activity type, and job metadata.
- Accurate Material and Time Calculations
  - Correct EVE rounding rules for materials. (Might need some really minor tweaks)
  - Per node job time calculation using real SDE activity times.
  - Time reductions applied from blueprint ME and TE, structure bonuses, rig bonuses, and skills or implants.
  - Separate handling for root blueprint versus non root nodes.
- Facility and System Modeling
  - Select structure type Raitaru, Azbel, Sotiyo, Athanor, or Tatara.
  - Select rig tier None, T1, or T2.
  - Security aware rig bonuses for High, Low, Null, and Wormhole space.
  - Facility tax input per activity.
  - Automatic system security detection.
  - Live ESI industry cost indices with caching.
- Cost and Install Fee Estimation
  - EVE like job cost calculation using estimated item value.
  - Applies system cost index, structure role bonus, facility tax, and SCC surcharge.
  - Install costs calculated per node and summarized globally.
- Market Pricing Integration
  - Optional price inclusion toggle.
  - Market hub selection such as Jita. (Only Jita for now)
  - Buy versus sell price mode for inputs.
  - Cached market prices.
- Totals View
  - Aggregated material totals across the entire plan.
  - Clear separation between raw materials and intermediates.
  - Grouped summaries by category, group, and grand total.
  - Visual indicators for intermediate versus raw items.
- Shopping List
  - Automatically excludes intermediates.
  - Shows only what you need to buy.
  - Displays required quantity, unit prices, and total cost.
  - Fully sortable columns.
- Production Queue
  - Shows all intermediate items that must be built.
  - Displays required runs, excess output, and activity type.
  - Helps plan actual job execution order.
- Inventory Integration
  - Paste inventory directly from EVE.
  - Inventory stored locally in your browser. (Possible OPTIONAL ESI integration in the future)
  - Automatically applies inventory to totals, shopping list, and remaining ISK needed.
  - Clear distinction between required, owned, missing, and excess items.
- Profit and Margin Summary
  - Final product output summary with icon and metadata.
  - All in cost, revenue, profit, and margin calculations.
  - Profit per unit and total profit displayed.
  - Visual margin bar for quick evaluation.

---

## [0.7.0] - 2025-12-27
### Added
- **Blueprint Skill Planner**
  - Search and select any blueprint.
  - Builds a full dependency tree across Manufacturing and Reactions (shows what feeds into what).
  - Shows required skills in two ways:
    - All required skills (deduped + highest required level per skill)
    - Per blueprint skill breakdown, including each direct skill’s full prerequisite chain (shown as a readable tree).
  - One click export list you can copy and import into EVE.
  - Quality of life controls for the tree:
    - Expand / collapse all
    - Optional “show only top 2 / top 3 levels”
    - Filter the tree by blueprint / product name
    - Toggle showing reaction nodes

---

## [0.6.6] - 2025-12-27
### Changed
- Added version control and invalidation rules for client cached market data objects.

### Fixed
- **Survey Scanner**
  - Added missing type prices for materials other than Minerals (MoonGoo, Ice products)
  - Material breakdown now displays the estimated price for the previously missing materials.

---

## [0.6.5] - 2025-12-25
### Added
- **Survey Scanner**
  - Mineral Tracking
    - New Mineral table captures a “Start New” snapshot showing initial units, mined units, % left, and remaining totals.
  - Mineral Icons
  - Collapsible Mineral Panel 
    - Mineral Breakdown section can be expanded/collapsed to reduce visual noise.
  - Share Snapshot
    - Scanner state is now saved and restored from generated share links, replacing the old static URL.

### Fixed
- **Survey Scanner**
  - Table hover highlight.
  - ETA calculation stabilized by using sliding windows instead of start-to-now averages.

---

## [0.6.4] - 2025-12-23
### Added
- **Market Scheduler**
  - All ESI market prices used across the site are now pre-cached automatically every day at 11:20 UTC, replacing the old “generate on first visit” behavior.

### Changed
- Backend performance improvements for faster and more consistent ESI price fetching (less duplicate work, smoother load under traffic).

### Fixed
- Market importer stability
  - Resolved another edge-case that could cause the importer to fail unexpectedly.

---

## [0.6.3] - 2025-12-21
### Fixed
- Added support for multiple survey scanner input formats from game 
<br>(Bistot    30 000    480 000 m3    64 400 000,00 ISK    12 km)
<br>(Bistot    244    3,904 m3    524,000.00 ISK    106 km)
- Fixed concurrent market history imports breaking in some cases when generating the daily market data for each group of ores.

---

## [0.6.2] - 2025-12-18
### Changed
- Added Prismaticite prices to the Survey Scanner. (The price is the expected average over many direct refine batches)
- Added Prismaticite prices to the Mining Ledger.
- Removed the reset button on the Survey Scanner tool.
- Added an undo button for the Survey Scanner tool.
- Updated Prismaticite direct refine mineral probabilities with the latest data gathered.

### Fixed
- Fixed incorrect styling for the buttons on the "Manage Character" page.

---

## [0.6.1] - 2025-12-06
### Added
- Global Winter theme.
- Global theme toggle.

### Changed
- Optimized static assets file size.

### Fixed
- Fixed hide button icon clipping for all 3 mining market data tools.
- Fixed incorret text color for some buttons.

---

## [0.6.0] - 2025-12-05
### Changed
- Improved login reliability and character switching behavior.
- Updated the character menu in the navbar to work more smoothly across all sessions.
- Better handling when an account has no main character selected yet.

### Fixed
- Rare cases where linking an alt or switching main characters didn't refresh the UI correctly.
- Occasional issues where returning from EVE SSO would not restore the intended page.
- Fallback portrait/name now displays correctly if no main character is set.
- Changelog popup - The botton "Show full history" not closing the popup and redirecting propely in some cases.
- Fixed the About view not displaying the correct latest version.

---

## [0.5.0] - 2025-11-30
### Added
- **Changelog popup** shown on app load when a new version is available.
  - Uses the latest entry from `CHANGELOG.md`.
  - Remembers the last seen version in `localStorage` so it only appears once per release.
- **Changelog history view** at `/changelog`.
  - Timeline-style list of all past releases.
- Styling for changelog popup and history page to match the global theme.

### Changed
- Minor layout tweaks in the root app shell to host the global popup cleanly above the main content.

---

## [0.4.0] - 2025-11-18
### Added
- **Prismaticite Refinement module**:
  - New interactive tool to simulate Prismaticite refine outcomes and ISK/hour.
  - **Direct refine & Reaction refine** support, each with its own roll model and output logic.
  - **Best / worst case** rolls per mineral (min/max units hit) for more realistic ranges.
  - **God / hell roll** scenarios for fun extremes (all max or all min rolls, not meant for long-term expectations).
  - Output values presented directly as **refined units**, using your configured refine yield.

### Changed
- Refinement UI now assumes all values are **already refined**, removing redundant “(refined)” text in column headers.
- Refine input uses **decimal format** (e.g. `0.9063`) instead of percentage for more precise control.
- Tooltip wording simplified and updated to focus on min/max roll logic and how Path A / Path B behave.
- Header layout updated so the refine input sits inline with the title without stretching the section vertically.

### Fixed
- Best/worst ISK/hour values now correctly use **min/max units per mineral** instead of relying on a simple average roll.

---

## [0.3.0] - 2025-10-18
### Added
- **Ratting Ledger** module:
  - Per-character breakdown of **Total (Gross)**, **Tax**, and **Net after tax**.
  - **Top Systems** and **Top NPC Types** bar charts.
  - “Latest entries” table with recent ticks and tax details.

### Changed
- Card headers redesigned for better UI/UX:
  - Character portrait on the left, with bounties, ESS, and tax arranged compactly on the right.
- NPC types section now expands card height as needed, keeping cards aligned even when system counts differ.

### Fixed
- Total (Gross) value styling adjusted to use standard white instead of gold.
- Tax value colorized in red for quick visual scanning.
- Added extra padding in the “Latest entries” table (When, Character, Net columns) for readability.
- UTC date display corrected to respect user timezone / UTC expectations consistently.

---

## [0.2.0] - 2025-10-12
### Added
- Improvements to the **Survey Scanner / anomaly timer** tool:
  - Smarter estimation of **m³ mined per second** using sliding windows instead of a simple start-to-now calculation.
  - Automatic recalculation when new EVE survey data is pasted into the component.
  - Auto-updating timers to estimate remaining time before an ore anomaly or belt is fully mined.

### Changed
- Chart configuration updated to fix type mismatches with the Angular + Chart.js bindings.
- UI layout refined for better readability in dark mode.

---

## [0.1.0] - 2025-09-30
### Added
- Initial public release **EVE Haakario Labs**:
  - **Moon Tax Calculator** with contract/tax breakdown and unofficial disclaimer overlay.
  - **Mining Ledger** core with per-character aggregates and basic charts.
  - **Moon Ore / Standard Ore** tables with value-per-m³ calculations and sorting.
- Global **dark theme**:
  - Global design tokens.
- Basic navigation and layout structure.

