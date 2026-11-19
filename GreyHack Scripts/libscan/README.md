# libscan

**What is it?**  
This folder contains GreyScript utilities that use **`metaxploit.so`** to inspect a remote service or router kernel for vulnerabilities and test whether any of them grant access (such as a remote shell).

Instead of buying individual one-off exploits from Hackshop, `libscan` lets you **scan any target library yourself** from the command line and see what each vulnerability requires.

---

## Evolution & Files
1. **`Drafts/scanhttp - V1.src` & `Drafts/testhttp - V1.src`** *(V1 — Hardcoded Prototypes)*  
   - Initial proof-of-concept scripts that scanned `libhttp.so` on port `80` and tested zero-prerequisite `overflow` calls.
2. **`Drafts/libscan - V2.src`** *(V2 — `Game-Tested`)*  
   - Parameterized to accept `<ip> [port]` from the command line (defaulting to port `0` for router kernel scans), removing all hardcoded IPs.
3. **`Drafts/libscan - V3.src`** *(V3 — `Game-Tested` Read-Only Parser)*  
   - Automatically parses `scan_address` output into a clean numbered menu of `(address, value, requirements)`.
   - Prompts you to either press **Enter** (safe read-only exit) or pick a number (with an optional extra argument) to run `metaLib.overflow(...)` and open a `shell` if obtained.

---

## Requirements
- **`/lib/metaxploit.so`** must be installed on your computer (available in Hackshop → Tools).

---

## How to Build & Run (In-Game)
1. Copy the `.src` file into your Grey Hack computer (for example, `/home/YourUser/src/libscan.src`).
2. Compile it in Terminal (for example, into `/bin/libscan`):
   ```text
   build /home/YourUser/src/libscan.src /bin
   ```
3. Run it:
   - **Scan a router kernel (port `0` default):**
     ```text
     libscan <target_ip>
     ```
   - **Scan a specific service port (e.g., HTTP on `80` or SSH on `22`):**
     ```text
     libscan <target_ip> 80
     ```
   - **Show help:**
     ```text
     libscan -h
     ```
