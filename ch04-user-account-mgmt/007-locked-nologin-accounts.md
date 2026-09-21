# No Login and Locked Accounts:  
A bunch of accounts in the **/etc/passwd** file have **nologin** as the login shell </br>  
<img width="1004" height="481" alt="Screenshot From 2026-09-21 19-34-02" src="https://github.com/user-attachments/assets/a0cfc487-018f-49b8-ba3a-48f1b9315fdb" />    
As the **shell** states, these accounts are not allowed to be logged in with a password; so no login allowed.  
For example: I notice that the accounts **mail** and **sshd** have **/usr/sbin/nologin** as their **login shell** in the **/etc/passwd** file and either an * or an ! in the **/etc/shadow** file. An * or an ! in the encrypted password field of the **shadow** file only means that **password login is impossible**. </br>  
<img width="778" height="192" alt="Screenshot From 2026-09-21 19-45-33" src="https://github.com/user-attachments/assets/6d127fbb-f4ee-47be-bb03-0150a90dab80" />  

