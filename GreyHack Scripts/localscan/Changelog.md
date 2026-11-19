# localscan — Changelog

All notable changes to `localscan` are documented in this file.

Development follows the progression:

**Research → Draft → Test → Game-Tested → Stable**

---

## [Unreleased]

### Planned
- Test local `overflow` privilege escalation during an active mission.
- Promote `V1` to root `localscan.src` once escalation is verified in-game.

---

## [V1] — Game-Tested (Read-Only Scanner Verified)

### Added
- Loads local `.so` libraries via `metaxploit.load(path)` (defaulting to `/lib/init.so`).
- Checks both `/lib/metaxploit.so` and `current_path + "/metaxploit.so"` for portability.
- Reuses the `libscan V3` `scan_address` parser (`parts[-1]`) to list `(address, value, requirements)`.
- Interactive `user_input` overflow prompt with optional extra argument and automatic `start_terminal` on `shell` results.

### Verified (Grey Hack `v0.9.7398 - BETA`)
- Compiled and ran `/bin/localscan /lib/init.so` against `init.so v1.0.4`; cleanly parsed all 28 vulnerabilities and exited cleanly on Enter.
