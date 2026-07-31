# Changelog

All notable changes to Æxyr will be documented in this file.

---

## [1.0.6] — 2026-07-31
### Fixed
- **Trial countdown reset bug (critical)**: Resolved an issue where simultaneously-launched instances showed divergent trial countdowns, with some resetting to ~9d23h on page refresh
  - **Root cause**: `_read_version_file_bytes()` silently falling back to `b"unknown"` on transient VERSION file I/O errors, producing a wrong Fernet decryption key — combined with WSGIMiddleware thread pool concurrency allowing race conditions on `.trial` file operations
  - Cached Fernet encryption key at module load (`_CACHED_TRIAL_KEY`) — VERSION file now read exactly once per process lifetime, eliminating transient I/O failure modes
  - Added `threading.Lock()` around `check_trial()` to serialize concurrent thread access, preventing race conditions on `.trial` file read/create operations
  - Added error-level logging when VERSION file read falls back to `b"unknown"`, making silent failures visible in logs

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
