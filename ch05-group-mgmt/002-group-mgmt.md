# Managing Groups

## Creating, Modifying, and Deleting a Group  
The following commands can be used to create, modify and delete a group:  
1. groupadd
2. groupmod
3. groupdel

## groupadd command  
The simplest usage of this command is **sudo groupadd groupname**. </br>  
<img width="503" height="388" alt="image" src="https://github.com/user-attachments/assets/2adb5fb0-5ede-422f-8718-870bdf27b394" />  
I have created a group named **ithelpdesk**. The group identifier **gid** is **1002**. I note that group identifier for my account and the accounts I created start from **1000**.  
The reason why **GID**s start from **1000** is the value for the variable **GID_MIN** in the **/etc/login.defs** file - image below </br>  
<img width="659" height="259" alt="Screenshot From 2026-10-13 21-27-34" src="https://github.com/user-attachments/assets/7820de72-66ce-4fcf-9653-450ef0e99696" />  
