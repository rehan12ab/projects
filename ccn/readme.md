
# 1-NETWORK DIAGRAM:
![image](https://github.com/user-attachments/assets/a7bfc102-26e6-4c04-a2f6-0c61346db6a1)

-----------------------------------------------------------------------------------------------------------
# 2-ALL CONFIGURATIONS(REMAINING NOT DONE YET)
```console
- Basic setting to all devices plus ssh on router and 13 switches
- Vlan assignment plus all access and trunk port
- switchport security to all 12 switches
- subnetting and ip addressing
- ospf on router and 13 switches
- static ip address to server room devies
- DHCP server device and configuration
- Inter VLAN routing on 13 switches plus IP DHCP helper address
- Wireless networking configuration
- Verifying & testing configurations
```
-----------------------------------------------------------------------------------------------------------
# 3-FIRST FLOOR (ACCESS LAYER)
![image](https://github.com/user-attachments/assets/1b5e6c5c-b806-4898-b3c9-abb2a2790dd0)
- ### MANAGEMENT SWTICH CONFIGURATIONS

![WhatsApp Image 2025-01-02 at 20 59 08_bfaa7370](https://github.com/user-attachments/assets/162a0b36-cacb-4e56-859e-4cf9e7beafa6)

- ### Now after running commands on first switch just run on all rest 11 switches of layer 2

```bash
en
config t
 

hostname layer-2 sw 
banner motd #This is layer-2 sw #

line console 0
password 1234
login 
exit

line vty 0 15
password 1234
login 
exit

no ip domain-lookup
enable password 1234
service password-encryption

do wr
```

![image](https://github.com/user-attachments/assets/3756bfb7-f959-47bd-a195-9bbe324ca679)
![image](https://github.com/user-attachments/assets/2ca95c12-2770-4f61-9ca0-be03b3b20f04)
![image](https://github.com/user-attachments/assets/a8dfeb9f-552f-44dc-a363-867319f757e1)
![image](https://github.com/user-attachments/assets/2cd35e1c-2e18-4071-a1d4-887aced3717f)
![image](https://github.com/user-attachments/assets/1e6cfbcb-dfa7-4e36-a198-4697cc1a1343)
![image](https://github.com/user-attachments/assets/93fae3bf-bdf6-4075-a6f3-3e56efd94711)
![image](https://github.com/user-attachments/assets/97c13973-e65a-4883-8f04-e1b7058f3c6c)
![image](https://github.com/user-attachments/assets/a377cd4f-bd58-40bf-9aae-e5a325af04cc)
![image](https://github.com/user-attachments/assets/3cc36d60-248e-428e-a6ca-e27a2c4e4a57)
![image](https://github.com/user-attachments/assets/2feaf110-f54a-4791-a340-092f32fe6270)
![image](https://github.com/user-attachments/assets/c28c182b-672c-40cd-b54c-b8430862b318)

# REAL TASK START
-----------------------------------------------------------------------------------------------------------
# 1-DISTRIBUTION LAYER MULTI-SWICTH 1
- ### Now after running commands on first switch just run on all rest 4 switches of layer 3 floor 1 **and also add ssh**

```bash
en
config t
 

hostname layer-3-sw
banner motd #This is layer-3-sw #

line console 0
password 1234
login 
exit

ip domain-name hackerssg.net
username hackerssg password 1234
crypto key generate rsa
1024
line vty 0 15
login local
transport input ssh
exit

no ip domain-lookup
enable password 1234
service password-encryption

do wr

```

![image](https://github.com/user-attachments/assets/5aa7b4b4-d7b3-44b2-9055-f490063323da)
![image](https://github.com/user-attachments/assets/81a69928-e2e2-494a-ab3c-bae660c8779b)
![image](https://github.com/user-attachments/assets/463097a0-4238-4740-a8a1-63d39c2b6a31)
![image](https://github.com/user-attachments/assets/bb7eda71-7385-4fc4-a51a-f6b11b519d30)

-------------------------------------------------------------------------------------------------------------------------------------------------------

# 5-CORE LAYER ROUTER 
- ### Now after running commands on first switch just run on all rest 4 switches of layer 3 floor 1 **and also add ssh**

```bash
en
config t
 

hostname core-layer-router
banner motd #This is core-layer-router #

line console 0
password 1234
login 
exit

ip domain-name hackerssg.net
username hackerssg password 1234
crypto key generate rsa
1024
line vty 0 15
login local
transport input ssh
exit

no ip domain-lookup
enable password 1234
service password-encryption

do wr

```

![image](https://github.com/user-attachments/assets/04463b1a-bbd6-4f0f-9793-a88043240000)
![image](https://github.com/user-attachments/assets/9de25601-f6be-470d-83bd-b703a3e51bea)
![image](https://github.com/user-attachments/assets/968fc614-fed8-4c57-9dc7-6c825389518b)
![image](https://github.com/user-attachments/assets/27b8e425-cb88-4db1-ac4e-24b588008e41)

----------------------------------------------------------------------------------------------------------------------------------------


# 2&3- TRUNKING SWITCH PORT AND ASSIGNING VLAN's 

- ### MANAGEMENT SWITCH FLOOR 1
```bash
int range fa0/1-2
switchport mode trunk

vlan 10
name management
exit

int range fa0/3-24
switchport mode access
switchport access vlan 10

switchport port-security
switchport port-security maximum 2
switchport port-security mac-address sticky
switchport port-security violation shutdown

do wr
exit

do sh start

```

![image](https://github.com/user-attachments/assets/d9c061b2-e409-465d-8f3d-53da4cf946b7)



- ### RESEARCH SWITCH FLOOR 1
```bash
int range fa0/1-2
switchport mode trunk

vlan 20
name research
exit

int range fa0/3-24
switchport mode access
switchport access vlan 20

switchport port-security
switchport port-security maximum 2
switchport port-security mac-address sticky
switchport port-security violation shutdown

do wr
exit

do sh start

```
![image](https://github.com/user-attachments/assets/187fc602-ebda-4fbd-8a1c-d1237fd4b96a)



- ### HR SWITCH FLOOR 1
```bash
int range fa0/1-2
switchport mode trunk

vlan 30
name human-resource
exit

int range fa0/3-24
switchport mode access
switchport access vlan 30

switchport port-security
switchport port-security maximum 2
switchport port-security mac-address sticky
switchport port-security violation shutdown

do wr
exit

do sh port-security

```
![image](https://github.com/user-attachments/assets/9c7e76b9-bd48-4402-bba3-630220af6277)


- ### MARKETING SWITCH FLOOR 2
```bash
int range fa0/1-2
switchport mode trunk

vlan 40
name marketing
exit

int range fa0/3-24
switchport mode access
switchport access vlan 40

switchport port-security
switchport port-security maximum 2
switchport port-security mac-address sticky
switchport port-security violation shutdown

do wr
exit

do sh port-security

```
![image](https://github.com/user-attachments/assets/ee25fc11-d3b9-43df-919a-0e12e44074ff)


- ### ACCOUNTING SWITCH FLOOR 2
```bash
int range fa0/1-2
switchport mode trunk

vlan 50
name accounting
exit

int range fa0/3-24
switchport mode access
switchport access vlan 50

switchport port-security
switchport port-security maximum 2
switchport port-security mac-address sticky
switchport port-security violation shutdown

do wr
exit

do sh port-security

```
![image](https://github.com/user-attachments/assets/78898838-5258-4996-9190-9e34152f92ec)


- ### FINANCE SWITCH FLOOR 2
```bash
int range fa0/1-2
switchport mode trunk

vlan 60
name finance
exit

int range fa0/3-24
switchport mode access
switchport access vlan 60

switchport port-security
switchport port-security maximum 2
switchport port-security mac-address sticky
switchport port-security violation shutdown

do wr
exit
```
![image](https://github.com/user-attachments/assets/3782d252-ee72-42bc-899f-6f47aa0cbcd5)


- ### LOGISTICS SWITCH FLOOR 3
```bash
int range fa0/1-2
switchport mode trunk

vlan 70
name logistics
exit

int range fa0/3-24
switchport mode access
switchport access vlan 70

switchport port-security
switchport port-security maximum 2
switchport port-security mac-address sticky
switchport port-security violation shutdown

do wr
exit



```
![image](https://github.com/user-attachments/assets/cb1bc63c-e6dc-4c83-94f9-ef35eab81705)


- ### CUSTOMER SWITCH FLOOR 3
```bash
int range fa0/1-2
switchport mode trunk

vlan 80
name customer
exit

int range fa0/3-24
switchport mode access
switchport access vlan 80

switchport port-security
switchport port-security maximum 2
switchport port-security mac-address sticky
switchport port-security violation shutdown

do wr
exit



```
![image](https://github.com/user-attachments/assets/5d195453-9104-4233-b77c-67fd26756186)


- ### GUEST SWITCH FLOOR 3
```bash
int range fa0/1-2
switchport mode trunk

vlan 90
name guest
exit

int range fa0/3-24
switchport mode access
switchport access vlan 90

switchport port-security
switchport port-security maximum 2
switchport port-security mac-address sticky
switchport port-security violation shutdown

do wr
exit

```
![image](https://github.com/user-attachments/assets/bc1eb56f-9cbd-43a8-a60d-441e5b978c8a)


- ### ADMIN SWITCH FLOOR 4
```bash
int range fa0/1-2
switchport mode trunk

vlan 100
name admin
exit

int range fa0/3-24
switchport mode access
switchport access vlan 100

switchport port-security
switchport port-security maximum 2
switchport port-security mac-address sticky
switchport port-security violation shutdown

do wr
exit


```
![image](https://github.com/user-attachments/assets/5067b0cd-c8b2-4771-be2a-27e94fc7749e)

- ### ICT SWITCH FLOOR 4
```bash
int range fa0/1-2
switchport mode trunk

vlan 110
name ICT
exit

int range fa0/3-24
switchport mode access
switchport access vlan 110

switchport port-security
switchport port-security maximum 2
switchport port-security mac-address sticky
switchport port-security violation shutdown

do wr
exit
```
![image](https://github.com/user-attachments/assets/be227af7-580b-4e4c-ad27-95e24ad093be)

- ### SERVER SWITCH FLOOR 4
```bash
int range fa0/1-2
switchport mode trunk

vlan 120
name SERVER-VLANS
exit

int range fa0/3-24
switchport mode access
switchport access vlan 120

switchport port-security
switchport port-security maximum 2
switchport port-security mac-address sticky
switchport port-security violation shutdown

do wr
exit
```
![image](https://github.com/user-attachments/assets/6057b427-76f8-4935-9486-b29b6c7d1575)

---------------------------------------------------------------------------------------------------------------------------------------------------------
# Subnetting And IP Addressing

### IP Addressing of Floor 1

1. **Management VLAN 10**: `192.168.10.0/26`
2. **Research VLAN 20**: `192.168.10.64/26`
3. **Human Resource VLAN 30**: `192.168.10.128/26`

### IP Addressing of Floor 2

1. **Marketing VLAN 40**: `192.168.10.192/26`
2. **Accounting VLAN 50**: `192.168.11.0/26` 
3. **Finance VLAN 60**: `192.168.11.64/26`

### IP Addressing of Floor 3

1. **Logistic VLAN 70**: `192.168.11.128/26`
2. **Customer VLAN 80**: `192.168.11.192/26`
3. **Guest VLAN 90**: `192.168.12.0/26`

### IP Addressing of Floor 4

1. **Admin VLAN 100**: `192.168.12.64/26`
2. **ICT VLAN 110**: `192.168.12.128/26`
3. **Server VLAN 120**: `192.168.12.192/26`
   
![WhatsApp Image 2025-01-03 at 09 03 38_6fcb9796](https://github.com/user-attachments/assets/d57dcf74-0747-423a-bc61-e0a35f010568)
![WhatsApp Image 2025-01-03 at 09 03 38_cff4e067](https://github.com/user-attachments/assets/7d3317c0-e114-49dc-90a0-ad90452b07a1)


# Addressing betweeen routers and layer-3 switch
![WhatsApp Image 2025-01-03 at 09 03 38_8a38796f](https://github.com/user-attachments/assets/d08074d5-7c2b-4e80-8641-12181656dd58)

--------------------------------------------------------------------------------------------------------------------------------------------

# Trunking layer 3 switches and making (layer 2 part to be layer 3 interface)

.Floor 1 Layer 3 swtich
```bash
int range gig1/0/3-8
switchport mode trunk
exit
do wr

int range gig1/0/1-2
no swtichport
exit

int range gig1/0/1
ip address 10.10.10.1 255.255.255.252
exit
int range gig1/0/2
ip address 10.10.10.9 255.255.255.252
exit
```
![image](https://github.com/user-attachments/assets/3bb7143f-3ee8-4be0-bded-1c842a42bd44)

.Floor 2 Layer 3 swtich
```bash
int range gig1/0/3-8
switchport mode trunk
exit
do wr

int range gig1/0/1-2
no swtichport
exit

int range gig1/0/1
ip address 10.10.10.13 255.255.255.252
exit
int range gig1/0/2
ip address 10.10.10.5 255.255.255.252
exit
```

![image](https://github.com/user-attachments/assets/8007c461-a307-4602-b111-ba68bdaf6ccf)
![image](https://github.com/user-attachments/assets/d768f225-ac12-4a48-b3bb-ab2936332660)

.Floor 3 Layer 3 swtich
```bash
int range gig1/0/3-8
switchport mode trunk
exit
do wr

int range gig1/0/1-2
no swtichport
exit

int range gig1/0/1
ip address 10.10.10.41 255.255.255.252
exit
int range gig1/0/2
ip address 10.10.10.45 255.255.255.252
exit
```

![image](https://github.com/user-attachments/assets/a635ecee-6be3-4aa2-a4e2-78b8dc3592a2)
![image](https://github.com/user-attachments/assets/27ab9746-e64e-4321-b5e9-3dadfa262c61)


.Floor 4 Layer 3 swtich
```bash
int range gig1/0/3-8
switchport mode trunk
exit
do wr

int range gig1/0/1-2
no swtichport
exit

int range gig1/0/1
ip address 10.10.10.49 255.255.255.252
exit
int range gig1/0/2
ip address 10.10.10.53 255.255.255.252
exit
```

![image](https://github.com/user-attachments/assets/b59b0452-bb16-4717-92b6-ce77a47cbc76)
![image](https://github.com/user-attachments/assets/78939388-0c53-4c95-8b28-539b01af4d39)


-------------------------------------------------------------------------------------------------------------------------------

# Assigning ip address Floor 1 Routers(gig) and serial port

![image](https://github.com/user-attachments/assets/30105aaf-4ad0-4e35-8c00-9630424e340b)

![image](https://github.com/user-attachments/assets/93e0ba97-5d56-4529-a11b-9038820b869e)

![image](https://github.com/user-attachments/assets/fe11b4f5-7cc8-4dc2-a26c-5df94adbe595)


----------------------------------------------------------------------------------------------------------------------------

# 5-OSPF ON THE ROUTERS AND LAYER3 SWITCHES

## FIRST OSPF ON ROUTERS

- ### CONFIGURING ALL PATH ON ROUTER OF FLOOR 1

```bash
router ospf 10

network 10.10.10.0 0.0.0.3 area 0
network 10.10.10.4 0.0.0.3 area 0
network 10.10.10.16 0.0.0.3 area 0
network 10.10.10.28 0.0.0.3 area 0
network 10.10.10.32 0.0.0.3 area 0
exit
do wr
```
![image](https://github.com/user-attachments/assets/83b7a791-9509-47b9-8719-b6b2a33ae16f)

- ### CONFIGURING ALL PATH ON ROUTER OF FLOOR 2

```bash
router ospf 10

network 10.10.10.12 0.0.0.3 area 0
network 10.10.10.8 0.0.0.3 area 0
network 10.10.10.16 0.0.0.3 area 0
network 10.10.10.20 0.0.0.3 area 0
network 10.10.10.24 0.0.0.3 area 0
exit
do wr
```
![image](https://github.com/user-attachments/assets/e9662acd-72f8-4a5b-a1b3-a1a24949aaa2)

- ### CONFIGURING ALL PATH ON ROUTER OF FLOOR 3

```bash
router ospf 10

network 10.10.10.32 0.0.0.3 area 0
network 10.10.10.20 0.0.0.3 area 0
network 10.10.10.36 0.0.0.3 area 0
network 10.10.10.48 0.0.0.3 area 0
network 10.10.10.40 0.0.0.3 area 0
exit
do wr
```
![image](https://github.com/user-attachments/assets/928afb36-351e-4012-8294-529dceb51ebf)

- ### CONFIGURING ALL PATH ON ROUTER OF FLOOR 4

```bash
router ospf 10

network 10.10.10.24 0.0.0.3 area 0
network 10.10.10.28 0.0.0.3 area 0
network 10.10.10.36 0.0.0.3 area 0
network 10.10.10.44 0.0.0.3 area 0
network 10.10.10.52 0.0.0.3 area 0
exit
do wr
```
![image](https://github.com/user-attachments/assets/865bb2a6-2d36-4f86-9812-8e57b386189d)


-------------------------------------------------------------------------------------------------
## SECOND OSPF APPLY ON LAYER 3 SWITCHES ALSO  FOR ADVERSTISING ALL NETWORKS on LAYER 3 SWITHC OF FLOOR 1


- ### FLOOR 1 LAYER 3 SWITCH
```bash
ip routing
router ospf 10
network 10.10.10.0 0.0.0.3 area 0
network 10.10.10.8 0.0.0.3 area 0

network 192.168.10.0 0.0.0.63 area 0
network 192.168.10.64 0.0.0.63 area 0
network 192.168.10.128 0.0.0.63 area 0
network 192.168.10.192 0.0.0.63 area 0
network 192.168.11.0 0.0.0.63 area 0
network 192.168.11.64 0.0.0.63 area 0
```
![image](https://github.com/user-attachments/assets/c99f466a-4b51-4830-8387-5f5a6b95d9c2)

![image](https://github.com/user-attachments/assets/9a513d68-7ce3-4db5-b8ca-04cc9e6c9013)

- ### FLOOR 2 LAYER 3 SWITCH
```bash
ip routing
router ospf 10
network 10.10.10.12 0.0.0.3 area 0
network 10.10.10.4 0.0.0.3 area 0

network 192.168.10.0 0.0.0.63 area 0
network 192.168.10.64 0.0.0.63 area 0
network 192.168.10.128 0.0.0.63 area 0
network 192.168.10.192 0.0.0.63 area 0
network 192.168.11.0 0.0.0.63 area 0
network 192.168.11.64 0.0.0.63 area 0
do wr
```

![image](https://github.com/user-attachments/assets/a8f3f40f-ee97-408b-84e9-d26019cc173d)


- ### FLOOR 3 LAYER 3 SWITCH
```bash
ip routing
router ospf 10
network 10.10.10.42 0.0.0.3 area 0
network 10.10.10.40 0.0.0.3 area 0

network 192.168.11.128 0.0.0.63 area 0
network 192.168.11.192 0.0.0.63 area 0
network 192.168.12.0 0.0.0.63 area 0
network 192.168.12.64 0.0.0.63 area 0
network 192.168.12.128 0.0.0.63 area 0
network 192.168.12.192 0.0.0.63 area 0
do wr
```

![image](https://github.com/user-attachments/assets/b2385fd3-a010-49d4-9496-b066cd241f5b)


- ### FLOOR 4 LAYER 3 SWITCH
```bash
ip routing
router ospf 10
network 10.10.10.52 0.0.0.3 area 0
network 10.10.10.48 0.0.0.3 area 0

network 192.168.11.128 0.0.0.63 area 0
network 192.168.11.192 0.0.0.63 area 0
network 192.168.12.0 0.0.0.63 area 0
network 192.168.12.64 0.0.0.63 area 0
network 192.168.12.128 0.0.0.63 area 0
network 192.168.12.192 0.0.0.63 area 0
do wr
```
![image](https://github.com/user-attachments/assets/1ae22be6-ee18-47a2-9293-f51b93951b12)



--------------------------------------------------------------------------------------------
# 6- STATIC IP ADDRESS TO SERVER ROOM DEVICES (STATICALLY ASSIGN IP FROM DHCP SERVER)

- ### DHC SERVER IP CONFIGURATION

![image](https://github.com/user-attachments/assets/5fe52895-0a85-438f-adad-e53129ff92db)

- ### EMAIL SERVER

![image](https://github.com/user-attachments/assets/4441de54-706f-4a3b-b520-1453a6d9e6f7)

- ### HTTPS SERVER

![image](https://github.com/user-attachments/assets/7ed6afd3-b4be-45f3-9d4b-e0381c84f2b7)

--------------------------------------------------------------------------------------------
# 7- DHCP SERVER DEVICE AND CONFIGURATION

- ### MANAGEMENT POOL (F1)
![image](https://github.com/user-attachments/assets/52d135f4-3184-4ca2-a4ec-b60e9296ac96)


- ### RESEARCH POOL (F1)
![image](https://github.com/user-attachments/assets/5639ddd9-aba3-4cbe-83de-817b81fee756)


- ### HR POOL (F1)
![image](https://github.com/user-attachments/assets/3fec0c01-9fa9-49ea-8538-f4e4d5d9f699)


 
- ### MARKETING  POOL (F2)
![image](https://github.com/user-attachments/assets/8fb9c3d1-e29e-413a-823a-0508a96e16a7)


  
- ### ACCOUNTING POOL (F2)
![image](https://github.com/user-attachments/assets/186f5e9d-09ac-4f54-8eb1-b20ef31cf331)


 
- ### FINANCE POOL (F2)
![image](https://github.com/user-attachments/assets/a07385c2-f822-408c-9843-061e83c787f4)

  
- ### LOGISTIC POOL (F3)
![image](https://github.com/user-attachments/assets/4464b234-f17c-4b74-96da-91f53a45640a)

  
- ### CUSTOMER POOL (F3)
![image](https://github.com/user-attachments/assets/5d8ad793-08fe-4d3a-80e9-0c23173c1048)


- ### GUEST POOL (F3)
![image](https://github.com/user-attachments/assets/cf8334ff-f8e9-4c24-85f2-176412f9de52)

  
- ### ADMIN POOL (F4)
![image](https://github.com/user-attachments/assets/a7c744e5-71e7-4770-ad1b-423c3765322e)

 
- ### ICT  POOL (F4)

![image](https://github.com/user-attachments/assets/f26c771b-5f0a-453b-9a1c-5232489d609e)


--------------------------------------------------------------------------------------------
# 8- Inter VLAN routing on 13 switches plus IP DHCP helper address

###  FIRST ON DO 1 & 2 L3 SWITCH
```bash
vlan 10
vlan 20
vlan 30
vlan 40
vlan 50
vlan 60

int vlan 10
no shutdown
ip add 192.168.10.1 255.255.255.192
ip helper-address 192.168.12.196
exit

int vlan 20
no shutdown
ip add 192.168.10.65 255.255.255.192
ip helper-address 192.168.12.196
exit

int vlan 30
no shutdown
ip add 192.168.10.129 255.255.255.192
ip helper-address 192.168.12.196
exit



int vlan 40
no shutdown
ip add 192.168.10.193 255.255.255.192
ip helper-address 192.168.12.196
exit

int vlan 50
no shutdown
ip add 192.168.11.1 255.255.255.192
ip helper-address 192.168.12.196
exit

int vlan 60
no shutdown
ip add 192.168.11.65 255.255.255.192
ip helper-address 192.168.12.196
exit

do wr
```
![image](https://github.com/user-attachments/assets/22660c9e-b7af-49b9-af73-8861817ef153)
![image](https://github.com/user-attachments/assets/adcc4fc1-b3ad-4390-bc76-7f103cd88775)


###  FIRST ON DO 3 & 4 L3 SWITCH

```bash
vlan 70
vlan 80
vlan 90
vlan 100
vlan 110
vlan 120

int vlan 70
no shutdown
ip add 192.168.11.129 255.255.255.192
ip helper-address 192.168.12.196
exit

int vlan 80
no shutdown
ip add 192.168.11.193 255.255.255.192
ip helper-address 192.168.12.196
exit

int vlan 90
no shutdown
ip add 192.168.12.1 255.255.255.192
ip helper-address 192.168.12.196
exit



int vlan 100
no shutdown
ip add 192.168.12.65 255.255.255.192
ip helper-address 192.168.12.196
exit

int vlan 110
no shutdown
ip add 192.168.12.129 255.255.255.192
ip helper-address 192.168.12.196
exit

int vlan 120
no shutdown
ip add 192.168.12.193 255.255.255.192
exit

do wr
```
![image](https://github.com/user-attachments/assets/b3d0548d-0ec7-4f75-97d0-bb5a14db1ab5)
![image](https://github.com/user-attachments/assets/e303951c-b38a-4e6d-848b-ae7f39da3c54)





--------------------------------------------------------------------------------------------
# 9- Wireless networking configuration

- ### THIS TIME ONLY COFIGURING FINANCE ACCESS POINT

![image](https://github.com/user-attachments/assets/be43b5b9-4d97-42dc-9715-e5b2c0331839)

- ### CONNECTING LAPTOP TO FINANCE WIFI

![image](https://github.com/user-attachments/assets/e1c204ca-e389-4230-9979-cbe88daab047)

- ### LAPTOP IS CONNECTED
![image](https://github.com/user-attachments/assets/85aafb94-4c60-48d3-a2ea-10079083bdd7)

--------------------------------------------------------------------------------------------
# 10- VERIFY PING THAT NETWORK MAKE SUCCESSFUL

