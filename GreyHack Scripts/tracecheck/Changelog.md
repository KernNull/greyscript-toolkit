# tracecheck — Changelog

All notable changes to `tracecheck` are documented in this file.

Development follows the progression:

**Research → Draft → Test → Game-Tested → Stable**

---

## [Unreleased]

### Planned
- Verify `V2` on a remote target during an active mission.
- Promote to root `tracecheck.src` once verified.

---

## [V2] — Draft (Pending In-Game Test)

### Changed
- Removed `get_content` line-printing on `/var/system.log` and `/server/transactions.log` after confirming in `V1` that `/var/system.log` is a binary file (`"can't open /var/system.log. Binary file."`).
- Reports owner, size, and `LogViewer.exe` usage note instead.

---

## [V1] — Game-Tested

### Added
- Displays current host, local IP, and public IP.
- Enumerates active processes via `host_computer.show_procs` and flags any `dsession` process.
- Checks `/var/system.log` (and `/server/transactions.log` if present) metadata (`owner`, `size`).

### Verified (Grey Hack `v0.9.7398 - BETA`)
- Compiled and ran `/bin/tracecheck`; cleanly listed active processes, verified `dsession` check (`[OK] No dsession processes detected.`), and confirmed `/var/system.log` is a binary file when read with `get_content`.
