# No Login and Locked Accounts:  
A bunch of accounts in the **/etc/passwd** file have **nologin** as the login shell </br>  
<img width="1004" height="483" alt="Screenshot From 2026-09-21 19-34-02" src="https://github.com/user-attachments/assets/8dad0429-b233-4468-b8f1-579d075a44b2" />  
As the **shell** states, these accounts are not allowed to be logged in with a password; so no login allowed.  
For example: I notice that the accounts **mail** and **sshd** have **/usr/sbin/nologin** as their **login shell** in the **/etc/passwd** file and either an * or an ! in the **/etc/shadow** file. An * or an ! in the encrypted password field of the **shadow** file only means that **password login is impossible**.  
