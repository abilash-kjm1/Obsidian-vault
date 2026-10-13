

---

# Cisco IOS CLI — Complete Study Notes

> [!abstract] The Big Picture  
> Cisco IOS is the operating system used on Cisco routers and switches. The Command-Line Interface (CLI) allows network engineers to view, configure, and manage these devices using text commands.

## 1. Introduction to Cisco IOS and CLI

### What is Cisco IOS?

Cisco IOS is the operating system used on many Cisco routers and switches.

### What is CLI?

CLI stands for **Command-Line Interface**. It allows you to interact with a network device by typing commands.

Network engineers often prefer the CLI because it provides direct access to device configuration and management features.

**Remember:**

- IOS = Operating system.
    
- CLI = Text-based way to control the device.
    
- Router and switch = Network devices that can be managed through the CLI.
    

## 2. Connecting to a Cisco Device

To configure a Cisco device locally for the first time, you may connect through its console port.

![](Attachments/Day%2004%20-%20Intro%20to%20the%20CLI.png)

### Common connection components

- **Console port:** A physical management connection on the device.
    
- **Rollover cable:** Used with compatible RJ-45 console connections.
  ![361](Attachments/Day%2004%20-%20Intro%20to%20the%20CLI-2.png)
    
- **USB-to-serial adapter:** May be required when using serial console hardware with a computer that lacks a serial port.
    
- **USB console cable:** Used with compatible USB console ports.
    ![](Attachments/Pasted%20image%2020261012213618.png)

### Using PuTTY

PuTTY is a terminal emulator that can provide access to the Cisco CLI.

Typical serial settings described in the lesson:

|Setting|Value|
|---|---|
|Connection type|Serial|
|Speed|9600 baud|
|Data bits|8|
|Stop bits|1|
|Parity|None|
|Flow control|None|

> [!tip] Memory trick  
> The console connection is like a direct communication cable between your computer and the network device.

Note: Console connectors and connection settings can vary by device model.

![](Attachments/Day%2004%20-%20Intro%20to%20the%20CLI-3.png)

## 3. The Three Important CLI Modes

Understanding these modes is essential.

|Mode|Example prompt|Purpose|
|---|---|---|
|User EXEC|`Router>`|Limited access and basic inspection|
|Privileged EXEC|`Router#`|Administrative and operational commands|
|Global Configuration|`Router(config)#`|Change device configuration|

### Mode 1: User EXEC

**Prompt:** `Router>`

This is the initial command mode after accessing the CLI.

You can perform limited inspection, but you cannot make general configuration changes.

Command to leave this mode for privileged access:

```
enable
```

### Mode 2: Privileged EXEC

**Prompt:** `Router#`

Enter this mode by typing:

```
enable
```

This mode provides broader administrative access.

You can use commands to:

- View configurations.
    
- Inspect device information.
    
- Save configuration changes.
    
- Perform supported operational tasks.
    

However, general configuration changes require entering a configuration mode.

### Mode 3: Global Configuration

**Prompt:** `Router(config)#`

Enter this mode from Privileged EXEC:

```
configure terminal
```

The abbreviated command commonly used is:

```
conf t
```

This mode allows you to change device-wide settings.

### Remember the mode sequence

```
Router>
   |
   | enable
   v
Router#
   |
   | configure terminal
   v
Router(config)#
```

> [!important] Exam tip  
> `>` means User EXEC.
> 
> `#` means Privileged EXEC.
> 
> `(config)#` means Global Configuration.

## 4. CLI Shortcuts and Help

Cisco IOS provides shortcuts that reduce typing.

### Tab completion

Press `Tab` to complete a command when the entered text is unambiguous.

### Question mark

Type:

```
?
```

The CLI displays available commands or valid options at that point.

### Ambiguous commands

If an abbreviation matches multiple commands, IOS may report an ambiguous command error.

**Remember:**

- `Tab` = command completion.
    
- `?` = command help.
    
- Ambiguous abbreviation = more than one possible match.
    

## 5. Essential Cisco IOS Commands

|Command|Purpose|
|---|---|
|`enable`|Enter Privileged EXEC mode|
|`configure terminal`|Enter Global Configuration mode|
|`show running-config`|Display the active configuration|
|`show startup-config`|Display the saved configuration|
|`copy running-config startup-config`|Save the active configuration|
|`write`|Save the active configuration|
|`write memory`|Save the active configuration|
|`enable password <password>`|Configure a legacy enable password|
|`enable secret <password>`|Configure the enable secret|
|`service password-encryption`|Obscure eligible plaintext passwords|
|`no <command>`|Negate a supported configuration command|

### Viewing configurations

Display the current active configuration:

```
show running-config
```

Display the saved configuration:

```
show startup-config
```

From Global Configuration mode, the lesson also describes using `do` before show commands:

```
do show running-config
```

## 6. Running-config vs Startup-config

This is one of the most important concepts in the lesson.

### Running-config

- The active configuration currently used by the device.
    
- Stored in RAM, as described in the lesson.
    
- Changes made during configuration affect the running configuration.
    
- Unsaved changes may be lost when the device reboots.
    

### Startup-config

- The saved configuration.
    
- Stored in NVRAM, as described in the lesson.
    
- Loaded when the device starts.
    

### Comparison

|Feature|Running-config|Startup-config|
|---|---|---|
|Meaning|Current active configuration|Saved configuration|
|Storage in lesson|RAM|NVRAM|
|Changes during configuration|Updated as you make changes|Not automatically updated by ordinary changes|
|Role during reboot|Unsaved changes can be lost|Loaded during startup|

### Easy memory trick

**Running = what is running now.**

**Startup = what loads when starting.**

### Example

