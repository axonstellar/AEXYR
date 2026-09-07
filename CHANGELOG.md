# Changelog

All notable changes to Æxyr will be documented in this file.

---

## [1.3.5] — 2026-09-07
### Added
- Neural Cortex knowledge graph: a persistent, interconnected vault of notes that grows with every task, with 3D force-directed visualization and automatic context injection
- Multi-domain SSL certificate management: support for multiple Cloudflare accounts and domains with per-certificate credential routing and automatic domain-to-service binding
- Knowledge vault ships with 92 seed notes across 10 categories, forming a baseline knowledge constellation

### Changed
- Server Rack service control commands now route through the Process Manager for reliable process lifecycle management
- Platform page loaders can be toggled off in settings for instant navigation

### Fixed
- Certificate provisioning error handling for credential file write failures
- Neural Cortex large-graph visibility (camera clipping, adaptive repulsion, velocity clamping)
- Mobile settings modal button positioning
- UI flash on page load eliminated across all visualizer pages
- Various sidebar layout, notification, and tooltip refinements

---

## [1.2.0] — 2026-08-18
### Changed
- Platform-wide visual refresh: light-mode themes for Page Builder, Files, and Terminal; avatar rebrand; theme-aware dashboard banners; login page enhancements; EULA accessibility toggle
- SiteBuild Engram prompt refinements to reduce canvas-literal reproduction bias

### Fixed
- Topology SSL/TLS subtitle now resolves dynamically via JavaScript instead of server-side placeholder

### Security
- Build pipeline hardened: all development documentation double-protected from Docker image via .dockerignore and Dockerfile deletion; dependency isolation preserved for conflicting package versions

---

## [1.0.1 – 1.1.0] — 2026-06-03 through 2026-08-15
### Added
- "No Browser Agent" (NBA) chat button for skipping browser-based task verification

### Changed
- System services managed via supervisorctl; Server Rack hides system service controls from end-users
- Process detection migrated from lsof/ss to direct /proc/net/tcp kernel reads for reliability
- Service lifecycle improvements: intentional stop flags prevent auto-restart of stopped services; extended startup detection window

### Fixed
- Topology node detail panel shows live PID, uptime, CPU, and memory data
- Certificate renewal reliability using certbot certonly with force-renewal
- Agent subordinates now receive the full tools section in their system prompts
- Project services spawn as aexyr-user for proper permission management
- Trial countdown timer accuracy
- Licensed status badge display timing

### Security
- License system hardening: atomic file operations, retry logic, file locking, consolidated identification, and enhanced diagnostics
- Internal encryption key storage hardened against static analysis extraction

---

## [1.0.0] — 2026-06-01
### Released
- Initial platform release
