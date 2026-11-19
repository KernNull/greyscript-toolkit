# SCAN-HTTP — Changelog

All notable changes to the `Scanhttp` scripts (`SCAN-HTTP` and `TEST-HTTP`) are documented in this file.

Development follows the progression:

**Research → Draft → Test → Game-Tested → Stable**

---

## [Unreleased]

### Planned
- Test interactive `overflow` selection in-game on a target service.
- Promote `0.3` to root `LIBSCAN.src` once interactive `overflow` is verified.

---

## [0.3] — Game-Tested (Read-Only Parser Verified)

### Added
- Automatic `scan_address` parser: strips `<b>` tags, extracts `(address, value, requirements)` tuples, and prints a numbered menu.
- Interactive `user_input` overflow prompt: press Enter to exit in read-only mode, or select a numbered entry (with optional extra argument such as LAN IP or password) to execute `metaLib.overflow`, print `typeof(res)`, and launch `res.start_terminal` on a `shell`.

### Fixed
- Fixed parser extracting `"array "` on `"loop in array <value>"` lines by taking the final space-separated token (`parts[-1]`) before `". Buffer overflow."`.

### Verified (Grey Hack `v0.9.7398 - BETA`)
- Compiled and ran `/bin/libscan 192.168.0.1` against `kernel_router.so v1.1.0`; cleanly parsed all 4 vulnerabilities (`ositionpointoffsetmin`, `qualess`, `send_color_star`, `tionx`) with requirements and exited cleanly on Enter.

---

## [0.2] — Game-Tested (`/bin/libscan`)

### Added
- Parameterized CLI arguments: `<ip> [port]` (defaulting `port` to `0` for router kernel scanning when omitted) plus `-h` / `--help` usage output.
- Port parsing with `to_int` and numeric type guard.

### Fixed
- Removed hardcoded target IP from the scanner.
- Fixed `metaexploit.so` typo in error message to `/lib/metaxploit.so`.

### Verified (Grey Hack `v0.9.7398 - BETA`)
- Compiled and ran as `/bin/libscan <router_ip>` against `kernel_router.so v1.1.0` (port `0`); discovered 4 vulnerabilities on `0x1C05C4F8`.
- Confirmed `to_int` port argument handling (`<ip> 80`).

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
