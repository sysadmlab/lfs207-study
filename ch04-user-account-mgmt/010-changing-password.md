# Changing Password  
I can change the password for my user account using the command **passwd**. However, if I need to change password for an other user, I need elevated privileges.  
The binary for the command **passwd** is located at **/usr/bin/passwd** and the permissions for this file is a bit different. </br>  
<img width="615" height="180" alt="image" src="https://github.com/user-attachments/assets/28e6a0f8-3589-4b36-9c62-f7db0b3f436a" />  
As seen in the image above, the **setuid** bit is enabled for the **/usr/bin/passwd** binary file, marked by **s** in user permissions. This file is owned by user **root** and group **root**.  
The **Others** group has **read** and **execute** permissions on this binary. This means that when a normal user executes **passwd** the command executes with the user's real UID; However, since
**setuid** is enabled, the effective UID becomes the root's UID. So this is why the user is able to change the password in the **/etc/shadow** file.  
I have to mention it because the **/etc/shadow** file has **000** permissions set in **Rocky Linux** and **640** permissions set for **root:shadow** in Ubuntu Server.  
This means that only **root** can modify this file, and that is the reason why the command **passwd** can **setuid** bit enabled. </br>  
<img width="560" height="220" alt="image" src="https://github.com/user-attachments/assets/ed0bce8c-ea98-42c5-aec4-d270644bd8c1" /> </br>  

### User Changing his own password  
<img width="705" height="341" alt="Screenshot From 2026-10-06 22-23-53" src="https://github.com/user-attachments/assets/e3cdb0b0-90ed-44a0-9fe4-c43ce4967da3" />  

### User Changing password of another user  
<img width="580" height="209" alt="Screenshot From 2026-10-06 22-25-53" src="https://github.com/user-attachments/assets/09ab0cc6-11c2-4116-9582-01ee97c66a6f" />  
