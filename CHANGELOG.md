# Changelog

All notable changes to DOCSIOS will be documented in this file.

## 1.2 (Build 120) - 2026-05-08

### Notifications & Background Refresh

- Added configurable event notifications by event type and severity.
- Added configurable background refresh requests for local notification checks.
- Added clearer background check status information.
- Improved local notification handling for DOCSight events.
- Preserved compatibility with existing notification settings from earlier app versions.

### Diagnostics

- Added local app diagnostics logging.
- Added exportable diagnostic reports including app logs and MetricKit data.
- Added diagnostic log filtering.
- Added clearer controls for diagnostics collection.
- Added app distribution information to diagnostic exports.
- Added stronger redaction for sensitive diagnostic values.
- Moved diagnostics into a dedicated Settings sheet.

### Events & Monitoring

- Added segment utilization events.
- Added day grouping for the Events timeline.
- Added richer device event filters and event details.
- Added SNR affected channel context to event details.
- Added better handling for unsupported DOCSIS error counters.
- Improved event labels, localization, and detail formatting.
- Fixed Channel Compare selection.

### Dashboard & Refresh Behavior

- Improved Dashboard pull-to-refresh behavior and loading feedback.
- Improved modem poll state handling.
- Improved connection info readability.
- Improved affected-channel and signal summary presentation.
- Added clearer last-updated feedback while pulling to refresh across data views.
- Removed redundant refresh timestamp footers.
- Further refined Dashboard card layout, connection info readability, and status presentation.

### Settings & User Experience

- Reworked the Settings screen structure.
- Added confirmation dialogs for logout actions.
- Improved custom Settings row interaction behavior.
- Added clearer and more compact background refresh settings.
- Improved Apple Watch settings visibility when no watch is paired.
- Improved diagnostics settings clarity.

### Snapshots

- Improved snapshot timeline loading stability.
- Improved snapshot list and detail behavior.

### Security & Reliability

- Hardened API URL handling.
- Improved Keychain token storage behavior.
- Improved local cache cleanup after logout or authentication failure.
- Added safer handling for temporary exported files.
- Improved handling of unauthenticated backend setups.
- Improved app state refresh behavior for diagnostics and status indicators.
- Improved StoreKit app transaction handling.

### Apple Watch & Widgets

- Improved Apple Watch support for local HTTP backends.
- Improved Watch data synchronization.
- Improved Watch dashboard and settings behavior.
- Improved widget data fetching behavior.
- Refined Apple Watch typography and dashboard presentation.

### Charts & Data Presentation

- Improved SNR-related chart and event formatting.
- Improved presentation of unavailable or unsupported signal/error metrics.
- Improved event-derived tooltip and detail formatting.

## 1.1 (Build 93) - 2026-04-12

### iOS

#### Added
- Refine home screen widgets with improved layout and refresh button
- Add hide/show toggle for bar chart series in error trends chart
- Add severity threshold selection for live activity auto-start
- Clear notifications, badge, and Live Activity on logout
- Add confirmation dialog before marking all events as read

#### Fixed
- Localize connection monitor events in correlation chart tooltip

### Apple Watch

#### Added
- Add watch dashboard card configuration with hide/show toggle and iPhone sync
- Add thresholds to watch connection monitor and hide raw resolution badge
- Update bell badge instantly when events are acknowledged on Watch

## 1.0 (Build 1) - 2026-04-06

Initial App Store Release 🎉 Contains no changes since 0.1 (Build 80)

## 0.1 (Build 80) - 2026-04-04

### Improved

Snapshot heatmap health requests are now serialised and debounced — previously multiple visible days would load in parallel causing request bursts; fixes CrowdSec bans when accessing remotely e.g. via Pangolin/Traefik.

## 0.1 (Build 79) - 2026-04-04

Note: Build numbers are now assigned automatically by Xcode Cloud and increment continuously — this is why the jump from build 27 to 79 is larger than usual.

### Added

- Snapshots tab — browse and compare historical modem snapshots with a 24-hour heatmap timeline, health indicators, and scrub tooltip
- Outage timeline in Monitor View showing past outage periods at a glance
- Offline caching for Trends, Speedtest, Broadband, and Modulation — data stays visible when the backend is unreachable
- BQM chart — interactive latency history with lost polls visualization, matching the web UI
- Apple Watch: Segment Utilization card and detail page
- Apple Watch: Monitor page now shows latency and packet loss charts
- Apple Watch: Channel detail for flagged channels with signal metrics and health indicators
- Apple Watch: Speedtest trigger in the Speed page with live status feedback
- Apple Watch: Manual refresh button on the Channels and Channel Detail pages

### Improved

