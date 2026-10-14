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
The minimum and the maximum values for **System** groups is also defined in the **/etc/login.defs** file.  

## groupmod command  
Using the **groupmod** command, I can **append** users to a group, **change GID**, **rename** the group etc.  
As the first task, I am going to add the user **tech01** to the group **ithelpdesk**. To achieve this I will use the **-a** switch for append and the **-U** switch for user(s).  
Then I'm going to change the **GID** of the group. </br>  
<img width="887" height="457" alt="image" src="https://github.com/user-attachments/assets/cd8c6ef8-eb54-4887-bdd2-efaeaebc1a91" />  

Using the **-g** option with the **groupmod** command, I have modified the group identifier **GID** of the group **ithelpdesk** </br>  
<img width="883" height="637" alt="image" src="https://github.com/user-attachments/assets/e4f2f014-f7da-4d05-907f-648e97241b45" />  

## Modifying membership with usermod command  
I can also use the **usermod** command to add a user to a group. Using the option **-G** I can provide a list of supplementary groups to which the user will be added.  
### Note of caution  
While using the **-G** option, it is necessary to use the **-a** (append) option. If the **-a** option is not used the command will erase the **current** supplementary group list and consider
only those groups that are provided with the **-G** option. </br>  
<img width="509" height="280" alt="image" src="https://github.com/user-attachments/assets/5086e9bb-b9d5-447e-a98a-7e919d4942f0" />  

## groupdel command  
The **groupdel** command is used to delete a group and its simplest usage is **sudo groupdel groupname**.  
I am going to use the **groupdel** command to delete the **ithelpdesk** group I created. </br>  
<img width="509" height="517" alt="image" src="https://github.com/user-attachments/assets/eb7ce093-bf10-4887-b3bc-105893562f6a" />  
Deleting a group also removes its membership list.  
