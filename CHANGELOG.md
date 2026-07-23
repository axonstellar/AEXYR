# Changelog

All notable changes to Æxyr will be documented in this file.

---

## [1.0.5] — 2026-07-23
### Security
- XOR-obfuscated encryption passphrase and split salt storage in `crypto.py` to prevent extraction via `strings` on compiled binaries

### Fixed
- **License system hardening**: Atomic trial file writes via `os.replace()` to eliminate race-condition resets; retry-before-delete on decryption failures; VERSION byte normalization in key derivation; file locking with `fcntl.flock()`; unified install ID; trial reset logging
- **Licensed badge timing fix**: Replaced silent DOM query with MutationObserver to reliably display the licensed Æ badge regardless of async sidebar component load timing

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
