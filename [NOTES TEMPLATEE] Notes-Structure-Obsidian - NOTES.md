# OSCP Note-Taking in Obsidian — Structure & Templates

> Obsidian is plain Markdown in a local folder ("vault"), so it's fast, offline, and your notes convert straight into the report. This file explains the vault to build, then gives copy-paste templates.
>
> **Golden rule:** capture as you hack. Notes written "later" are notes never written.

---

## 1. Vault structure

Create a vault called **OSCP** with these folders:

```
OSCP/
├── 00-Templates/          ← note templates (Templater/core Templates plugin)
│   └── Machine.md
├── Engagements/
│   └── Exam-2026/
│       ├── _Dashboard.md   ← Dataview table of all machines
│       ├── _Network.canvas ← visual pivot/host map (Canvas core plugin)
│       └── Machines/
│           ├── sputnik.md
│           └── ...
├── Cheatsheets/           ← ports, revshells, privesc, AD
├── Credentials.md         ← every cred found (one table)
└── Attachments/           ← screenshots (set as default attachment folder)
```

In **Settings → Files & Links**: set "Default location for new attachments" to `Attachments`, and enable "Automatically update internal links". In **Settings → Core plugins**: enable **Templates**, **Canvas**, and **Daily notes** (optional).

---

## 2. Plugins worth installing

- **Dataview** (community) — turns your machine notes into a live sortable dashboard from their frontmatter.
- **Templater** (community) — richer templates than the core plugin (auto date, prompts).
- **Kanban** (community) — a drag board of machines by status (Recon → Foothold → Rooted).
- Core **Canvas** — draw the network/pivot map, link host notes onto it.

Everything below works with just the **core Templates + Dataview**; the rest are nice-to-haves.

---

## 3. Per-machine template

Save as `00-Templates/Machine.md`. The `---` block at the top is **YAML frontmatter** — Dataview reads it for the dashboard.

````markdown
---
host: NAME
ip: 10.10.10.x
os: linux            # linux | windows
status: recon        # recon | foothold | rooted | stuck
points: 20
local: false
proof: false
proofshot: false
msf_used: false
foothold:
privesc:
---

# {{title}}  ({{date}})

## Enumeration
- [ ] Full TCP: `nmap -sV -sC -p- --min-rate 5000 <ip> -oN nmap/allports`
- [ ] UDP: `sudo nmap -sU --top-ports 100 <ip>`
- [ ] Web: feroxbuster / nikto / whatweb / robots.txt
- [ ] Quick-checks: FTP anon · SMB null · SNMP public · LDAP bind

```
(paste the ports that matter — not the whole scan)
```

## Foothold
Vector:
1.
```bash
exact command
output proving it worked
```
![[05_foothold_id.png]]

## Privilege Escalation
- [ ] `sudo -l` / `whoami /priv`
- [ ] SUID / capabilities / cron
- [ ] LinPEAS / WinPEAS
```bash
exact escalation command -> id / whoami
```

## Proof ⭐
```bash
hostname && id && cat /root/proof.txt      # Linux
hostname; whoami; type ...\proof.txt        # Windows
```
![[10_root_proof.png]]
- local.txt: `____`   proof.txt: `____`

## Loot & Remediation
- Creds → add to [[Credentials]]
- Findings → remediation: …
````

To spin up a new machine note: **Ctrl/Cmd-N**, then **command palette → "Templates: Insert template" → Machine** (or set a hotkey).

---

## 4. Live dashboard (Dataview)

Put this in `Engagements/Exam-2026/_Dashboard.md`. It builds a sortable table from every machine note's frontmatter — no manual upkeep:

````markdown
# Exam Dashboard

```dataview
TABLE ip, os, status, points, local, proof, proofshot
FROM "Engagements/Exam-2026/Machines"
SORT points DESC
```

## Still need root
```dataview
LIST FROM "Engagements/Exam-2026/Machines" WHERE proof = false
```
````

Change a note's `status:` or tick `proof: true` and the dashboard updates instantly. That's your points tracker.

---

## 5. Credentials (one searchable note)

`Credentials.md` — a single table you can Ctrl-F. Link the source host with `[[wikilinks]]`:

```markdown
| Credential            | Type        | Source     | Works on          | Cracked |
|-----------------------|-------------|------------|-------------------|---------|
| svc_sql : Autumn2021! | password    | [[sputnik]]| ssh, [[ledger]]   | yes     |
| administrator : <NT>  | NTLM hash   | [[ledger]] | winrm dc01        | n/a     |
```

Credential reuse wins boxes — one place to look means you never forget to try a password elsewhere.

---

## 6. Screenshots & callouts

- Paste an image (**Ctrl/Cmd-V**) — it lands in `Attachments/` and embeds as `![[name.png]]`. Rename to `NN_description.png` (`01_nmap`, `10_root_proof`).
- The **root proof** must show **hostname + id/whoami + flag in one terminal, on the target** — screenshot that exact frame.
- Use callouts to make key blocks scannable:

```markdown
> [!warning] Proof
> hostname + id + flag, one frame.

> [!success] Working cred
> svc_sql : Autumn2021! (reused on ledger)

> [!bug] Dead end
> RFI failed — allow_url_include=Off. Pivoted to log poisoning.

> [!todo] Lead
> root cron in /opt/report.sh — not yet exploited
```

---

## 7. Network / pivot map (Canvas)

Create `_Network.canvas`. Drop a card per host, drag your machine notes onto it, and draw arrows for the pivot path (Kali → entry host → internal → DC). For a pivot set, **only the entry host has a known IP** — label internal hosts by name, addresses discovered through the tunnel.

---

## 8. Exam-day flow

1. Duplicate the `Engagements/Exam-2026` folder; create a Machine note per target; kick off all scans.
2. Work the **Kanban board** (or the Dashboard's "still need root" list) — always pick the top-points un-rooted box.
3. Every cred → `Credentials.md`. Every proof → run the one-liner, paste the screenshot, tick `proof: true`.
4. 60-minute rule: no progress → set `status: stuck`, jot the `[!todo]` lead, switch hosts.
5. **Report time:** each machine note is already a report section. Copy the Markdown into the [report template](./OSCP-Exam-Report-Template.md) and `pandoc` it to PDF.

---

## 9. What NOT to do

- ❌ Don't keep notes only in terminal scrollback — gone on box revert.
- ❌ Don't write "got a shell" without the command — not reproducible.
- ❌ Don't screenshot a flag alone — hostname + id + flag together.
- ❌ Don't leave remediation blank "for later" — fill it while fresh.
- ❌ Don't omit partial boxes — a documented foothold still scores.

*Companion to Module 12 — Report Writing · The XSS Rat · OSCP Course. Authorized / lab use only.*
