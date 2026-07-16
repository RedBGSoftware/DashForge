# Changelog

All notable changes to DashForge will be documented in this file.

---

## v1.1.0 - Upcoming

### Added

- Full logging system with file output, log levels, and in-app log panel
- Log panel timestamps and message type display
- UDP listener start/stop control in the app
- UDP forwarder with global enable, per-target enable, forward-only mode, and loop protection
- Configurable telemetry UI refresh rate to cap dashboard rendering without dropping packets
- Dashboard categories and tags with backward-compatible saved dashboard metadata
- Dashboard Manager search and category filtering
- Dashboard action button widget with extensible DashForge actions
- Action Button button-box skins: push button, on/off, start engine, rocker, and toggle lever
- Action Button active/idle colors and configurable label placement
- Built-in template store for dashboards, game profiles, and sample replays
- Store install/uninstall workflow with path support from template `index.json`
- Recording import/export for `.dfrec` files
- Recording metadata cache for faster Replay and Sessions loading
- Recording metadata, notes, and backward-compatible `.dfrec` enrichment
- Sessions system for grouping recordings, notes, metadata, tags, and linked `.dfrec` files
- Session CRUD, recording linking, filtering, cleanup of missing recording references, and relative recording paths
- Cached session analysis stored in `.dfsession` files
- Extensible session analysis engine with driving metrics, coaching events, and track trace generation
- Clickable analysis trace points, event filtering/sorting, fixed-height event list, and contextual advice text
- Live Trace widget using the same analysis engine for real-time trace and driving events
- Live Trace widget options for event icons, event details, auto show, auto close delay, and voice event announcements
- Mini circuit/timing widget
- Telemetry Tile widget for configurable telemetry fields and colors
- Widget catalog reorganization by functional category
- Add Widget search and category filtering
- Shared top info bar component for Dashboard, Data, and Replay
- Central reusable notification system with typed, animated, auto-dismissing toasts
- Dashboard Builder sheets harmonized with the dark DashForge visual style
- Bridge command control through the Dashboard Action Button widget
- Bridge command protocol for keyboard, Win32 virtual-key, and mouse actions
- Native Assetto Corsa profile and parser
- Native Assetto Corsa Competizione profile and parser
- Native F1 24 profile and parser
- Native F1 25 profile and parser
- Stateful F1 UDP aggregation across Motion, Lap Data, Car Telemetry, Car Status, and Motion Ex packets
- Configurable UDP and serial hardware output with selectable telemetry fields
- Hardware presets for shift lights, gear displays, mini dashboards, and custom packets
- Bonjour discovery of nearby DashForge instances
- Secure request/accept handshake before peer file payload transfer
- Peer transfer for dashboards, recordings, and sessions with linked `.dfrec` files
- Transfer progress UI and automatic library refresh after import
- Automatic UDP forward targets from discovered DashForge peers
- Floating performance overlay for FPS, UI Hz, packet rates, CPU, memory, RSS, and network throughput
- Runtime cache/log cleanup action in Settings and the performance overlay

### Changed

- Replay controls were simplified and restyled for compact and regular layouts
- Recording controls now combine start/stop behavior into a stateful primary action
- Replay rows now highlight active playback
- Replay, Data, and Sessions screens now keep primary controls fixed while content scrolls independently
- Data Explorer now distinguishes changing, supported-stable, and unsupported telemetry fields
- Settings sections were restyled for a cleaner Apple-like layout
- Settings were split into focused tabs
- Sessions library panel can be collapsed
- Session sheets now keep header/footer actions fixed while scrolling only the form content
- Add Widget and Dashboard Manager sheets now keep stable macOS dimensions during filtering
- Dashboard popup sizes were tuned separately for macOS and iOS
- Widget categories were aligned between source folders and the Add Widget UI
- Dashboard categories are stored as free strings so future categories can be added without code changes
- Live analysis is shared across Live Trace widgets and only runs while an analysis widget is visible
- Recording and session lists keep cached content visible while refreshing in the background
- Inactive application tabs no longer observe high-frequency telemetry state

