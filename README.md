# EvE-Haakario-Labs

# Changelog

All notable changes to this project will be documented in this file.

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
- UI layout refined for better readability in dark mode (consistent card and chart styling with the rest of the app).

---

## [0.1.0] - 2025-09-30
### Added
- Initial public release **EVE Haakario Labs**:
  - **Moon Tax Calculator** with contract/tax breakdown and unofficial disclaimer overlay.
  - **Mining Ledger** core with per-character aggregates and basic charts.
  - **Moon Ore / Standard Ore** tables with value-per-m³ calculations and sorting.
- Global **dark + gold “glass” theme**:
  - Global design tokens.
  - Glassy panels, zebra tables, and pill chips.
- Basic navigation and layout structure.
