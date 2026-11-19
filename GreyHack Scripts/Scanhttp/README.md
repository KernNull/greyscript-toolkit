# Scanhttp (`SCAN-HTTP` & `TEST-HTTP`)

**What is it?**  
This folder contains two small GreyScript utilities that use **`metaxploit.so`** to inspect a remote service for vulnerabilities and test whether any of them grant access (such as a remote shell).

Instead of buying individual one-off exploits from Hackshop, these scripts let you **scan the target library yourself** and see what each vulnerability actually returns.

---

## What Each Script Does
1. **`Drafts/SCAN-HTTP - V0.1.src`** *(Read-only vulnerability scanner)*  
   - Connects to a target IP and port using `/lib/metaxploit.so`.
   - Downloads ("dumps") the library running on that port (for example, `libhttp.so`).
   - Scans the library for vulnerable memory addresses and prints out:
     - Each memory address (like `0xA20F5B6`)
     - The vulnerable string/value name
     - Any prerequisites (such as required library versions, folders like `/Public`, or whether a user/root must be logged in)
2. **`Drafts/TEST-HTTP - V0.1.src`** *(Overflow tester)*  
   - Takes specific `(memory_address, vulnerable_value)` pairs found by `SCAN-HTTP`.
   - Runs `metaLib.overflow(...)` on each one and prints what type of access it returned (`shell`, `computer`, `file`, or `null`).
   - If it gets a `shell`, it automatically opens an interactive terminal on the target.

---

## Requirements
- **`/lib/metaxploit.so`** must be installed on your computer (available in Hackshop → Tools).

---

## Current Status & Limitations
- **v0.1 (`Game-Tested` prototype):** Both scripts currently have a target IP/port hardcoded inside the file as a proof-of-concept from testing against `libhttp.so v1.1.3`.
- **Planned (v0.2):** Update the scripts to accept `[ip] [port]` from the command line so they work against *any* target service without editing the source code.

---

## How to Build & Run (In-Game)
1. Open the `.src` file in `CodeEditor` (or copy it to `/home/YourUser/src/`).
2. *(For v0.1)* Replace the IP and port in `metax.net_use(...)` (and the target pairs in `TEST-HTTP`) with your target's values.
3. Compile in Terminal:
   ```text
   build scan-http.src /home/YourUser
   ```
4. Run the compiled binary from Terminal:
   ```text
   ./scan-http
   ```