- App and Watch data loads faster due to parallel API requests
- Channel detail loads signal history, thresholds, and weather simultaneously
- Chart scrubbing feels smoother with less work done per touch event
- Apple Watch skips a refresh on wrist-raise if the data was fetched recently
- Reduced memory usage in the image cache

### Fixed

- Modulation health trend chart now correctly shows a 0–100% scale
- Offline banner displayed with correct width in Channels view; duplicate removed from Events view
- Apple Watch: base URL is validated before attempting a connection
- Apple Watch: credentials are properly cleared when resetting the app
- Apple Watch: dashboard card order is correctly synced from the iPhone
- Pasting a URL no longer triggers the iOS clipboard access banner
- Incident PDF reports are cleaned up from storage after sharing
- Various security improvements around credential storage and data protection

## 0.1 (Build 27) - 2026-03-27

### Added

- Segment Utilization: DOCSight's segment utilization data is now surfaced in the app, showing downstream and upstream utilization over time with min/avg/max stats.

## 0.1 (Build 26.1.1) - 2026-03-23

### Added
- Signal Summary card now shows ⓘ buttons next to each metric (DS Power, Signal Clarity/SNR, US Power, Errors) — tapping opens a popover anchored to the icon with a brief explanation, matching the web UI's glossary tooltips
- Packet loss warning notifications are now configurable via a dedicated toggle in Settings → Notifications

### Improved
- Glass cards now correctly re-render when switching Light/Dark Mode while the app is in the background (iOS 26 glassEffect was not tracking color scheme changes)

### Fixed
- Channel picker: selecting/deselecting channels no longer produces duplicates or stale checkmarks (stale closure bug)

## 0.1 (Build 26.0.10) - 2026-03-22

### Added

- Trigger new speedtest directly from the Speedtest tab (with start/done banners and haptic feedback)
- Traceroute support in Connection Monitor
- App Intents support — Early Beta
- Notifications are cleared when acknowledged events are dismissed in iOS or watchOS
- watchOS: completely redesigned as a real companion app — all views rebuilt with a consistent card-based layout. The Dashboard, Monitor, and Trends pages are all new.
- watchOS: range picker (24h / 7d / 30d) on Trends page
- watchOS: speedtest history and timestamps on detail pages
- watchOS: skeleton loader for Events sheet
- watchOS: configurable dashboard card order via iOS Settings

### Improved

- watchOS: data reloads on Events sheet dismiss without triggering an unnecessary modem poll

### Fixed

- Events: app icon badge cleared when events are acknowledged

## 0.1 (Build 25) - 2026-03-16

### Added

- Watch Dashboard — new glance-view page showing channel health (DS/US % healthy), uncorrectable error rate, BNetz broadband measurement, Connection Monitor latency/packet loss, collector status, and last modem poll
- Watch Complication: Health Gauge — new accessoryCircular complication showing signal health state as a color-coded gauge ring with short label
- Watch Complication: SNR Gauge — SNR level shown as a gauge ring, replacing the previous dot indicator
- Watch Page Order — configurable page order from iOS Settings, synced to the Watch via WatchConnectivity
- Comparison Tab — compare signal quality across two custom time periods side by side, with threshold overlays
- Signal Insights — diagnostic cards for backend health issues, accessible as a sheet from the Health Summary card
- Notifications — individual per-event notifications with timestamps, capped at 5

### Improved

- Connection Monitor card header shows average ping at a glance
- Watch Events: tap-to-confirm replaces swipe-to-acknowledge (avoids conflict with page-swipe gesture)
- Channel comparison limit raised to 64 with Select All option

## 0.1 (Build 24) - 2026-03-12

### Added

- Apple Watch app — native watchOS companion with Signal, Gaming, Speedtest, and Events pages; data is fetched directly from the backend via credentials synced from the iPhone app
- Watch complication & Smart Stack — health status complication for watch faces; rectangular Smart Stack widget showing health, gaming score, latest speedtest, and SNR
- Connection Monitor — new tab with a multi-target latency chart, P95/avg/min/max stats, packet loss, per-target detail rows, and a dashboard summary card
- Notification severity filter — choose which severity levels (critical, warning, info) trigger background push notifications; filter applies to both banners and the notification badge count
- Localized notifications — background event notifications are fully localized (EN/DE) and include a "Mark as Read" action

### Improved

- Image viewer (Smokeping, BQM) redesigned close button; swipe-to-dismiss added

### Fixed

- Modulation Detail Sheet prev/next buttons no longer drop taps during loading
- Live Activity not triggered when health changes to "marginal"
- Pull-to-refresh cancellation no longer incorrectly triggers the offline banner
- Notification fallback correctly shows "New Event" when the event payload can't be fetched
- Modulation View no longer shows a double navigation bar

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