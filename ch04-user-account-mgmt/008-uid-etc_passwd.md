# User IDs and the /etc/passwd file  
The following image is a screenshot of the **/etc/passwd** file. There are 7 fields that are separated using a colon symbol (:). The first field is the **username**, second the **encrypted password**, third the **user id (uid)**, fourth the **primary group of the user (or) User Private Group (gid), fifth the **comment** field, sixth the **home folder location**, and the final field is the **login shell**. </br>  
<img width="995" height="601" alt="Screenshot From 2026-10-05 14-44-09" src="https://github.com/user-attachments/assets/14ec90b1-dae4-4944-b42f-0fbaa7b6bbd4" />  
I have sorted the **/etc/passwd** file based on the third field which is the UID. I note that the UID for my user and a user created by me start at 1000 whereas the UIDs of accounts created by the system start at 0. The **root** user's UID is 0.  

## login.defs file  
The file **login.defs** defines the miminum and the maximum range for UIDs for **system accounts** and **user accounts**. In Rocky Linux and in Ubuntu Server this file is present under the **/etc** directory.  
### Note:  
I assumed that I would find the **login.defs** file under **/etc** in openSUSE Leap 16, however to my suprise, it is under **/usr/etc/login.defs**. On further research, I learned that **vendor-shipped** defaults live under **/usr/etc** and user-created files are under **/etc**. </br>  

The images below are screenshots of the minimum and maximum range for **Rocky Linux**, **Ubuntu Server**, and **openSUSE Leap 16** respectively. </br>  
<img width="677" height="793" alt="1" src="https://github.com/user-attachments/assets/e21abc1a-f710-47dc-b49e-9e4cf71daa91" />  
While UID minimum and the maximum remain the same for user accounts, the distributions differ in the range for the system accounts.  
