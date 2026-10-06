# Practice Exercises — Module 01: Networking Fundamentals

> Extra hands-on practice with **direct links** to live labs. Authorized / lab use only.
> RatCTF machines open in-browser (Pwnbox — no VPN). **hackxpert labs** (web/API practice): main categories at https://labs.hackxpert.com/ (Injection · XSS · BAC · Request Forgery · File System · Business Logic · Auth) · Course Labs https://labs.hackxpert.com/courseLabs/index.html · API Labs https://labs.hackxpert.com/APIs/index.html · OWASP lab https://owasp.thexssrat.com · Rat API https://ratapi.thexssrat.com/

---

## Exercise 01.1 — DNS zone transfer

**Target machine(s):**
- [dns-lab](https://ratctf.com/challenges/dns-lab)

**Your task:**
- Enumerate DNS on the target and attempt an AXFR zone transfer.
- List every internal hostname the transfer leaks.

**Success criteria:** capture the flag/root and take a proof screenshot (hostname + id/whoami + flag in ONE frame). Note both hashes where applicable.

## Exercise 01.2 — SNMP with the default community

**Target machine(s):**
- [snmp-lab](https://ratctf.com/challenges/snmp-lab)

**Your task:**
- Confirm UDP 161 is open, then test the 'public' community string.
- Dump the MIB and find the credential/flag it exposes.

**Success criteria:** capture the flag/root and take a proof screenshot (hostname + id/whoami + flag in ONE frame). Note both hashes where applicable.

## Exercise 01.3 — Full port + service map

**Target machine(s):**
- [http-lab](https://ratctf.com/challenges/http-lab)
- [smb-ftp-lab](https://ratctf.com/challenges/smb-ftp-lab)

**Your task:**
- On each box map ALL TCP ports + top-100 UDP and identify every version.
- Decide the one service you'd attack first and justify it.

**Success criteria:** capture the flag/root and take a proof screenshot (hostname + id/whoami + flag in ONE frame). Note both hashes where applicable.

---
*[PRACTICE] · The XSS Rat · OSCP Course · Practice only on these authorized lab targets.*