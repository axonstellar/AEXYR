# Changelog

All notable changes to Æxyr will be documented in this file.

---

## [1.0.4] — 2026-07-02
### Fixed
- Replaced `lsof`/`ss`-based process detection with direct `/proc/net/tcp` kernel reads for reliable service lifecycle management in containers where `ss` is unavailable
- Added intentional stop flag (`.service_stopped`) to prevent the Process Manager and service reachability engine from auto-restarting services that were intentionally stopped via the API
- Increased service start detection poll window for more reliable startup confirmation

### Changed
- Updated copyright footer from "AxonStellar" to "AxonStellar LLC" across all platform interfaces

## [1.0.3] — 2026-07-02
### Fixed
- Fixed tool prompt discovery in encrypted Docker builds — `get_unique_filenames_in_dirs()` now discovers `.enc` encrypted files, resolving empty `Tools available` section in agent system prompts that prevented subordinate agents from accessing tools like `search_engine` and `document_query`
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
