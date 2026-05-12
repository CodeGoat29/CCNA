# 4. Intro to The CLI

### What Is a CLI?

- A "Command-line Interface"
- The interface you use to configure Cisco devices

A GUI is a "Graphical User Interface"

### How Do You Connect to a Cisco Device?

- Console Port : When you first configure a device, you have to connect via the Console Port.

![Console port](image-2.png)

You can use a "Rollover cable" : DB9 serial connector to RJ45 OR a DB9 Serial to USB

![image](remote_assets/0527c007-d607-4bef-8ce1-7b18a177614d.png)

### How Do You Actually Access The CLI?

- You need to use a TERMINAL EMULATOR (Example: PuTTy is a popular choice) and connect via "Serial" (default settings)

### Cisco Default Settings Are:

Speed (baud) : 9600 bits/second
Data bits: 8 data bits
Stop bits: 1 stop bit (sent after 8 data bits are sent)
Parity: None
Flow Control: None

---

When you first enter the CLI you will DEFAULT be in what is called 'User EXEC' mode.

### **User Exec Mode**

(Hostname) >		// Prompt looks like THIS //

- User EXEC mode is very limited.
- User can look at some things but can't make ANY changes to the configuration.
- AKA 'User Mode'

Using the 'enable' command, in User EXEC mode, switches you to 'Privileged EXEC' mode.

---

### **Privileged Exec Mode**

- Provides complete access to view the device's configuration, restart the device, etc.
- Cannot change the configuration, but can change the time on the device, save the configuration file, etc.

(Hostname)#		// Prompt looks like THIS //

---

USE a Question Mark (?) to view the available commands in ANY mode. Combining ? with a letter or partial command will list all the commands with those letters.

![image](remote_assets/52454e6f-d5b1-45f0-9a50-e412d356f6d2.png)

USE the TAB key to complete partially entered commands IF the command exists.

---

### Global Configuration Mode:

To enter Global Configuration Mode, enter the command, within Privileged EXEC mode

'configure terminal' (or 'conf t')

Router# configure terminal

Note the prompt change:

Router(config) #		

Type 'exit' to drop back into 'Privileged EXEC' mode.

---

### to Enable Password for User Exec Mode:

Router(config)# enable password (password)

- Passwords ARE case-sensitive.

// This command encrypts plain-text passwords, visible in the config files, using simple encryption.

Router(config)# service password-encryption

If you enable 'service password-encryption'

- Current passwords WILL be encrypted.
- Future passwords WILL be encrypted.
- The 'enable secret' WILL NOT be effected.

If you disable 'service password-encryption'

- Current passwords WILL NOT be decrypted.
- Future passwords WILL NOT be encrypted.
- The 'enable secret' WILL NOT be effected.

// This command enables passwords for the Privileged EXEC mode.

Router(config)# enable secret (password)

// enable secret will ALWAYS be encrypted (at level 5)

---

There are TWO separate configuration files kept on the device at once.

Running-config :

- The current, ACTIVE configuration file on the device. As you enter commands in the CLI, you edit the active configuration.

Startup-config :

- The configuration file that will be loaded upon RESTART of the device.

To see the configuration files, inside 'Privileged EXEC' mode:

Router# show running-config // for running config //

## Or

Router# show startup-config // for startup config //

---

To SAVE the Running configuration file, you can:

Router# write
Building configuration...
## [Ok]

Router# write memory
Building configuration...
## [Ok]

Router# copy running-config startup-config

Destination filename [startup-config]?

Building configuration...
## [Ok]

---

To encrypt passwords:

Router# conf t

Router(config)# service password-encryption

This makes all current passwords *encrypted*

Future passwords will ALSO be *encrypted*

“Enable secret” will not be effected (it’s ALWAYS encrypted)

![image](remote_assets/09c841fe-b5c0-4683-9082-baf060e24c03.png)

Now you will see that the password is no longer in plaintext.

“7” refers to the type of encryption used to encrypt the password. In this case, “7” uses Cisco’s proprietary encryption.

“7” is fairly easy to crack since the encryption is weak.

For BETTER / STRONGER encryption, use “enable secret”

![image](remote_assets/346f3015-9211-47a9-888f-4e02a013a728.png)

“5” refers to MD5 encryption.

Can still be cracked but it’s much much stronger.

Once you use “enable secret” command, this will override “enable password”

---

To CANCEL or delete a command you entered, use the “no” keyword

![image](remote_assets/2978d101-08d4-4ee3-8995-f36aa1c47d15.png)

In this instance, disabling “service password-encryption”:

- current passwords will NOT be decrypted (unchanged)
- future passwords will NOT be encrypted
- the “enable secret” will not be effected

---

![image](remote_assets/e16966a3-674a-4376-bdab-2c06e3659e5f.png)

![image](remote_assets/e449e074-bf4c-40f1-a61e-0442ad83f284.png)

![image](remote_assets/4c1bdf58-7de6-4074-8189-1573a174474c.png)

![image](remote_assets/e7771e65-5ed5-406d-9751-76520713210c.png)

![image](remote_assets/5f7357d4-f44b-4a61-a24c-86f3368f30f7.png)
