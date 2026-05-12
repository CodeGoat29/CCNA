# CCNA CLI Command Reference Notes

## Cisco CLI Modes

| Mode                      | Prompt            | What It Means                                                               |
| ------------------------- | ----------------- | --------------------------------------------------------------------------- |
| User EXEC Mode            | `Router>`         | Basic viewing mode with limited commands                                    |
| Privileged EXEC Mode      | `Router#`         | Higher-level mode used to view configs, save configs, and run show commands |
| Global Configuration Mode | `Router(config)#` | Mode used to make configuration changes                                     |

---

# CLI Help and Shortcuts

| Shortcut / Command | Description                                  | Example                          |
| ------------------ | -------------------------------------------- | -------------------------------- |
| `?`                | Shows available commands in the current mode | `Router# ?`                      |
| `command ?`        | Shows what can come next in a command        | `Router# show ?`                 |
| `Tab`              | Auto-completes a partially typed command     | `conf` + `Tab` → `configure`     |
| `exit`             | Goes back one mode                           | `Router(config)# exit`           |
| `no`               | Undoes or removes a command                  | `Router(config)# no hostname R1` |

## Important Note

The `?` can be used by itself or inside a command.

```bash
Router# ?
Router# show ?
Router(config)# service ?
```

This helps you see available commands, options, and what the CLI expects next.

---

# Moving Between CLI Modes

| Command              | Description                                                  | Example                      |
| -------------------- | ------------------------------------------------------------ | ---------------------------- |
| `enable`             | Moves from User EXEC mode to Privileged EXEC mode            | `Router> enable`             |
| `configure terminal` | Moves from Privileged EXEC mode to Global Configuration mode | `Router# configure terminal` |
| `exit`               | Moves back to the previous mode                              | `Router(config)# exit`       |

## Example Flow

```bash
Router> enable
Router# configure terminal
Router(config)# exit
Router#
```

---

# Common CLI Commands

| Command Name                    | Description                                      | Cisco Command Example                            |
| ------------------------------- | ------------------------------------------------ | ------------------------------------------------ |
| View available commands         | Shows commands available in the current mode     | `Router# ?`                                      |
| Enter Privileged EXEC mode      | Gives access to higher-level commands            | `Router> enable`                                 |
| Enter Global Configuration mode | Allows you to configure the device               | `Router# configure terminal`                     |
| Exit current mode               | Goes back to the previous mode                   | `Router(config)# exit`                           |
| Set enable password             | Sets a password for Privileged EXEC mode         | `Router(config)# enable password cisco123`       |
| Encrypt passwords               | Encrypts current and future plain-text passwords | `Router(config)# service password-encryption`    |
| Set stronger enable password    | Uses stronger encryption than `enable password`  | `Router(config)# enable secret cisco123`         |
| Undo a command                  | Removes or reverses a command                    | `Router(config)# no service password-encryption` |
| View running config             | Shows the active configuration                   | `Router# show running-config`                    |
| View startup config             | Shows the saved boot configuration               | `Router# show startup-config`                    |
| Save configuration              | Saves running-config to startup-config           | `Router# write`                                  |
| Save configuration              | Same basic purpose as `write`                    | `Router# write memory`                           |
| Save configuration              | Copies active config to startup config           | `Router# copy running-config startup-config`     |

---

# Configuration Files

Cisco devices keep **two separate configuration files** at the same time.

## Running-Config

The **running-config** is the current active configuration on the device.

As you type configuration commands into the CLI, you are changing the running-config.

```bash
Router# show running-config
```

Key idea:

```text
Running-config = active right now
```

---

## Startup-Config

The **startup-config** is the saved configuration that loads when the device restarts.

```bash
Router# show startup-config
```

Key idea:

```text
Startup-config = used after reboot
```

---

# Saving the Configuration

Changes made in the CLI usually affect the **running-config first**.

To keep those changes after a reboot, you must save them to the **startup-config**.

## Option 1

```bash
Router# write
```

## Option 2

```bash
Router# write memory
```

## Option 3

```bash
Router# copy running-config startup-config
```

You may see:

```bash
Building configuration...
```

---

# Password Commands

## Enable Password

Used in Global Configuration mode.

```bash
Router# configure terminal
Router(config)# enable password cisco123
```

This sets a password for entering Privileged EXEC mode.

---

## Service Password Encryption

Encrypts plain-text passwords in the configuration.

```bash
Router# configure terminal
Router(config)# service password-encryption
```

Important notes:

* Encrypts current plain-text passwords
* Future plain-text passwords will also be encrypted
* This encryption is weak
* Better option: use `enable secret`

---

## Enable Secret

Stronger than `enable password`.

```bash
Router(config)# enable secret cisco123
```

Key idea:

```text
enable secret > enable password
```

If both are configured, `enable secret` takes priority.

---

# The `no` Command

The `no` command is used to undo or remove a configuration command.

## Example

```bash
Router(config)# service password-encryption
Router(config)# no service password-encryption
```

Meaning:

```text
service password-encryption = turns it on
no service password-encryption = turns it off
```

---

# The `do` Command

In configuration mode, some Privileged EXEC commands normally do not work.

The `do` command lets you run certain Privileged EXEC commands from configuration mode.

## Example

```bash
Router(config)# do show running-config
```

Instead of exiting back to Privileged EXEC mode first:

```bash
Router(config)# exit
Router# show running-config
```

Key idea:

```text
do = run EXEC-level commands from config mode
```

---

# Must-Know CCNA Summary

| Concept                              | Quick Meaning                          |
| ------------------------------------ | -------------------------------------- |
| `Router>`                            | User EXEC mode                         |
| `Router#`                            | Privileged EXEC mode                   |
| `Router(config)#`                    | Global Configuration mode              |
| `enable`                             | Go to Privileged EXEC mode             |
| `configure terminal`                 | Go to Global Configuration mode        |
| `exit`                               | Go back one mode                       |
| `?`                                  | Show help / available options          |
| `Tab`                                | Auto-complete command                  |
| `no`                                 | Undo a command                         |
| `do`                                 | Run EXEC commands while in config mode |
| `running-config`                     | Active current config                  |
| `startup-config`                     | Saved config loaded after restart      |
| `write`                              | Save the config                        |
| `copy running-config startup-config` | Save running-config to startup-config  |
