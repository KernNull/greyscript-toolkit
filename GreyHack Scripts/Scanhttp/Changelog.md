# SCAN-HTTP — Changelog

All notable changes to the `Scanhttp` scripts (`SCAN-HTTP` and `TEST-HTTP`) are documented in this file.

Development follows the progression:

**Research → Draft → Test → Game-Tested → Stable**

---

## [Unreleased]

### Planned
- Parameterize target IP and port via `params` (`[ip] [port]`) and remove hardcoded mission IP addresses before publishing.
- Generalize into a reusable `metaxploit.so` library scanner/prober for any service (HTTP, SSH, FTP, SQL, router kernel).
- Fix `metaexploit.so` typo in `SCAN-HTTP - V0.1.src` error message (`metaxploit.so`).

---

## [0.1] — Game-Tested (Hardcoded Prototype)

### Added
- `Drafts/SCAN-HTTP - V0.1.src`: Connects via `metaxploit.net_use`, dumps the remote library (`dump_lib`), enumerates vulnerable memory addresses (`scan`), and prints vulnerability details (`scan_address`).
- `Drafts/TEST-HTTP - V0.1.src`: Tests zero-prerequisite `libhttp.so` `v1.1.3` overflow payloads (`0x6BA50096`, `0x60221C11`, `0xA20F5B6`), prints each returned object type (`typeof(res)`), and launches `res.start_terminal` when a `shell` is obtained.

### Verified
- Executed in Grey Hack `v0.9.7398 - BETA` against a target HTTP service on port `80` (`libhttp.so` `v1.1.3`).
- `SCAN-HTTP - V0.1.src` discovered 6 vulnerable memory addresses.
- `TEST-HTTP - V0.1.src` confirmed:
  - `0x6BA50096` (`ositializedelembofa`) → `computer` (`guest`)
  - `0x60221C11` (`siintln`) → `file` (`guest`)
  - `0xA20F5B6` (`elendpointln`) → `shell` (`guest`)
- Also confirmed in-game that GreyScript rejects newlines inside `[ ... ]` list literals (`got EOL() where Comma or RSquare is required`), resolved using `targets.push(...)`.
