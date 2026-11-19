# tracecheck

**What is it?**  
`tracecheck` is a **read-only** process and log-awareness utility for Grey Hack. When you connect to a machine (or check your own), `tracecheck` quickly tells you:
- Who is active on the machine (specifically flagging any **`dsession`** process, which indicates an active user/admin session and potential **Active Trace**).
- Whether `/var/system.log` (and `/server/transactions.log` if present) exists, who owns it, and how large it is.

---

## Is It Safe to Run?
Yes. `tracecheck` only **reads** process lists and file metadata — it does not modify logs or kill processes.

---

## Requirements
- No extra libraries required.
- Latest version: `V2` (removes binary `get_content` attempt from `V1`).

---

## How to Build & Run (In-Game)
1. Copy the `.src` file into your Grey Hack computer (for example, `/home/YourUser/src/tracecheck.src`).
2. Compile it in Terminal:
   ```text
   build /home/YourUser/src/tracecheck.src /bin
   ```
3. Run it:
   ```text
   tracecheck
   ```

---

## What the Output Shows
- **Host / IP header:** Current hostname, local IP, and public IP.
- **`[ ACTIVE PROCESSES ]`:** Full process list (`show_procs`) plus a `[!] WARNING` banner if any `dsession` is active.
- **`[ SYSTEM LOG (/var/system.log) ]`:** File owner, size in bytes, and a reminder that `/var/system.log` is a binary log (use `LogViewer.exe` as `root` to inspect or clear it).
