# 1-NETWORK DIAGRAM:
![image](https://github.com/user-attachments/assets/a7bfc102-26e6-4c04-a2f6-0c61346db6a1)


# 2-ALL CONFIGURATIONS(REMAINING NOT DONE YET)

# 3-FIRST FLOOR

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

![image](https://github.com/user-attachments/assets/86938048-b669-4558-9f53-4ce1fd1c6c43)

