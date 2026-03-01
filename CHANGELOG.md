# Changelog

All notable changes to DOCSIOS will be documented in this file.

## 0.1 (Build 17) - 2026-03-01

### Improved
- Row Styling Alignment — Harmonized the visual design of Timeline rows and Event rows to ensure a consistent look and feel across different modules.
- Smart Tooltips — Enhanced tooltips to dynamically filter content based on visible chart series and corrected the display order.
- Component Reusability — Streamlined the codebase by removing legacy chart implementations in favor of the centralized chart component.
- Data Models — Updated BNetzMeasurement and CorrelationEntry to support the expanded metrics and improved chart requirements.

### Added
- Global Chart Unification — Successfully migrated all feature-specific charts (Speedtest, Broadband, Channel Details, Trends, and Correlation) to the new global DsChartCard component for a consistent UI/UX.
- Interactive Chart Legends — Users can now toggle the visibility of individual metrics by tapping legend items.
- Full-Screen Landscape Mode — Added a dedicated toggle to expand any chart into a high-detail landscape view.
- Individual Metric Scaling — Implemented normalization logic (matching the web backend) to display SNR, Power, and Errors optimally within the same chart.
- Enhanced Signal Metrics — Added Upstream Power (US), Correctable, and Uncorrectable errors to the Signal Correlation timeline.

### Fixed
- Navigation Stability — Resolved the critical "view jumping" issue on iPhone Pro Max models during orientation changes by stabilizing the NavigationStack hierarchy.
- Navigation bar titles now appear correctly for tabs in the "More" section, including in German

## 0.1 (Build 16) - 2026-02-27

### Improved
- Default Event Filtering — "Monitoring Started" events are now hidden by default in Timeline.
- Toolbar UX — Unified filter interactions across Events View and Timeline View using consistent menus and icon logic.
- "Mark All Read" Logic — Standardized the button to be always visible but disabled if no unacknowledged events exist, ensuring it correctly accounts for filtered entries.

### Added

- Complaint Workflow — New dedicated section for generating ISP complaint letters. Choose the time period, language, and enter your customer details — the app generates a ready-to-send letter that can be exported as a PDF or shared directly via the DOCSight API.
- Speedtest Quality Indicators — Download and upload speeds are now color-coded based on your booked bandwidth, making it easy to spot underperforming results at a glance. The color indicators appear in the speedtest list, on the dashboard, and in the detail view.
- Speed Health in Speedtest Details — The detail view for a speedtest result now shows an overall Speed Health rating (Good / Warning / Poor) at the top.
- Temperature overlay in Trends and Timeline charts — a subtle dashed orange line showing temperature alongside signal quality, normalized to
each chart's scale
  - The overlay only appears if weather integration is enabled in DOCSight
  - **Requires minimum version v2026-02-27.3 of DOCSight**
- App Icon Badges — Implemented local synchronization of the home screen badge count to reflect unacknowledged events. (requires Push Notification permissions)
- iPad Optimization — Refactored Channels View to a NavigationSplitView layout for a native sidebar experience.
- Direction Toggle — Added a segmented picker to Channels View (DS/US) to easily navigate long channel lists.
- Active Filter Indicators — Added blue dot badges to toolbar icons to signal when a filter is actively hiding data (e.g., hidden monitoring events).

## 0.1 (Build 14) - 2026-02-27

> [!NOTE]  
> I had to skip Build 13 because I needed to add an App Store Connect–related change.

### Improved
- Improved dashboard loading UX with smooth card insert animations (fade + slight top-slide + spring reflow), so cards no longer pop in.
- Improved backend compatibility messaging in Dashboard with clearer update-required presentation.
- Improved Connection card behavior by making expansion conditional on available device details.

### Added
- Added adoption of new DOCSight summary payload in `GET /api/channels`:
  - `summary.health`
  - `summary.ds_power_avg`
  - `summary.ds_snr_min`
  - `summary.ds_snr_avg`
  - `summary.us_power_avg`
  - `summary.ds_correctable_errors`
  - `summary.ds_uncorrectable_errors`
  - `summary.us_capacity_mbps`
- Added `GET /health` version usage in app (DOCSight Version in Settings + dashboard compatibility check).
- Added version-based backend requirement check against `v2026-02-27.1`.
- Added `GET /api/device` integration with new DeviceInfo model and expandable modem details in the Dashboard Connection card (manufacturer, model, firmware, uptime).
- Added EN/DE localization for the new backend/version/device UI strings.

### Fixed
- Replaced remaining manual client-side derivations with backend-provided summary values in Dashboard and Gaming paths.
- Updated Signal Health issue mapping to current backend issue keys (new code set), preventing raw technical keys from appearing in UI.

## 0.1 (Build 12) - 2026-02-26
### Improved
- Refined Dashboard readability in expanded Affected Channels rows with clearer direction highlighting (DS in blue, US in purple) and a neutral separator.
- Updated Help screen presentation with app branding and a cleaner support/feedback entry point.
- Improved setup onboarding visuals by replacing the connector symbol with the app logo.

### Added
- Added a smoother and more reliable splash fade-out handoff.

### Fixed
- Fixed tap targets for setup primary actions (Connect / Authenticate) so the full button area is tappable.
- Fixed modulation improvement highlighting in Events/Related Events by switching to blue for better visual semantics.

## 0.1 (Build 11) - 2026-02-26
### Improved
- Refined the Dashboard with cleaner, more scannable cards and better interaction behavior.
- Polished localization and wording across key UI areas (including Affected Channels).
- Improved iPad dashboard layout editing for better readability and card organization.

### Added
- Added expandable Signal Summary and Affected Channels cards.
- Added faster drill-down from Affected Channels directly into channel details.
- Added persistence for each Dashboard card’s expanded/collapsed state on iPhone.
- Added compact, localized channel issue summaries in Channel Detail.

### Fixed
- Fixed channel issue visibility by aligning issue summaries with backend health details.
- Fixed Events wording consistency (replacing abbreviated channel labels with localized full labels).
- Fixed Speedtest chart interaction to better surface the selected timestamp on the x-axis.

## 0.1 (Build 10) - 2026-02-26
### Improved
- Events experience with clearer modulation/SNR details and smoother channel navigation
- Event interaction usability by expanding tap areas and refining row layout
- Visual styling (colors, timestamps, indicators) for improved readability

### Added
- “Related Events” section in Channel Details showing channel-specific modulation changes

### Fixed
- Tab bar localization now updates immediately after language change

### Changed
- Minor wording and localization refinements (EN/DE)

## 0.1 (Build 9) - 2026-02-25
### Added
- Initial public TestFlight beta release
- Dashboard with signal health, collector status and speedtest snapshot
- Channel analysis with per-channel detail views
- Trend and correlation views
- BQM and Smokeping integration
- Incident/journal and export tools
- Home screen widgets (two sizes)
- English and German localization