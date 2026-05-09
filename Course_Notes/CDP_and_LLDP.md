# 36. CDP and LLDP (Layer 2 Discovery Protocol)

## Intro to Layer 2 Discovery Protocols

- LAYER 2 DISCOVERY PROTOCOL, such as CDP and LLDP share information WITH and DISCOVER information about NEIGHBORING (Connected) DEVICES

- **The Shared Information Includes:**
    - Hostname
    - IP Address
    - Device Type
    - etcetera.

- **CDP** is a Cisco Proprietary Protocol
- **LLDP** is an Industry Standard Protocol (IEEE 802.1AB)

- Because they SHARE INFORMATION about the DEVICES in the NETWORK, they can be considered a security risk and are often NOT used. It is up to the NETWORK ENGINEER / ADMIN to decide if they want to use them in the NETWORK or not.

![image](remote_assets/65f39e9f-ae1a-42c6-8afb-5e79f939fe5d.png)

---

## Cisco Discovery Protocol (CDP)

- CDP is a Cisco proprietary protocol
- It is enabled on Cisco devices (routers, switches, firewalls, IP Phones, etc) by DEFAULT

> **Note:** CDP Messages are periodically sent to Multicast MAC ADDRESS `0100.0CCC.CCCC`

- When a DEVICE receives a CDP message, it PROCESSES and DISCARDS the message. It does NOT forward it to other devices.
- By DEFAULT, CDP Messages are sent once every **60 seconds**
- By DEFAULT, the CDP hold-time is **180 seconds.** If a message isn’t received from a neighbor for 180 seconds, the neighbor is REMOVED from the CDP Neighbor Table
- CDPv2 messages are sent by DEFAULT

![image](remote_assets/8a0552be-dbc7-4c7b-b011-e32dff75a57e.png)

![image](remote_assets/26e180ec-da08-44d2-bb55-325fdc0c234f.png)

---

## CDP Neighbor Tables

![image](remote_assets/00cd814e-0255-4fac-ac71-3e50054f813c.png)

“Device ID” = What devices were DISCOVERED by CDP

“Local Intrface” = What LOCAL device interface the neighbors are connected to

“Holdtime” = Hold-time countdown in seconds (0 = device removed from table)

“Capabilities” = Refers to Capability Codes table (located above output)

“Platform” = Displays the MODEL of the Neighbor Device

“Port ID” = Neighbor ports that LOCAL device is connected to

---

## More Detailed Output

![image](remote_assets/cd4fbedb-c12f-4e1e-8582-8db16985121f.png)

“Version” = shows what version of Cisco’s IOS is running on the device

---

## Show Specific CDP Neighbor Entry

![image](remote_assets/83ef9488-e82c-4453-ae6e-02575039d0f9.png)

---

## CDP Configuration Commands

![image](remote_assets/393b2680-2304-4c8e-9180-88cc5fefbfd8.png)

- CDP is GLOBALLY ENABLED, by DEFAULT
- CDP is also ENABLED on each INTERFACE, by DEFAULT
- To ENABLE / DISABLE CDP globally: `R1(config)# [no] cdp run`
- To ENABLE / DISABLE CDP on specific interfaces : `R1(config-if)# [no] cdp enable`
- Configure the CDP timer: `R1(config)# cdp time *seconds*`
- Configure the CDP holdtime: `R1(config)# cdp holdtime *seconds*`
- ENABLE / DISABLE CDPv2: `R1(config)# [no] cdp advertise-v2`

 

---

## Link Layer Discovery Protocol (LLDP)

- LLDP is an INDUSTRY STANDARD PROTOCOL (IEEE 802.1AB)
- It is usually DISABLED on Cisco devices, by DEFAULT, so it must be manually ENABLED
- A device can run CDP and LLDP at the same time

> **Note:** LLDP Messages are periodically sent to Multicast MAC ADDRESS `0180.c200.000E`

- When a DEVICE receives an LLDP message, it PROCESSES and DISCARDS the message. It does NOT forward it to OTHER DEVICES
- By DEFAULT, LLDP Messages are sent once every **30 seconds**
- By DEFAULT, LLDP Holdtime is **120 seconds**
- LLDP has an additional timer called the ‘reinitialization delay’
    - If LLDP is ENABLED (Globally or on an INTERFACE), this TIMER will DELAY the actual initialization of LLDP (**2 seconds,** by DEFAULT)

---

## LLDP Configuration Commands

- LLDP is usually GLOBALLY DISABLED by DEFAULT
- LLDP is also DISABLED on each INTERFACE, by DEFAULT

- To ENABLE LLDP GLOBALLY : `R1(config)# lldp run`

- To ENABLE LLDP on specific INTERFACES (tx): `R1(config-if)# lldp transmit`
- To ENABLE LLDP on specific INTERFACES (rx): `R1(config-if)# lldp receive`

YOU NEED TO ENABLE BOTH TO SEND AND RECEIVE (Unless you want to only enable SEND or RECEIVE LLDP Messages)

 

- Configure the LLDP timer: `R1(config)# lldp timer *seconds*`
- Configure the LLDP holdtime: `R1(config)# lldp holdtime *seconds*`
- Configure the LLDP reinit timer: `R1(config)# lldp reinit *seconds*`

![image](remote_assets/25afc5ad-4d82-4472-b282-31ed2a65eae7.png)

![image](remote_assets/78fab926-9fda-4c83-91eb-eda4bf4ec005.png)

## Show LLDP Status

![image](remote_assets/32b11d7b-4050-422e-afd4-bec23e8db3a1.png)

## Show All LLDP Neighbors

![image](remote_assets/85a46d24-5574-4400-bc03-6b0568294940.png)

## Show LLDP Neighbors in Detail

![image](remote_assets/26751ca8-ed54-4e5c-9927-8c6eb0e2e3f7.png)

## Show Specific LLDP Device Entry

![image](remote_assets/b5332838-d112-4556-bee0-c3716a3d4f89.png)

![image](remote_assets/2dd16e33-75a9-4e11-91aa-b507ed490e9b.png)
