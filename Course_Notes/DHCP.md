# 39. DHCP (Dynamic Host Configuration Protocol)

## The Purpose of DHCP

- DHCP is used to allow HOSTS to automatically / dynamically learn various aspects of their NETWORK configuration; without MANUAL / STATIC configuration
- It is an ESSENTIAL part of modern NETWORKS
    - When you connect a phone / laptop to WiFi, do you ask your NETWORK admin which IP ADDRESS, SUBNET MASK, DEFAULT GATEWAY, etc the phone / laptop should use ?
- Typically used for CLIENT devices (workstations, phones, etc)
- DEVICES (such as ROUTERS, SERVERS, etc) are usually MANUALLY configured
- In small NETWORKS (such as Home NETWORKS), the ROUTER typically acts as the DHCP SERVER for HOSTS in the LAN
- In LARGE NETWORKS, the DHCP SERVER is usually a Windows / Linux SERVER

---

## Basic Functions of DHCP

![image](remote_assets/81b1e260-d669-4944-aa7b-5b7e6a505233.png)

![image](remote_assets/8e7ff968-f47f-4877-88ec-451a9828905e.png)

![image](remote_assets/ca9253f6-3e97-42d8-9293-7b271488be78.png)

![image](remote_assets/b4659586-9e8b-482e-a492-fab9f979aa40.png)

![image](remote_assets/bd292766-0a22-4c0a-ac96-0262ba03d720.png)

> **Note:** ALL the IPs are the same because this is Jeremy’s Home ROUTER (it provides all these services)

Command `ipconfig /release`

![image](remote_assets/13c9528b-8ecb-43e3-a3be-9993c03e1fa5.png)

![image](remote_assets/46821c80-1fa1-435c-b71f-f2a81a2a415a.png)

Wireshark capture of the `ipconfig /release` mechanism

![image](remote_assets/f9eb66a1-9c7e-4b5c-9393-9005f51ad172.png)

![image](remote_assets/16e2b443-6ab6-49c4-bfde-2083c7b2185e.png)

---

Command `ipconfig /renew`

![image](remote_assets/de06e7a3-b011-48eb-a5c6-8a6295258fbc.png)

Renewing Process has FOUR messages:

![image](remote_assets/94febcd6-cd2b-4f6d-97db-69e33b1c1c4d.png)

### **1) DHCP Discover**

- Are there any DHCP Servers in this NETWORK? I need an IP ADDRESS ?

![image](remote_assets/70f7fc01-3222-4fec-8bd3-8b96cfbc086f.png)

NOTE the use of DHCP Reserved Ports 67 and 68

2) DHCP OFFER:

- How about THIS IP ADDRESS ?

![image](remote_assets/0f6e38bc-5eb0-4538-b0d1-e5795ee3af3a.png)

- The DHCP OFFER message can be either BROADCAST or UNICAST
- NOTE OPTIONS at the bottom : Message Type, Server ID, Lease Time, Subnet, etc.

### **3) DHCP Request**

- I want to use the IP ADDRESS that was offered

![image](remote_assets/3023a977-2477-42ec-8890-283ef326bad1.png)

### **4) DHCP Ack**

- Okay! You may use THAT ADDRESS

![image](remote_assets/543c77e8-326b-45c6-a149-2f3668dac3ff.png)

---
## DHCP Renew Process Summary

![image](remote_assets/a2f5cc4e-c949-4a8d-a985-29c6631c635e.png)

---

## DHCP Relay

- Some NETWORK engineers might choose to configure each ROUTER to act as the DHCP SERVER for its connected LANS
- However, large enterprises often choose to use a CENTRALIZED DHCP SERVER
- If the SERVER is centralized, it won’t receive the DHCP CLIENTS’ Broadcast DHCP messages
- To FIX this, you can configure a ROUTER to act as a DHCP RELAY AGENT
- The ROUTER will forward the clients’ Broadcast DHCP messages to the remote DHCP SERVER as a Unicast messages

![image](remote_assets/3c0b188e-a120-499e-b089-18740d0d4559.png)

![image](remote_assets/04c380f4-e1b4-46f3-89ab-1c89f16eed7a.png)

---

## Configuring DHCP in Cisco IOS

Commands for configuring DHCP SERVERS in Cisco IOS

![image](remote_assets/5cac378b-2769-4da2-bd46-1bd93dd5d144.png)

Command `show ip dhcp binding`

![image](remote_assets/2cb89226-c24f-4cac-86f0-5cfb5ba16575.png)

![image](remote_assets/4e10257e-2ca8-466f-96fc-f4a02ab319a4.png)

---

## DHCP Relay Agent Configuration in IOS

![image](remote_assets/d1e1df72-85ef-4323-87f4-26cf14132bda.png)

## Relay Agent Must Have Connectivity With DHCP Server

---

## DHCP Client Configuration in IOS

![image](remote_assets/353e553c-b4a5-4f18-818f-3d7a395491b3.png)

---

## Commands Summary

![image](remote_assets/41e4ab84-7d5d-42e6-93d7-4b982976dd16.png)
