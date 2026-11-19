# PING-SCOUT — Changelog

All notable changes to PING-SCOUT are documented in this file.

PING-SCOUT is a read-only Grey Hack reconnaissance and network-inventory utility developed for the PINGTOWER system.

Development follows the progression:

**Research → Draft → Test → Game-Tested → Stable**

A version is not considered stable until it has undergone sufficient testing and has been explicitly approved.

---

## [Unreleased]

### Planned
- Evaluate optional output filtering or compact mode if needed.
- Await owner approval before designating `0.5` as `Stable`.

---

## [0.5] — Game-Tested

### Added
- Optional `target_ip` CLI parameter (`ping-scout [target_ip]`) to scout a remote router and its LAN without modifying anything (`External-source` API behavior pending in-game verification).
- `-h` / `--help` usage output.
- Router forwarded/used ports section (`router.used_ports`) showing port number, `OPEN`/`CLOSED` state, target LAN IP (`port.get_lan_ip`), and service info.
- Router firewall rules section (`router.firewall_rules`).
- Router `ESSID` and `BSSID` reporting when present.
- `OPEN` vs. `CLOSED` port state tracking (`closedPortCount` separated from `openPortCount`).

### Improved
- Added null and `typeof()` guards for `get_shell`, `host_computer`, `get_router`, `used_ports`, `firewall_rules`, and `devices_lan_ip` to prevent runtime crashes.
- Compacted per-port output to one line (`<port> [<state>] -> <service>`) for cleaner readability.

### Verified (Grey Hack `v0.9.7398 - BETA`)
- **Local mode (`pingscout`):** Compiled and ran cleanly; enumerated local system info, router `192.168.0.1` (`ESSID`/`BSSID`), 3 forwarded ports, firewall rules, and 10 LAN devices (`5` open ports, `10` closed ports, `15` identified services, `0` unavailable).
- **Remote mode (`pingscout <target_ip>`):** Compiled and ran cleanly; enumerated remote router kernel, `ESSID`/`BSSID`, forwarded port `80 [OPEN]`, firewall rules, and 8 LAN devices (`1` open port, `3` closed ports, `4` identified services, `0` unavailable).
- Promoted to root `PING-SCOUT.src` (`Game-Tested`; `Stable` designation awaits explicit owner approval).

---

## [0.4] — Runtime Verified

### Fixed
- Restored the original `router.port_info(port)` call, passing the port object rather than its numeric port number.
- Corrected the service-identification regression introduced in 0.3.

### Verified
- Successfully compiled and executed in Grey Hack.
- Completed two consecutive successful runtime tests.
- Discovered 8 LAN devices in both runs.
- Enumerated 9 open ports in both runs.
- Identified all 9 services in both runs.
- Successfully classified HTTP, FTP, and SSH services.
- Confirmed zero unavailable service identifications.
- Confirmed zero unavailable port scans.
- Both runs produced identical scan results.
- No runtime errors observed.

### Service Breakdown
- HTTP: 5
- FTP: 2
- SSH: 2
- Other: 0

### Notes
- Service identification and string-based classification are now runtime verified.
- Repeatability has been confirmed across two consecutive runs in the current PINGTOWER network environment.
- Stable status has not yet been designated.

---

## [0.3] — Runtime Verified

### Added
- Service classification counters:
  - HTTP
  - FTP
  - SSH
  - Other
- Per-device port and service reporting.
- Service breakdown in the scan summary.

### Changed
- Expanded the existing 0.2 scan summary with service-type statistics.
- Retained the existing 0.2 counters and reporting.

### Testing
- Successfully compiled in Grey Hack.
- Successfully executed from start to finish.
- Discovered 11 LAN devices.
- Enumerated all 9 open ports.
- No runtime errors observed.

### Known Issues
- Service identification returned `Unavailable` for all 9 open ports.
- The implementation passed the numeric port number to `router.port_info()` instead of the port object.
- Service classification could not be meaningfully verified because service identification failed.

### Resolution
- The service-lookup regression was corrected in 0.4 by restoring the original port-object argument.

---

## [0.2] — Runtime Verified

### Added
- Scan summary with numerical counters.
- LAN device discovery count.
- Local active port count.
- Total LAN open port count.
- Devices with and without open ports.
- Unavailable port scan tracking.
- Identified and unavailable service counts.

### Improved
- More informative scan completion report.
- Counter consistency checks against discovered devices and services.

### Testing
- Successfully compiled in Grey Hack.
- Successfully executed from start to finish.
- Verified against the PINGTOWER multiplayer environment.
- Counter results manually checked against scan output.

---

## [0.1] — Initial Working Version

### Added
- Initial PING-SCOUT reconnaissance utility.
- Local computer information gathering.
- Local active port inspection.
- Router information gathering.
- LAN device discovery.
- Remote device open-port inspection.
- Service and version identification.
- Completion footer.

### Testing
- Successfully compiled in Grey Hack.
- Successfully executed from start to finish.
- Confirmed working against the PINGTOWER multiplayer environment.

---

## Development Notes

- PING-SCOUT is intended to remain read-only.
- No automatic exploitation, remote login, file modification, or destructive operations.
- Unavailable information must be distinguished from confirmed negative results.
- New GreyScript functionality must be verified in-game before being classified as game-tested.
- Experimental versions belong in `Drafts/`.
- The root `Ping-Scout/` directory is reserved for the finalized script and its supporting documentation.
- Version history must reflect actual development and testing results.
- Runtime verification does not automatically confer stable status.
- No version may be designated stable without sufficient testing and explicit owner approval.