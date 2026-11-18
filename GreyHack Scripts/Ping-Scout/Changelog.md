# PING-SCOUT — Changelog

All notable changes to PING-SCOUT are documented in this file.

PING-SCOUT is a read-only Grey Hack reconnaissance and network-inventory utility developed for the PINGTOWER system.

Development follows the progression:

**Research → Draft → Test → Game-Tested → Stable**

A version is not considered stable until it has undergone sufficient testing and has been explicitly approved.

---

## [Unreleased]

### Planned
- Improve service identification and classification.
- Expand network reconnaissance and inventory reporting.
- Improve output readability and scan summaries.
- Strengthen error handling and reporting of unavailable information.
- Continue prioritizing read-only operation and safe reconnaissance.

---

## [0.4] — Runtime Verified

### Fixed
- Restored the original `router.port_info(port)` call using the port object rather than its numeric port number.
- Restored successful service identification.

### Verified
- Successful compilation and execution in Grey Hack.
- Discovered 8 LAN devices.
- Enumerated 9 open ports.
- Identified all 9 services.
- Successfully classified HTTP, FTP, and SSH services.
- Confirmed zero unavailable service identifications.
- Confirmed zero unavailable port scans.

### Service Breakdown
- HTTP: 5
- FTP: 2
- SSH: 2
- Other: 0

### Notes
- LAN discovery results differed from previous runs.
- No runtime errors observed.

---

## [0.3] — In Development

### Added
- Service classification counters:
  - HTTP
  - FTP
  - SSH
  - Other
- Per-device service reporting.
- Compact service breakdown in the scan summary.

### Changed
- Expanded the existing 0.2 scan summary with service-type statistics.
- Retained all existing 0.2 counters and reporting.

### Testing
- Draft prepared.
- Runtime testing pending.
- String classification using `lower` and `indexOf` requires in-game verification.

---

## [0.3] — Runtime Verified

### Added
- Service classification counters:
  - HTTP
  - FTP
  - SSH
  - Other
- Per-device service reporting.
- Compact service breakdown in the scan summary.

### Changed
- Expanded the existing 0.2 scan summary with service-type statistics.
- Retained all existing 0.2 counters and reporting.

### Testing
- Successfully compiled in Grey Hack.
- Successfully executed from start to finish.
- Discovered all 11 LAN devices.
- Enumerated all 9 open ports.
- No runtime errors observed.
- Service identification returned `Unavailable` for all 9 ports.
- Service classification remains unresolved and requires further investigation.

### Known Issues
- `router.port_info()` service identification worked in 0.2 but did not return usable service information in 0.3.
- New string-based service classification has not yet been independently verified.

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
- Version history must reflect actual development and testing results. Do not label a version stable without sufficient testing.