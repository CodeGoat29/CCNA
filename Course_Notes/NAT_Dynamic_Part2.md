# 45. NAT (Dynamic): Part 2

## More About Static NAT

- STATIC NAT involves statically configuring one-to-one mappings of PRIVATE IP ADDRESSES to PUBLIC IP ADDRESSES
- When traffic from the INTERNAL HOST is sent to the OUTSIDE NETWORK, the ROUTER will translate the SOURCE ADDRESS

![image](remote_assets/60ba15dd-ee70-4bd9-b9a7-febf3ebbcd10.png)

- HOWEVER, this one-to-one mapping also allows EXTERNAL HOSTS to access the INTERNAL HOST via INSIDE GLOBAL ADDRESS

![image](remote_assets/09de8e06-249c-4185-9d09-ca5fc1435f5a.png)

---

## Dynamic NAT

- In DYNAMIC NAT, the ROUTER dynamically maps INSIDE LOCAL ADDRESSES to INSIDE GLOBAL ADDRESSES, as needed
- An ACL is used to identify WHICH traffic should be translated
    - If the SOURCE IP is PERMITTED; the SOURCE IP will be translated
    - If the SOURCE IP is DENIED; the SOURCE IP will NOT be translated
        
        <aside>
> **Note:** However, Packet Traffic will NOT be dropped
        
        </aside>
        
- A NAT POOL is used to define the available INSIDE GLOBAL ADDRESS

![image](remote_assets/98fe2d7d-345c-4d6b-9772-4b152f9bd7a3.png)

  

- Although they are dynamically assigned, the mappings are still one-to-one (one INSIDE LOCAL IP ADDRESS per INSIDE GLOBAL IP ADDRESS)
- If there are NOT enough INSIDE GLOBAL IP ADDRESSES available (=ALL are being used), it is called ‘NAT POOL EXHAUSTION’
    - If a PACKET from another INSIDE HOST arrives and needs NAT but there are no AVAILABLE ADDRESSES, the ROUTER will drop the PACKET
    - The HOST will be unable to access OUTSIDE NETWORKS until one of the INSIDE GLOBAL IP ADDRESSES becomes available
    - DYNAMIC NAT entries will time out automatically if not used, or you can clear them manually

## NAT Pool Exhaustion

![image](remote_assets/59c01575-b42f-475b-9502-2f9ed490ca8d.png)

192.168.0.167 TIMES OUT and 192.168.0.98 is assigned it’s TRANSLATED SOURCE IP

![image](remote_assets/59e68f3b-8acc-4d7e-8d8e-f930dec3be5f.png)

## Dynamic NAT Configuration

![image](remote_assets/6694689a-4880-497c-a1f6-838003810f0c.png)

`show ip nat translations`

![image](remote_assets/5b656147-f61c-4313-9a7e-34bec3ae6fbf.png)

![image](remote_assets/04951fde-f130-43f8-b2ce-05eba6382329.png)

![image](remote_assets/99bb39f3-2ea7-44d2-929e-223755726882.png)

---

## Dynamic Pat (NAT Overload)

- PAT (NAT OVERLOAD) translates BOTH the IP ADDRESS and the PORT NUMBER (if necessary)
- By using a unique PORT NUMBER for each communication flow, a single PUBLIC IP ADDRESS can be used by many different INTERNAL HOSTS
    - PORT NUMBERS are 16 bits = over 65,000 available port numbers
- The ROUTER will keep track of which INSIDE LOCAL ADDRESS is using which INSIDE GLOBAL ADDRESS and PORT

![image](remote_assets/8f720b58-9700-4908-bd8d-a1846191854b.png)

## Pat Configuration (Pool)

![image](remote_assets/2a1acc30-658c-4479-9984-9c620b5e6ce3.png)

`show ip nat translations`

![image](remote_assets/088db6f4-a695-4765-b435-2f20a5e16c9e.png)

## Pat Configuration (Interface)

![image](remote_assets/8a3990ff-c58e-44a9-928d-e534f0cff690.png)

![image](remote_assets/557d0217-80d2-4423-ba6a-041703568e13.png)

`show ip nat translations`

![image](remote_assets/cae56ec7-38b5-4053-beda-ff670083718e.png)

---

## Command Review

![image](remote_assets/fe0655bb-4020-4ddc-bec4-b2fb198e2314.png)
