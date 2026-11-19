# pingscout

**What is it?**  
`pingscout` is a **read-only network reconnaissance tool** for Grey Hack. Think of it as an all-in-one "look around the network" utility: it inspects your own computer, your router (or a target IP's router), any forwarded ports, firewall rules, and every device on the local network — without attacking or changing anything.

---

## Is It Safe to Run?
Yes. `pingscout` only **reads** publicly/locally available network info. It does **not** log into machines, run exploits, or edit files.

---

## Requirements
- No extra libraries required (works on a standard Grey Hack computer).
- Latest version: `pingscout.src` (`V5 — Stable / Game-Tested`; draft history `V1`–`V5` in `Drafts/`).

---

## How to Build & Run (In-Game)
1. Copy `pingscout.src` into your Grey Hack computer (for example, `/home/YourUser/src/pingscout.src`).
2. Compile it in Terminal (for example, as `/bin/pingscout` or `/usr/bin/pingscout`):
   ```text
   build /home/YourUser/src/pingscout.src /bin
   ```
3. Run it:
   - **Check your own network:**
     ```text
     pingscout
     ```
   - **Check a remote target IP's router and LAN:**
     ```text
     pingscout <target_ip>
     ```
   - **Show help:**
     ```text
     pingscout -h
     ```

---

## What the Output Shows (Plain-English Breakdown)
- **`[ LOCAL SYSTEM ]`** *(local mode only)*: Your computer's hostname, local/public IP, gateway, active network card, internet status, and how many local ports are open.
- **`[ ROUTER INFORMATION ]`**: The router's local IP, public IP, kernel version (useful for checking router vulnerabilities), and Wi-Fi `ESSID`/`BSSID` if present.
- **`[ ROUTER FORWARDED PORTS ]`**: Which ports the router forwards externally, whether each is `OPEN` or `CLOSED`, which LAN machine it points to, and what service/version is running there.
- **`[ FIREWALL RULES ]`**: Any `ALLOW` or `DENY` firewall rules configured on the router.
- **`[ LAN DEVICE INVENTORY ]`**: Every device connected behind the router, along with its ports (`OPEN`/`CLOSED`) and detected services (like HTTP, SSH, or FTP).
- **`[ SCAN SUMMARY ]`**: A quick count of devices, open/closed ports, and a breakdown of HTTP, FTP, SSH, and other services found.
