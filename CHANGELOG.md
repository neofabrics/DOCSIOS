# Changelog

All notable changes to DOCSIOS will be documented in this file.

## 0.1 (Build 23) - 2026-03-08

### Added
- **Insights Tab** — on-device statistical analysis of historical modem data, no ML required:
  - *Prime-Time Degradation* — detects if your SNR regularly drops during specific evening hours
  - *Temperature Correlation* — checks whether high outside temperatures correlate with SNR loss
  - *Uncorrectable Error Trend* — alerts if uncorrectable errors have significantly increased week-over-week
  - *Channel Instability* — flags individual channels that changed modulation unusually often in the last 24h
- **Background Polling & Local Notifications** — the app can now check your DOCSight metrics in the background and notify you without being open:
  - New Events, Signal Health Changes, Speed Anomalies (each independently toggleable in settings)
  - Single-event notifications show the actual event message instead of just a count
  - Polling interval follows what's configured in your DOCSight backend — no unnecessary extra requests
- **Live Activity & Dynamic Island** — monitor modem health live from Lock Screen or Dynamic Island:
  - Compact: health dot + current SNR
  - Expanded: health status, SNR Avg, degraded channel count, uncorrectable errors
  - Lock Screen: 2×2 metric grid (SNR Min | SNR Avg / Uncorr. Errors | Degraded)
  - Starts automatically when a background check detects degradation
    - Can also be started manually in the Dashboard
  - Stops automatically on recovery or after 60 minutes
  - Shield badge when the backend is actively suppressing a known error spike
  - Live Activity polling follows the DOCSight backend's configured polling interval instead of a fixed interval
- **Temperature Overlay in Channel Detail Charts** — Power and SNR charts in channel detail view now show the outside temperature overlay if enabled, consistent with Trends and Correlation views

## 0.1 (Build 22.0.2) - 2026-03-07

> [!NOTE]  
> Build 22.0.2 is compatible with older DOCSight versions but requires at least `v2026-03-06.3` for the Modulation feature. Older versions will show a banner prompting to update DOCSight.

### Added

- Support for DOCSight's new Modulation feature — new full tab with distribution overview and intraday detail sheet (requires at least DOCSight `v2026-03-06.3`)
- Centralized OSLog-based error logging — unified logging via Apple's OSLog framework; logs remain on-device and are never transmitted
- AsyncState<T> + LoadingContainer — refactored boilerplate for async data loading

### Improved

- Reload animation — scroll-to-top + opacity dimming on filter/direction change in Modulation, Trends, Speedtest, Correlation and Dashboard; 0.8s artificial delay removed everywhere
- URLComponents — replaced string-interpolated query params with proper URLComponents

### Fixed

- Fullscreen image viewer — black screen on open prevented

## 0.1 (Build 21) - 2026-03-06

### Added
- Tolerated health status — new intermediate signal state between Good and Marginal, shown consistently across all views

### Improved
- Correlation chart: health bands now have a saturated color strip along the top edge for clearer boundaries

## 0.1 (Build 20.0.1) - 2026-03-05

### Fixed

- Fixed a stale app icon badge incorrectly showing unread events
- Fixed channel comparison not working when opened from the Dashboard
- Complaint View now correctly auto-detects all 4 supported languages based on device language settings

## 0.1 (Build 20) - 2026-03-03

### Improved

- Dashboard visual hierarchy — Gaming tab removed from tab bar; GamingScoreCard now opens GamingView as a sheet for a cleaner tab structure
- HealthSummaryCard slimmed down
- ChannelsCard now shows DS/US channel counts directly in the header alongside health percentages
- Operational events filter extended to cover both monitoring_started and monitoring_stopped; filter state persisted via @AppStorage and shared between EventsView and Correlation View
- Timeline tab renamed to "Correlation" / "Korrelation"; filter icon shows filled badge when operational events are hidden
- monitoring_started message now shows health state ("Health: Marginal") instead of repeating the title

### Added

- **New Feature: Channel Compare** — compare up to 6 DS or US channels side by side with Power and SNR charts, signal quality thresholds, scrubbing tooltips showing all channels simultaneously, and a fullscreen mode with period controls
  - Just tap the chart button in the Channel Detail View on the top right to open the Channel Compare feature
- Rich localized event details in EventsView and the Correlation timeline — human-readable, fully localized descriptions per event type instead of raw backend messages
- Localized event messages in Dashboard's RecentEventsCard (all event types covered)
- Localized correlation chart tooltips with compact modulation format ("DS 42 ▼2, US 7 ▲1")

### Fixed

- showPoints parameter in DsChartCard was declared but never wired up — data points now render correctly; Speedtest series in CorrelationView also
gains point markers
- Modulation event cards: multi-channel events no longer have a tap target on the whole card — each channel sub-row is independently tappable

## 0.1 (Build 19) - 2026-03-02

### Improved

- Uncorrectable error percentage shown in Signal card header (instead of raw count)
- Spike suppression indicator — when the backend suppresses a one-time error spike, the Signal card shows "One-time error spike"

### Added

- Modulation history chart in Channel Detail — stepped line showing QAM modulation changes over time, with fullscreen support

### Fixed

- Fullscreen rotation loop — chart no longer oscillates between portrait and landscape after manually returning to portrait

## 0.1 (Build 18) - 2026-03-01

### Improved

- Correlation chart – Line styles now match the web UI — thinner solid lines (SNR purple, DS Power pink, US Power
amber); uncorrectable errors rendered as bars in the bottom 20% of the chart
- Threshold fit button – Added "Fit" toggle button to charts; threshold lines outside the visible range are filtered
out when fit mode is off
- Weather overlay – Padding above and below the temperature line (15%) keeps it from touching the chart edges
- Dashboard – Channels card – Renamed from "Affected Channels" to "Channels"; icon updated to reflect the broader scope
- Trends – Errors chart uses a dedicated bar chart component; threshold reference lines added to all signal charts

### Added
- Correlation chart – Event markers (triangles) from the timeline displayed directly in the chart, color-coded by
severity; event label and message visible in the scrub tooltip
- Correlation chart – Fullscreen mode now includes a time range picker to switch periods without closing the chart
- Charts in trends and channel details – Now containing optional thresholds, can be enabled and disabled by the user per chart including optional fit to zoom
- Trends charts – Fullscreen mode now includes a range picker (Day / Week / Month)
- Channel Detail – Added 3-day option to the time range picker
- Chart defaults – New "Chart Defaults" section in Settings to configure default visibility of threshold lines,
threshold labels, and fit-to-thresholds behavior
- Dashboard – Signal Summary – DS/US power and SNR values are now color-coded (green / orange / red) based on signal
health, with the measured min–max range shown as a subtle hint
- Dashboard – Channels card – Header now shows the percentage of healthy DS and US channels (e.g. ↓ 85% ↑ 100% healthy)

### Fixed

- ChannelDetailView – No longer inherits pull-to-refresh when opened as a sheet from the Correlation view
- Correlation view – Section header renamed from "Timeline" to "Events" for clearer wording
- Dashboard – Signal card – Downstream and Upstream columns are now always equal height

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