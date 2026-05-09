# 49. Port Security

## Intro to Port Security

- PORT SECURITY is a security feature of Cisco SWITCHES
- It allows you to control WHICH SOURCE MAC ADDRESS(ES) are allowed to enter the SWITCHPORT
- If an unauthorized SOURCE MAC ADDRESS enters the PORT, an ACTION will be TAKEN
    - The DEFAULT action is to place the INTERFACE in an “err-disabled” state

![image](remote_assets/92f4ce9b-8fb4-4d57-b200-f41c7d5236ee.png)

- When you enable PORT SECURITY on an INTERFACE with the DEFAULT settings, one MAC ADDRESS is allowed
    - You can configure the ALLOWED MAC ADDRESS manually
    - If you DO NOT configure it manually, the SWITCH will allow the first SOURCE MAC ADDRESS that enters the INTERFACE
- You can CHANGE the MAXIMUM number of MAC ADDRESSES allowed
- A COMBINATION of manually configured MAC ADDRESSES and DYNAMICALLY LEARNED ADDRESSES is possible

![image](remote_assets/0b6e8053-6819-4e02-ae28-4699a5c9c92d.png)

---

## Why Use Port Security?

- PORT SECURITY allows NETWORK admins to control which DEVICES are allowed to access the NETWORK
- However, MAC ADDRESS SPOOFING is a simple task
    - It is easy to configure a DEVICE to send FRAMES with a different SOURCE MAC ADDRESS
- Rather than manually specifying the MAC ADDRESSES allowed on each PORT, PORT SECURITY’S ability to limit the number of MAC ADDRESSES allowed on an INTERFACE is more useful
- Think of the DHCP STARVATION ATTACK (DAY 48 LAB video)
    - The ATTACKER spoofed thousands of fake MAC ADDRESSES
    - The DHCP SERVER assigned IP ADDRESSES to these fake MAC ADDRESSES, exhausting the DHCP POOL
    - The SWITCH’S MAC ADDRESS table can also become full due to such an attack
- Limiting the NUMBER of MAC ADDRESSES on an INTERFACE can protect against those attacks

## Enabling Port Security

![image](remote_assets/b00765c2-f3a1-45be-8ed4-0a8dab68e43e.png)

`show port-security interface`

![image](remote_assets/787959b1-ffad-451d-ac65-11ea9a99db2d.png)

![image](remote_assets/9a6dd39d-130e-411b-be46-ecfe93420813.png)

![image](remote_assets/f071f447-a6ef-4ee6-8a40-2bde94030993.png)

## Re-Enabling an Interface (Manually)

![image](remote_assets/706736d4-ee7c-42b2-b424-6cc30eb50905.png)

## Re-Enabling an Interface (Err-Disable Recovery)

![image](remote_assets/6eb0d808-a989-4261-9b39-1ac9e1bf1460.png)

![image](remote_assets/41d54ef0-7391-473e-9b51-87f44b9e3f3c.png)

---

## Violation Modes

- There are THREE DIFFERENT VIOLATION MODES that determine what the SWITCH will do if an unauthorized FRAME enters an INTERFACE configured with PORT SECURITY
- Shutdown
        - Effectively shuts down the PORT by placing it in an ‘err-disabled` state
        - Generates a SYSLOG and / or SNMP message when the INTERFACE is ‘disabled’
        - The VIOLATION counter is set to 1 when the INTERFACE is ‘disabled’
- Restrict
        - The SWITCH discards traffic from unauthorized MAC ADDRESSES
        - The INTERFACE is NOT disabled
        - Generates a SYSLOG and / or SNMP message each time an unauthorized MAC is detected
        - The VIOLATION counter is incremented by 1 for each unauthorized FRAME
    
- Protect
        - The SWITCH discards traffic from unauthorized MAC ADDRESSES
        - The INTERFACE is NOT disabled
        - It does NOT generate a SYSLOG / SNMP message for unauthorized traffic
        - It does NOT increment the VIOLATION counter
    
---

## Violation Mode - Restrict

![image](remote_assets/819f00b9-9694-442d-8459-8018f4277e45.png)

## Violation Mode - Protect

![image](remote_assets/20d17f97-056e-4e76-8566-bb49c10bb9e1.png)

---

## Secure Mac Address Aging

![image](remote_assets/4454fedf-f942-4b0d-9b6f-074765de653d.png)

- By DEFAULT, SECURE MAC ADDRESSES will not ‘age out’ (Aging Time : 0 mins)
    - Can be configured with `switchport port-security aging time *minutes*`

- The DEFAULT Aging Type is ABSOLUTE
- Absolute
        - After the SECURE MAC ADDRESS is learned, the AGING TIMER starts and the MAC is removed after the TIMER expires, even if the SWITCH continues receiving FRAMES from that SOURCE MAC ADDRESS.
- Inactivity
        - After the SECURE MAC ADDRESS is learned, the AGING TIMER starts but is RESET every time a FRAME from that SOURCE MAC ADDRESS is received on the INTERFACE
            - Aging type is configured with:  `switchport port-security aging type {absolute | inactivity}`
- Secure Static MAC AGING (address configured with `switchport port-security mac-address x.x.x`) is DISABLED by DEFAULT

![image](remote_assets/93f11517-9d97-4e52-89ad-a0e590bca702.png)

---

## Sticky Secure Mac Addresses 

- ‘STICKY’ SECURE MAC ADDRESS learning can be enabled with the following command:
    - `SW(config-if)# switchport port-security mac-address sticky`

- When enabled, dynamically-learned SECURE MAC ADDRESSES will be added to the running configuration, like this:
    - `switchport port-security mac-address sticky *mac-address*`

- The ‘STICKY’ SECURE MAC ADDRESSES will NEVER age out
    - You need to SAVE the `running-config` to `startup-config` to make them TRULY permanent (or else they will not be kept if the SWITCH restarts)
- When you issue the `switchport port-security mac-address sticky` command, all current dynamically-learned secure MAC addresses will be converted to STICKY SECURE MAC ADDRESSES
- If you issue the `no switchport port-security mac-address sticky` command, all current STICKY SECURE MAC ADDRESSES will be converted to regular dynamically-learned SECURE MAC ADDRESSES

![image](remote_assets/10d591f9-334c-4e3b-889e-16030c36c445.png)

---

## Mac Address Table

- SECURE MAC ADDRESSES will be added to the MAC ADDRESS TABLE like any other MAC ADDRESS
    - STICKY and STATIC SECURE MAC ADDRESSES will have a type of STATIC
    - Dynamically-Learned SECURE MAC ADDRESSES will have a type of DYNAMIC
    - You can view all SECURE MAC ADDRESSES with `show mac address-table secure`
    

![image](remote_assets/c9123729-541c-4363-ba19-d8e49f75c6c5.png)

---

## Command Review

![image](remote_assets/716ce91d-d1bb-4f12-a8fd-226b65f22569.png)
