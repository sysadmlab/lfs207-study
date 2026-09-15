# Attributes of a User Account:  
The list of users in a system and the attributes for each user is found in the file **/etc/passwd**. </br>  
<img width="1043" height="601" alt="Screenshot From 2026-09-15 15-21-55" src="https://github.com/user-attachments/assets/3d4334ce-c646-4afb-8642-abc6c624baf8" />  
The fields for every user in **passwd** file denote an attributes and are separated by colon symbol (:). Considering the fields for my user account **as**:  
The **first** field is the **username** **as**.  
The **second** field is the user **password** which has an **x**.  
The **third** field is the **user id** (or) **uid** denoted by a number and unique to the user.  
The **fourth** field is the **group id** (or) **gid** denoted by a number and unique for the group. This group is generally the primary group (or) default group of the user.  
The **fifth** field is the **comment** or **GECOS** information - can be used to store the first/last name, email, or phone number of the user.  
The **sixth** field is the user's **home** directory where the user stores personal data such as documents, music, pictures etc.  
The **seventh** field is the user's **login shell** which is **/bin/bash** in this case.  

# Commands to determine the Current User:  
The commands **who**, **whoami**, and **id** will provide information about the current user although the level of information displayed differs among the commands. </br>  
<img width="1054" height="287" alt="Screenshot From 2026-09-15 17-57-34" src="https://github.com/user-attachments/assets/739c9432-7a57-49b6-847d-d1d9c1ce68db" />  

### Note:
Running the **id** command with **sudo** elevated privileges will display the information for the **root** user and **NOT** the current user. </br>  
<img width="1061" height="195" alt="Screenshot From 2026-09-15 18-19-27" src="https://github.com/user-attachments/assets/074b34da-adc5-436f-bba3-31219340070c" />  
