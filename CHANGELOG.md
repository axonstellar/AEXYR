# Changelog

All notable changes to Æxyr will be documented in this file.

---

## [1.2.0] — 2026-08-18
### Added
- Light-mode themes for Page Builder, Files Parallax Lens, and Terminal Parallax Lens
- Login page circular video reveal animation on successful authentication
- EULA accessibility toggle with high-contrast mode and CSS tooltip
- Page Builder tooltip migration from CSS pseudo-elements to JavaScript DOM for overflow escape

### Changed
- Replaced avatar across login, topology, chat, sidebar, EULA, and license gate with neon Ae emblem
- Dashboard welcome banner updated with light/dark theme variants (WebP RGBA)
- Login page footer consolidated to single centered line with em dash separator
- Asset cleanup removed ~2.4 MB of unreferenced files and optimized images
- SiteBuild Engram prompts refined with 6 fixes addressing canvas-literal reproduction bias

### Fixed
- SSL/TLS topology canvas subtitle now uses dynamic JavaScript lookup from SSL_CONFIG instead of server-resolved placeholder
- Service descriptions no longer reference internal branding in auto-restart text

### Security
- Build security remediation: all root-level development .md files double-protected via .dockerignore exclusion and Dockerfile deletion
- Removed 9 non-essential documentation files from source tree
- Requirements dependency isolation preserved (two-pass install for openai version conflict)

---

## [1.1.0] — 2026-08-15
### Added
- "No Browser Agent" (NBA) button in chat navigation — sends text intervention to skip browser agent usage

### Fixed
- Server Rack system service buttons now hidden from end-users to prevent accidental platform disruption
- System services (nginx, sshd) managed via supervisorctl instead of direct process kill
- Topology node detail panel shows real PID, uptime, CPU, and memory using /proc/net/tcp kernel data
- Certificate renewal uses `certonly --force-renewal` for reliable cert rotation
- Certificate deletion and renewal properly reference configured certbot paths

---

## [1.0.6] — 2026-07-31
### Fixed
- Corrected trial countdown timer

---

## [1.0.5] — 2026-07-23
### Security
- Hardened internal encryption key storage to prevent static analysis extraction from compiled binaries

### Fixed
- **License system hardening**: Atomic file operations to eliminate race-condition state resets; improved error recovery with retry logic; normalized key derivation inputs; added file locking for concurrent access safety; consolidated system identification; enhanced diagnostic logging
- **Licensed badge display fix**: Resolved a timing issue where the licensed status indicator could fail to appear due to asynchronous UI component loading

## [1.0.4] — 2026-07-02
### Fixed
- Replaced `lsof`/`ss`-based process detection with direct `/proc/net/tcp` kernel reads for reliable service lifecycle management
- Added intentional stop flag (`.service_stopped`) to prevent the Process Manager and service reachability engine from auto-restarting services that were intentionally stopped via the API
- Increased service start detection poll window for more reliable startup confirmation

## [1.0.3] — 2026-07-01
### Fixed
- Fixed empty `Tools available` section in agent system prompts that prevented subordinate agents from accessing tools like `search_engine` and `document_query`
- Project services now spawn as `aexyr-user` by default, allowing the agent to manage (stop/restart) its own deployed services without permission errors

## [1.0.2] — 2026-06-14
### Fixed
- License Gate hardening and activation reliability improvements
- Updated trial duration references in the License Gate UI

## [1.0.1] — 2026-06-03
### Fixed
- License Gate security hardening

## [1.0.0] — 2026-06-01
### Released
- Initial platform release
