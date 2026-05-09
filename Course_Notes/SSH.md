# 42. SSH (Secure Shell)

## Console Port Security

- By DEFAULT, no password us needed to access the CLI of a CISCO IOS DEVICE via the CONSOLE PORT
- You can CONFIGURE a PASSWORD on the *console line*
    - A USER will have to enter a PASSWORD to ACCESS the CLI via the CONSOLE PORT

![image](remote_assets/9609b0af-0fb1-4563-89e4-82b58b29325e.png)

- Alternatively, you can configure the CONSOLE LINE to require USERS to LOGIN using one of the configured USERNAMES on the DEVICE

![image](remote_assets/04588b3a-3640-41af-b19e-41768f63b2bc.png)

---

## Layer 2 Switch Management IP

- LAYER 2 SWITCHES do not perform PACKET ROUTING and build a ROUTING TABLE. They are NOT IP ROUTING aware
- However, you CAN assign an IP ADDRESS to an SVI to allow REMOTE CONNECTIONS to the CLI of the SWITCH (using Telnet or SSH)

![image](remote_assets/64a9e983-f353-4670-8a99-1e22129eb661.png)

---

## Telnet

- TELNET (Teletype Network) is a PROTOCOL used to REMOTELY ACCESS the CLI of a REMOTE HOST
- TELNET was developed in 1969
- TELNET has been largely REPLACE by SSH, which is MORE Secure
- TELNET sends data in PLAIN TEXT. NO ENCRYPTION(!)

> **Note:** TELNET SERVERS listen for TELNET traffic on TCP PORT 23

![image](remote_assets/9dffe7fb-4fa4-4ee9-90bf-d27461bb5190.png)

---

## Verify Telnet Configuration

![image](remote_assets/e077b5fd-3130-4fb0-9b17-d28bdef665df.png)

---

## SSH

- SSH (Secure Shell) was developed in 1995 to REPLACE LESS SECURE PROTOCOLS, like TELNET
- SSHv2, a major revision of SSHv1, was released in 2006
- If a DEVICE supports both v1 and v2, it is said to run ‘version 1.99’
- Provides SECURITY features; such as DATA ENCRYPTION and AUTHENTICATION

## Check SSH Support

![image](remote_assets/441c38b7-4b79-4c80-8eca-0463960124b6.png)

## Rsa Keys

- To ENABLE and use SSH, you must first generate an RSA PUBLIC and PRIVATE KEY PAIR
- The KEYS are used for DATA ENCRYPTION / DECRYPTION, AUTHENTICATION, etc.

![image](remote_assets/73bd5a86-32da-4ec6-b385-fe5425a72808.png)

## Vty Lines

![image](remote_assets/04e9072f-ccde-476d-a84d-3034e0b39d19.png)

---

## Summary About SSH Configurations

![image](remote_assets/bb6d358f-e742-434b-835c-5c7cd762abdb.png)

![image](remote_assets/bb2e760b-90c3-42a7-93f6-0ccc7e472d00.png)