### DashForge Bridge

- Added Windows bridge for forwarding raw telemetry data over UDP
- Added Assetto Corsa shared-memory forwarding
- Added Assetto Corsa Competizione shared-memory forwarding
- Added bridge UI with game/source selection, UDP target settings, runtime stats, and logs
- Added bridge About window
- Added portable single-file Windows release build
- Added optional Windows installer build with Start Menu, command-listener, and admin shortcuts
- Added command listener with configurable UDP port
- Set the default bridge source to `all` (`physics + graphics + static`)
- Bridge settings are persisted between launches
- Bridge UI was refined with a DashForge-inspired modern visual style
- Documented hardware-to-Bridge command packets and complete input code behavior
- Clarified that virtual gamepad emulation requires a separate virtual HID/driver layer

### DashForge Lab

- Replaced separate Python simulators with a packaged macOS Swift app
- Added generated telemetry for every built-in DashForge game profile
- Added original-timing and forced-PPS `.dfrec` replay
- Added ESP32 UDP and Arduino-style serial receiver simulation
- Added a generic 3D vehicle simulator with keyboard, mouse, and physical gamepad input
- Added configurable vehicle physics and serialization to any supported game format

### Game Profiles

- Added external JSON profile template for Assetto Corsa
- Added external JSON profile template for Assetto Corsa Competizione
- Expanded the generic UDP parser to support more telemetry fields
- Added mappings for position, velocity, acceleration, orientation, tyres, wheels, suspension, lap timing, race position, fuel, boost, and driver inputs
- Kept Assetto Corsa and Assetto Corsa Competizione profiles external and importable through the generic parser

### Fixed

- Fixed log level changes from the UI causing SwiftUI publishing warnings
- Fixed selected game profile changes not updating the live parser until app restart
- Fixed replay playback using the wrong parser
- Fixed Drive Mode so tapping or clicking anywhere exits fullscreen mode
- Fixed bridge window background rendering during resize
- Fixed replay parser selection for recordings
- Fixed recorder packet counting and zero-byte save regressions
- Fixed replay timing issues for non-Forza recordings
- Fixed Assetto Corsa replay loading/parsing issues
- Fixed live telemetry regression while packets were still received
- Fixed missing session detection after linked recordings were deleted
- Fixed duplicate installs and uninstall detection in the template store
- Fixed dashboard template import by using the existing `.dfdash` archive import path
- Fixed iOS placeholder/text contrast in session editors
- Fixed dashboard retrocompatibility after new widget options were added
- Fixed Live Trace auto-close behavior
- Reduced CPU spikes in Sessions by optimizing trace/event rendering paths
- Fixed self-discovery and duplicate or loop-prone peer forwarder targets
- Fixed session sharing so linked recordings are included
- Fixed imported files requiring an extra tab change before their lists refreshed
- Fixed transfer payloads being sent before receiver confirmation
- Fixed F1 live and replay timing while preserving other game parser behavior
- Fixed background-thread publishing and high-frequency parser logging regressions

### Documentation

- DashForge Bridge build and release guide
- DashForge Bridge command listener and command packet usage notes
- Assetto Corsa and Assetto Corsa Competizione bridge profile notes
- Developer documentation for architecture, telemetry parsers, dashboard widgets, sessions/recordings, and analysis engine extension
- Dashboard metadata compatibility notes
- Store/template index usage notes

---

## v1.0.0 - Initial Release · Published

### Added

- Live UDP telemetry support
- Dashboard Builder
- Replay recording system
- Premium Widgets Pack
- Dashboard import/export
- Custom game profile support
- macOS support
- iOS support

### Premium Widgets

- Race Control
- Car Dynamics
- Vehicle Balance
- Drift Tyre HUD
- G-Force Radar
- Telemetry Graphs

### Supported Games

- Forza Horizon 6

### Documentation

- Getting Started guide
- UDP setup guide
- Import / Export guide
- Custom Game Profiles guide