You configure a setting on a router but forget to save it.

If the router reboots before you save, the change may disappear.

That is why saving the configuration is important.

## 7. Saving Configuration Changes

To save the running configuration into the startup configuration, use:

```
copy running-config startup-config
```

The lesson also lists these commands:

```
write
```

```
write memory
```

These are entered from Privileged EXEC mode.

### Recommended workflow

```
1. Make configuration changes.
2. Verify the active configuration.
3. Save the configuration.
4. Check the saved configuration if needed.
```

Example:

```
Router# show running-config
Router# copy running-config startup-config
Router# show startup-config
```

> [!warning] Common mistake  
> Changing a configuration does not automatically mean it has been saved. Remember to save important changes.

## 8. Password Protection

Cisco IOS provides commands for protecting Privileged EXEC access.

### Enable password

```
enable password <password>
```

This configures a legacy password for entering Privileged EXEC mode.

Passwords are case-sensitive. Password characters may not be displayed while you type them.

### Service password-encryption

```
service password-encryption
```

This command obscures eligible plaintext passwords in configuration output.

The lesson describes its use of **Type 7**, a weak and reversible form of obfuscation.

It should not be treated as strong password protection.

### Enable secret

```
enable secret <password>
```

This configures the enable secret to protect Privileged EXEC access.

The lesson describes the older Type 5 / MD5 representation. Newer Cisco software may support different hashing algorithms, so security details depend on the platform and version.

### Comparison

|Feature|Enable password|Service password-encryption|Enable secret|
|---|---|---|---|
|Purpose|Configure a legacy enable password|Obscure eligible plaintext passwords|Configure the enable secret|
|Lesson's security description|Clear text unless otherwise protected|Weak Type 7|Type 5 / MD5 in the lesson|
|Important point|Legacy method|Easily reversed|Takes precedence over enable password according to the lesson|

> [!important] Remember  
> If both `enable password` and `enable secret` are configured, the lesson says that `enable secret` takes precedence.
> 
> For real devices, use the strongest supported configuration recommended for the exact IOS/IOS XE version.

## 9. The `no` Command

The `no` keyword is used to negate or remove a previously configured setting when the command supports it.

Example:

Enable the feature:

```
Router(config)# service password-encryption
```

Disable the feature:

```
Router(config)# no service password-encryption
```

**Remember:** `no` is not a universal undo button. Its effect depends on the command.

## 10. Quick Revision Sheet

Review this section before an exam or practice session.

- Cisco IOS = operating system for Cisco network devices.
    
- CLI = Command-Line Interface.
    
- Console port = local management connection.
    
- PuTTY = terminal emulator.
    
- User EXEC = `>`.
    
- Privileged EXEC = `#`.
    
- Global Configuration = `(config)#`.
    
- `enable` = enter Privileged EXEC.
    
- `configure terminal` = enter Global Configuration.
    
- `Tab` = autocomplete.
    
- `?` = help.
    
- Running-config = active configuration in RAM, according to the lesson.
    
- Startup-config = saved configuration in NVRAM, according to the lesson.
    
- `show running-config` = view active configuration.
    
- `show startup-config` = view saved configuration.
    
- `copy running-config startup-config` = save the configuration.
    
- `service password-encryption` = weak Type 7 obfuscation in the lesson.
    
- `enable secret` = preferred over `enable password` in the lesson.
    
- `no <command>` = negate a supported configuration command.
    

## 11. Active Recall Flashcards

Try to answer before revealing each answer.

### Q1. What does CLI stand for?

Answer: Command-Line Interface.

### Q2. What symbol identifies User EXEC mode?

Answer: `>`

### Q3. Which command enters Privileged EXEC mode?

Answer: `enable`

### Q4. Which command enters Global Configuration mode?

Answer: `configure terminal`

### Q5. What is the difference between running-config and startup-config?

Answer: Running-config is the active configuration; startup-config is the saved configuration loaded during startup.

### Q6. Which command saves the running configuration?

Answer: `copy running-config startup-config`

### Q7. What does the question mark do?

Answer: It displays available commands or valid syntax options.

### Q8. Why is Type 7 weak?

Answer: It is reversible and should not be treated as strong encryption.

### Q9. What happens when both enable password and enable secret are configured?

Answer: According to the lesson, enable secret takes precedence.

### Q10. What does the `no` keyword do?

Answer: It negates or removes a supported configuration command.

## 12. Practice Quiz

Answer these questions without looking at your notes.

1. You see `Switch#`. Which mode are you in?
    
2. Which command takes you from `Router>` to `Router#`?
    
3. Which command takes you from `Router#` to `Router(config)#`?
    
4. What can happen if you reboot before saving configuration changes?
    
5. Which command displays the active configuration?
    
6. Which command displays the saved configuration?
    
7. What does pressing Tab do?
    
8. What does `service password-encryption` do?
    
9. Which password command takes precedence according to the lesson?
    
10. What is the purpose of the `no` keyword?
    

### Quiz Answers

1. Privileged EXEC mode.
    
2. `enable`
    
3. `configure terminal`
    
4. Unsaved changes may be lost.
    
5. `show running-config`
    
6. `show startup-config`
    
7. Completes a command or abbreviation.
    
8. Obscures eligible plaintext passwords using the method described in the lesson.
    
9. `enable secret`
    
10. Negates a supported configuration command.
    

## 13. Common Mistakes

- Confusing `>` and `#`.
    
- Trying to make general configuration changes without entering a configuration mode.
    
- Forgetting to save the running configuration.
    
- Treating Type 7 as secure encryption.
    
- Assuming every Cisco device has identical console ports or software features.
    
- Assuming the `no` keyword works identically with every command.
    