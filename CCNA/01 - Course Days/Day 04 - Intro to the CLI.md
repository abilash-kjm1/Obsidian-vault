---
course: Jeremy's IT Lab CCNA 200-301
course_day: 4
status: Not Started
date_started:
date_completed:
tags:
  - ccna/course-day
---

# Intro to the CLI

[⬅️ Day 03](Day%2003%20-%20How%20the%20TCP-IP%20Model%20Actually%20Works.md) · [🏠 Dashboard](../00%20-%20Start%20Here/CCNA%20Dashboard.md) · [🗺️ Roadmap](../00%20-%20Start%20Here/Course%20Roadmap.md) · [Day 05 ➡️](Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201.md)

**Video:** [Intro to the CLI | Day 4](https://www.youtube.com/watch?v=IYbtai7Nu2g) · 31:06 · ▶ links jump to that moment
**Basics used here:** [Cisco Password Types](../Concepts/Cisco%20Password%20Types.md)

> [!abstract] The whole lesson in 3 lines  
> 1. Connect a laptop to the device's **console port** with a **rollover cable**, then open **PuTTY** (9600 baud, 8-N-1).  
> 2. The CLI has floors you climb: **`Router>`** (look) → `enable` → **`Router#`** (inspect and save) → `conf t` → **`Router(config)#`** (change).  
> 3. Protect it with **`enable secret`**, check your work with **`show running-config`**, and **save** it, or it's lost on reboot.

## 1. IOS, CLI and GUI ▶ [0:29](https://www.youtube.com/watch?v=IYbtai7Nu2g&t=29s)

![700](Attachments/Day%2004%20-%20Intro%20to%20the%20CLI-4.png)

- **Cisco IOS** = the operating system on Cisco routers and switches (like Windows on a PC). It has nothing to do with Apple's iOS.
- **CLI** (Command-Line Interface) = you type commands. This is what network engineers use, and what the CCNA tests.
- **GUI** (Graphical User Interface) = click-based tools. These exist (e.g. ASDM for firewalls) but aren't covered.

## 2. Connecting: the Console Port ▶ [1:42](https://www.youtube.com/watch?v=IYbtai7Nu2g&t=102s)

A brand-new device has no network settings, so the **first** configuration is always done **in person**, through the **console port**.

![700](Attachments/Day%2004%20-%20Intro%20to%20the%20CLI-5.png)

A Cisco switch has two console ports: **RJ-45** (looks like a network port, but it isn't one) and **USB mini-B**.

![700](Attachments/Day%2004%20-%20Intro%20to%20the%20CLI-6.png)

For the RJ-45 console port, use a **rollover cable**: RJ-45 on one end, **DB9** serial on the other. Laptops rarely have serial ports now, so add a **DB9-to-USB adapter**.

![700](Attachments/Day%2004%20-%20Intro%20to%20the%20CLI-7.png)

> [!info]- Rollover vs crossover: don't mix them up (click)  
> **Rollover** = the pin order is completely **reversed**: 1 → 8, 2 → 7, 3 → 6, 4 → 5, … 8 → 1. Think of it as the cable "rolled over". It's used **only for console** access.  
> **Crossover** = only the transmit and receive pairs swap: 1 → 3, 2 → 6. It's used for **Ethernet** between same-group devices. → [Day 02](Day%2002%20-%20Interfaces%20and%20Cables.md)

## 3. PuTTY and the Console Settings ▶ [3:50](https://www.youtube.com/watch?v=IYbtai7Nu2g&t=230s)

A **terminal emulator** (e.g. **PuTTY**, putty.org) gives you the text window. Choose **Serial** → **Open**.

![700](Attachments/Day%2004%20-%20Intro%20to%20the%20CLI-8.png)

Cisco's console defaults. **Memorize them for the exam:**

|Setting|Default|
|---|---|
|Speed (baud rate)|**9600** bits per second|
|Data bits|**8**|
|Stop bits|**1**|
|Parity|**None**|
|Flow control|**None**|

> [!tip] Memory trick  
> **"9600, 8-N-1, no flow."** (8 data bits, No parity, 1 stop bit)

On first boot, answer **`no`** to the "initial configuration dialog" and press **Enter**:

![700](Attachments/Day%2004%20-%20Intro%20to%20the%20CLI-9.png)

## 4. The Three CLI Modes ▶ [5:40](https://www.youtube.com/watch?v=IYbtai7Nu2g&t=340s)

> [!tip] Analogy: a building with locked floors  
> **Ground floor** (`>`): you can look around but touch nothing.  
> **Office** (`#`): you can view everything, save, and restart.  
> **Control room** (`(config)#`): you can actually change how the device works.

|Prompt|Mode|You can…|Get here with|
|---|---|---|---|
|`Router>`|**User EXEC**|Look at a few things; no changes|(where you start)|
|`Router#`|**Privileged EXEC**|View the full config, save, reload, set the clock|`enable`|
|`Router(config)#`|**Global configuration**|**Change** the configuration|`configure terminal`|

![700](Attachments/Day%2004%20-%20Intro%20to%20the%20CLI-10.png)

The word before the symbol is the **hostname** (default `Router` on a router).

![700](Attachments/Day%2004%20-%20Intro%20to%20the%20CLI-11.png)

```
Router> enable
Router# configure terminal
Router(config)# exit
Router# exit            ← logs you out
```

## 5. Shortcuts: `?`, Tab and Abbreviations ▶ [7:52](https://www.youtube.com/watch?v=IYbtai7Nu2g&t=472s)

|Key/trick|What it does|
|---|---|
|`?`|Lists the commands available right now|
|`e?` (no space)|Lists commands **starting with** "e" → `enable exit`|
|`enable password ?` (space)|Lists **what can come next**|
|**Tab**|Completes the word|
|Abbreviation|Any unique prefix works: `en` = enable, `conf t` = configure terminal|

![700](Attachments/Day%2004%20-%20Intro%20to%20the%20CLI-12.png)

`e` alone gives **"% Ambiguous command"** because both `enable` and `exit` start with "e". So the shortest forms are **`en`** and **`ex`**.

![700](Attachments/Day%2004%20-%20Intro%20to%20the%20CLI-13.png)

`con?` shows `configure connect`, so you need `conf`. Only `terminal` starts with "t", so **`conf t`** works.

> [!warning] Exam  
> Shortcuts are fine to type, but you must know the **full commands**: `conf t` = **`configure terminal`** (not "configuration terminal").

## 6. Protecting Privileged EXEC with a Password ▶ [10:29](https://www.youtube.com/watch?v=IYbtai7Nu2g&t=629s)

```
Router(config)# enable password CCNA
```

![700](Attachments/Day%2004%20-%20Intro%20to%20the%20CLI-14.png)

Reading the `?` help:
- **`LINE`** in capitals = *you* type something there (here, the password).
- **`<cr>`** = carriage return: nothing more to add, just press Enter.
- Passwords are **case-sensitive**: `CCNA` ≠ `ccna`.

![700](Attachments/Day%2004%20-%20Intro%20to%20the%20CLI-15.png)

When you type the password **nothing appears on screen**. That's intentional. After **3 wrong attempts**: `% Bad secrets`.

## 7. Running-config vs Startup-config ▶ [14:26](https://www.youtube.com/watch?v=IYbtai7Nu2g&t=866s)

![700](Attachments/Day%2004%20-%20Intro%20to%20the%20CLI-16.png)

|File|What it is|When it's used|
|---|---|---|
|**running-config**|The **live** config. Every command edits it immediately.|Right now|
|**startup-config**|The **saved** config|Loaded when the device **restarts**|

> [!tip] Analogy  
> **running-config** = a document open in Word with unsaved changes.  
> **startup-config** = the file on disk.  
> Reboot without saving = close Word without saving: your changes are gone.

> [!info]- Where are they stored? (click)  
> running-config lives in **RAM** (wiped on power-off). startup-config lives in **NVRAM** (non-volatile RAM, which survives power-off). That's exactly why unsaved changes disappear on reboot.

![700](Attachments/Day%2004%20-%20Intro%20to%20the%20CLI-17.png)

```
Router# show running-config
Router# show startup-config     → "startup-config is not present" until you save
```

### Saving: three commands that do the same thing ▶ [15:51](https://www.youtube.com/watch?v=IYbtai7Nu2g&t=951s)

![700](Attachments/Day%2004%20-%20Intro%20to%20the%20CLI-18.png)

```
Router# write
Router# write memory
Router# copy running-config startup-config
```

All run from **privileged EXEC** (`#`). Afterwards, `show startup-config` matches the running-config.

## 8. Encrypting Passwords ▶ [16:58](https://www.youtube.com/watch?v=IYbtai7Nu2g&t=1018s)

`enable password CCNA` sits in the config in **plain text**, so anyone glancing at the screen sees it.

```
Router(config)# service password-encryption
```

![700](Attachments/Day%2004%20-%20Intro%20to%20the%20CLI-19.png)

It now shows as `enable password 7 08026F6028`. The **7** = [type 7](../Concepts/Cisco%20Password%20Types.md) (Cisco's simple scramble). The password itself is still `CCNA`. Only how it's displayed changed.

![700](Attachments/Day%2004%20-%20Intro%20to%20the%20CLI-20.png)

But type 7 is **weak**: a free website reverses it in seconds.

## 9. `enable secret`: the Right Way ▶ [18:51](https://www.youtube.com/watch?v=IYbtai7Nu2g&t=1131s)

```
Router(config)# enable secret Cisco
Router(config)# do show running-config
```

![700](Attachments/Day%2004%20-%20Intro%20to%20the%20CLI-21.png)

- Stored as **type 5** = an **MD5 hash**. That's far stronger, though no password is unbreakable. → [Password types](../Concepts/Cisco%20Password%20Types.md#The%20Types)
- **Always** hashed, with or without `service password-encryption`.
- If both are configured, **`enable secret` wins** and `enable password` is ignored (it stays in the config, unused).

> [!important] Rule  
> **Always use `enable secret`**, never `enable password`.

> [!info]- What does `do` do? (click)  
> `show` commands belong to privileged EXEC (`#`). In config mode they're normally rejected. Putting **`do`** in front runs them without leaving config mode: `do show running-config`, or shortened, `do sh run`.  
> ⚠️ The video's review slide says `run`. That's a mistake (the video notes the erratum). The command is **`do`**.

## 10. Undoing a Command with `no` ▶ [20:47](https://www.youtube.com/watch?v=IYbtai7Nu2g&t=1247s)

Put **`no`** in front of a command to remove it:

```
Router(config)# no service password-encryption
```

![700](Attachments/Day%2004%20-%20Intro%20to%20the%20CLI-22.png)

Existing type-7 passwords **stay encrypted**. They are **not** decrypted.

![700](Attachments/Day%2004%20-%20Intro%20to%20the%20CLI-23.png)

|`service password-encryption`|Current passwords|Future passwords|`enable secret`|
|---|---|---|---|
|**Turned on**|Encrypted (type 7)|Encrypted|Not affected (always hashed)|
|**Turned off** (`no …`)|**Stay encrypted**|Plain text|Not affected (always hashed)|

## 11. Command Sheet

|Command|Mode|Does|
|---|---|---|
|`enable`|`>`|Enter privileged EXEC|
|`configure terminal` (`conf t`)|`#`|Enter global config|
|`exit`|any|Go up one level / log out|
|`enable password <pw>`|config|Plain-text enable password (avoid)|
|`enable secret <pw>`|config|Hashed enable password (**use this**)|
|`service password-encryption`|config|Type-7-encrypt plain passwords|
|`no <command>`|config|Remove a command|
|`do <exec command>`|config|Run a `#` command from config mode|
|`show running-config` (`sh run`)|`#`|Show the live config|
|`show startup-config`|`#`|Show the saved config|
|`write` / `write memory` / `copy running-config startup-config`|`#`|Save|

## 12. Test Yourself

Answer first, then click to check.

> [!question]- Which cable connects to a Cisco RJ-45 console port?  
> A **rollover cable**. Crossover is for Ethernet. USB uses the separate USB console port.

> [!question]- What are Cisco's default console settings?  
> **9600 baud, 8 data bits, no parity, 1 stop bit, no flow control.**

> [!question]- Your enable password is rejected, though you're sure it's right. Likely cause?  
> **Caps Lock is on.** Passwords are case-sensitive. (`service password-encryption` doesn't change the password itself.)

> [!question]- What's the most secure way to protect privileged EXEC mode?  
> **`enable secret`**: it's always hashed (type 5 / MD5).

> [!question]- Both `enable password` and `enable secret` are set. What must you type?  
> **Only the enable secret.** It takes precedence.

> [!question]- What is the full version of `conf t`?  
> **`configure terminal`**

> [!question]- You configured a device all morning and then the power failed. All your work is gone. Why?  
> You never **saved**. Changes live in the running-config (RAM), and reboot loads the startup-config (NVRAM).

> [!question]- You're at `Router(config)#` and want to view the config without leaving. What do you type?  
> **`do show running-config`**

> [!question]- You run `no service password-encryption`. What happens to an existing `enable password 7 …`?  
> Nothing. It **stays encrypted**. Only passwords configured from now on stay in plain text.

> [!question]- What does `Router#` tell you?  
> Hostname = **Router**, mode = **privileged EXEC** (`#`).

---

## 🧪 Lab Video (notes not made yet)

**Basic Device Security - Day 4 Lab** · 10:26 · [Watch on YouTube](https://www.youtube.com/watch?v=SDocmq1c05s)

- [ ] Watched
- [ ] Lab completed
