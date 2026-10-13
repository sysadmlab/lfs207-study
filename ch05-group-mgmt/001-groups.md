# Groups  
A user account in Linux has **one Primary Group** and this group is listed in the **fourth** field of **/etc/passwd** file.  
A user account can become a member to one or more **Secondary Groups** although there is a practical limit of **16**. </br>  

Groups and related information can be found in the **/etc/group** file. </br>  
<img width="344" height="265" alt="Screenshot From 2026-10-12 18-45-34" src="https://github.com/user-attachments/assets/5ef0fc68-c986-45de-a666-45b7eed5f9e2" />  
The above image is the screenshot of a part of the **/etc/group** file. Each record in this file consists of 4 fields separated by the colon symbol.  
The first field is the **group name**, the second field is the **password placeholder**, the third field is the **group identifier (GID)**, and the fourth is the **secondary group members** field.  

# /etc/passwd and /etc/group  
<img width="416" height="130" alt="Screenshot From 2026-10-13 08-56-37" src="https://github.com/user-attachments/assets/44c096e4-b540-4638-90a3-141a03a9c688" /> </br>  
The image above is a screenshot of a particular item in the **/etc/passwd** file. The user account **as** has **UID** 1000 and **GID** 1000.  In this case, **GID** 1000 is 
both the **Primary Group** and the **User Private Group** for the user **as**. </br>  
In the **/etc/group** file, the group **as** with **GID** 1000 does NOT have any members, particularly it does NOT list user **as** as its member.  
This is because only **Secondary group membership** is listed here. **Primary Groups** are NOT listed in the **/etc/group** file - as shown in the image below. </br>  
<img width="416" height="130" alt="Screenshot From 2026-10-13 08-58-22" src="https://github.com/user-attachments/assets/cb8f1464-b3c8-458c-8a73-0a9c1c5ef3fc" />  

# Directories and Files  
When I create Directories and Files, the items are owned by my user account (**UID**) and my primary group (**GID**). </br>  
<img width="477" height="150" alt="image" src="https://github.com/user-attachments/assets/c9afac6b-5837-4cfb-89e2-36aff7e34c44" />  
In this case my user account is **as** and my primary group is **as**.  
