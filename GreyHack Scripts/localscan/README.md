# localscan

**What is it?**  
`localscan` is a local library vulnerability scanner and privilege-escalation helper for Grey Hack. Once you have a shell on a machine (for example, as `guest`), `localscan` uses **`metaxploit.so`** to inspect local system libraries (like `/lib/init.so`, `/lib/kernel_module.so`, or `/lib/net.so`) and optionally run an `overflow` to see if you can escalate to a higher-privilege user or `root`.

---

## Requirements
- **`/lib/metaxploit.so`** (or `metaxploit.so` in your current working directory).
- Latest version: `V1` (`Game-Tested` on `/lib/init.so`).

---

## How to Build & Run (In-Game)
1. Copy the `.src` file into your Grey Hack computer (for example, `/home/YourUser/src/localscan.src`).
2. Compile it in Terminal:
   ```text
   build /home/YourUser/src/localscan.src /bin
   ```
3. Run it:
   - **Scan `/lib/init.so` (default):**
     ```text
     localscan
     ```
   - **Scan a specific local library:**
     ```text
     localscan /lib/kernel_module.so
     ```
   - **Show help:**
     ```text
     localscan -h
     ```

---

## What It Does
1. Loads the local `.so` file using `metaxploit.load(path)`.
2. Scans and parses all vulnerabilities into a numbered list showing `(address, payload_name, requirements)`.
3. Prompts you to either press **Enter** (safe read-only exit) or pick a `#` to execute `metaLib.overflow(...)` and open a `shell` if one is returned.
