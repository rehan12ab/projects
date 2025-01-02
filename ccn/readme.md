
# 1-NETWORK DIAGRAM:
![image](https://github.com/user-attachments/assets/a7bfc102-26e6-4c04-a2f6-0c61346db6a1)

-----------------------------------------------------------------------------------------------------------
# 2-ALL CONFIGURATIONS(REMAINING NOT DONE YET)
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

-----------------------------------------------------------------------------------------------------------
# 4-DISTRIBUTION LAYER MULTI-SWICTH 1
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


# 6- TRUNKING SWITCH PORT AND ASSIGNING VLAN's 

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


