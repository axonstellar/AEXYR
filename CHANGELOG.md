# Changelog

All notable changes to Æxyr will be documented in this file.

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
