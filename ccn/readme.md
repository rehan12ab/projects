
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




   

