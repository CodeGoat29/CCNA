# 44. NAT (Static): Part 1

## Private Ipv4 Addresses (Rfc 1918)

- IPv4 doesn’t provide enough ADDRESSES for all DEVICES that need an IP ADDRESS in the modern world
- The long-term solution is to switch to IPv6
- **There Are Three Main Short-Term Solutions:**
- Cidr
    - PRIVATE IPv4 ADDRESS
- NAT
- **Rfc 1918 Specifies The Following Ipv4 Address Ranges As Private:**
    
    ```
    10.0.0.0 /8       (10.0.0.0 to 10.255.255.255)             CLASS A 
    172.16.0.0 /12    (172.16.0.0 to 172.31.255.255)           CLASS B
    192.168.0.0 /16   (192.168.0.0 to 192.168.255.255)         CLASS C
    ```
    
- You are free to use these ADDRESSES in your NETWORKS. They don’t have to be GLOBALLY UNIQUE

![image](remote_assets/c774460a-0479-40ed-ac62-1e9820960943.png)

---

## Intro to NAT

- NETWORK ADDRESS TRANSLATION (NAT) is used to modify the SOURCE and / or DESTINATION IP ADDRESSES of packets
- There are various reasons to use NAT, but the MOST common reason is to ALLOW HOSTS with PRIVATE IP ADDRESSES to communicate with other HOSTS over the INTERNET
- For the CCNA you have to understand SOURCE NAT and how to configure it on CISCO ROUTERS

![image](remote_assets/11cbc222-4b2d-4283-9a8f-86cfff2e109d.png)

---

## Static NAT

- STATIC NAT involves statically configuring ONE-TO-ONE MAPPINGS of PRIVATE IP ADDRESSES to PUBLIC ADDRESSES

![image](remote_assets/40867b28-66ff-4182-be97-8495a4c2de23.png)

![image](remote_assets/b77177cc-f6e3-434f-87e0-fb5d0fe14c90.png)

![image](remote_assets/daac56f4-5af8-482c-9d1d-63a0fb3bdcb1.png)

## Private IP Cannot Be Mapped to The Same Global IP

## The Second Mapping Will Be Rejected

![image](remote_assets/6dceb3c2-39d6-4299-b08d-90cbddb8d6b3.png)

---

## Static NAT Configurations

![image](remote_assets/1b0d6780-56d8-4ea0-870b-abb65d3a6e66.png)

![image](remote_assets/add755f6-2d2c-4fe8-aae1-6d1aeecb6ea2.png)

Command `clear ip nat translation`

![image](remote_assets/4266d928-0970-4386-82d7-159cc2b02df6.png)

Command `show ip nat statistics`

![image](remote_assets/2e70576f-3879-4ba6-8ffa-307fd0c243c9.png)

---

## Command Review

![image](remote_assets/061f4c43-e755-41e8-b8b4-9e31e0723a19.png)
