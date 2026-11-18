# PING-SCOUT — Changelog

All notable changes to PING-SCOUT are documented in this file.

PING-SCOUT is a read-only Grey Hack reconnaissance and network-inventory utility developed for the PINGTOWER system.

Development follows the progression:

**Research → Draft → Test → Game-Tested → Stable**

A version is not considered stable until it has undergone sufficient testing and has been explicitly approved.

---

## [Unreleased]

### Planned
- Add device-level service summaries.
- Improve network inventory reporting and output readability.
- Expand scan summaries where useful.
- Strengthen error handling and reporting of unavailable information.
- Continue prioritizing read-only operation and safe reconnaissance.

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