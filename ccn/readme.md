# 1-NETWORK DIAGRAM:
![image](https://github.com/user-attachments/assets/a7bfc102-26e6-4c04-a2f6-0c61346db6a1)

-----------------------------------------------------------------------------------------------------------
# 2-ALL CONFIGURATIONS(REMAINING NOT DONE YET)
-----------------------------------------------------------------------------------------------------------
# 3-FIRST FLOOR (ACCESS LAYER)

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
# 4-DISTRIBUTION LAYER MULTI-ROUTER 1
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







