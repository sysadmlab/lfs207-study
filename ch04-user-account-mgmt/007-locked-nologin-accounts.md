# No Login Accounts:  
A bunch of accounts in the **/etc/passwd** file have **nologin** as the login shell </br>  
<img width="1004" height="481" alt="Screenshot From 2026-09-21 19-34-02" src="https://github.com/user-attachments/assets/a0cfc487-018f-49b8-ba3a-48f1b9315fdb" />    
As the **shell** states, these accounts are not allowed to be logged in with a password; so no login allowed.  
For example: I notice that the accounts **mail** and **sshd** have **/usr/sbin/nologin** as their **login shell** in the **/etc/passwd** file and either an * or an ! in the **/etc/shadow** file. An * or an ! in the encrypted password field of the **shadow** file only means that **password login is impossible**. </br>  
<img width="778" height="192" alt="Screenshot From 2026-09-21 19-45-33" src="https://github.com/user-attachments/assets/6d127fbb-f4ee-47be-bb03-0150a90dab80" />  

### Side Note: I have to use grep -E instead of egrep (as stated in the image above). </br>  


# Locked Accounts  
Locked accounts on the contrary are user accounts that have been out-rightly denied the ability to logon to the system, an action taken by a SysAdmin. The command **chage** is used to work with the **age** fields of an account's password. Obviously, this command requires elevated privileges. Using the **chage** command a SysAdmin can set an account to expire, making login impossible but keeping the account intact.  
The command **sudo chage -E 0 tech01** sets user **tech01** password expiry date to a time back in the past (**0 - the first day of the epoch - 01-Jan-1970**) such that the user cannot login to the system unless a SysAdmin allows. </br>  

