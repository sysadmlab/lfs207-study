# Password Aging  
Password aging can be handled using the command **chage**. As mentioned earlier the field 3 to 8 of the **/etc/shadow** file can be modified using the **chage** command. </br>  
<img width="816" height="751" alt="Screenshot From 2026-10-06 22-48-46" src="https://github.com/user-attachments/assets/aabb70e6-2efd-43e9-9fd4-7c71b71cb257" />  
While the **chage -l** command shows the **last password change** for the account **tech01** in human-readable format, the same is mentioned as **20732** days from the **epoch** (01 January 1970). </br>  

## Permissions for the /usr/bin/chage binary  
The command **chage** resides at **/usr/bin/chage** and similar to the **/usr/bin/passwd**, **chage** can **setuid**/**setgid** bits enabled (depending upon distribution).  
As seen in the image below, **/usr/bin/chage** has **setuid** bit enabled in **Rocky Linux** and **setgid** bit enabled in **Ubuntu Server**. </br>  
<img width="598" height="306" alt="image" src="https://github.com/user-attachments/assets/b5538970-a707-4533-a671-8b14ff72ba4c" />  
The **setuid**/**setgid** allows the effective UID to be **root**'s UID when an normal user executes the command **chage**.  
Using the elevated privileges the password aging fields in the **/etc/shadow** can be modified.  

## Using the command **chage**  
<img width="735" height="242" alt="image" src="https://github.com/user-attachments/assets/ba3d0973-1cde-4d26-8fd9-f070bb0daa15" /> </br>  
As shown in the above image, I have used the **chage** command to modify the **password warn days** and the **account expiry date**.  
