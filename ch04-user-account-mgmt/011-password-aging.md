# Password Aging  
Password aging can be handled using the command **chage**. As mentioned earlier the field 3 to 8 of the **/etc/shadow** file can be modified using the **chage** command. </br>  
<img width="816" height="751" alt="Screenshot From 2026-10-06 22-48-46" src="https://github.com/user-attachments/assets/aabb70e6-2efd-43e9-9fd4-7c71b71cb257" /> </br>  
The command **chage** resides at **/usr/bin/chage** and similar to the **/usr/bin/passwd**, **chage** can **setuid**/**setgid** bits enabled (depending upon distribution).  
As seen in the image below, **/usr/bin/chage** has **setuid** bit enabled in **Rocky Linux** and **setgid** bit enabled in **Ubuntu Server**. </br>  
<img width="598" height="306" alt="image" src="https://github.com/user-attachments/assets/b5538970-a707-4533-a671-8b14ff72ba4c" />  
The **setuid**/**setgid** allows the effective UID to be **root**'s UID when an normal user executes the command **chage**.  
Using the elevated privileges the password aging fields in the **/etc/shadow** can be modified.  
