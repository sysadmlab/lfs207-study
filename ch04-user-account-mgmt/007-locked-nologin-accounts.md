# No Login Accounts:  
A bunch of accounts in the **/etc/passwd** file have **nologin** as the login shell </br>  
<img width="1004" height="481" alt="Screenshot From 2026-09-21 19-34-02" src="https://github.com/user-attachments/assets/a0cfc487-018f-49b8-ba3a-48f1b9315fdb" />    
As the **shell** states, these accounts are not allowed to be logged in with a password; so no login allowed.  
For example: I notice that the accounts **mail** and **sshd** have **/usr/sbin/nologin** as their **login shell** in the **/etc/passwd** file and either an * or an ! in the **/etc/shadow** file. An * or an ! in the encrypted password field of the **shadow** file only means that **password login is impossible**. </br>  
<img width="778" height="192" alt="Screenshot From 2026-09-21 19-45-33" src="https://github.com/user-attachments/assets/6d127fbb-f4ee-47be-bb03-0150a90dab80" />  

### Side Note: I have to use grep -E instead of egrep (as stated in the image above). </br>  


# Locked Accounts    
Locked accounts on the contrary are user accounts that have been out-rightly denied the ability to logon to the system, an action taken by a SysAdmin. 

## Locking using "usermod" command:  
One way to lock an user account is using the command **usermod** with the **-L** option. Executing the command **sudo usermod -L tech01** locks the account of **tech01**. The command **prefixes** the **hashed password** with an **exclamatory sign**(!) such that password login is impossible. The command **sudo usermod -U tech01** will unlock the account of user **tech01**. Image below: </br>  
<img width="1012" height="861" alt="usermod" src="https://github.com/user-attachments/assets/62505d57-9101-4e18-843d-b3a0a2113a81" />  

## Locking using "passwd" command:  
Another way to lock an user account is the use of **passwd** command with the **-l** option. Executing the command **sudo passwd -l tech01** locks the account of **tech01**. The command **prefixes** the **hashed password** with an **exclamatory sign**(!) such that password login is impossible. The command **sudo passwd -u tech01** will unlock the account of user **tech01**. Image below: </br>  
<img width="1012" height="861" alt="passwd" src="https://github.com/user-attachments/assets/6bc0b348-6761-46c2-9d3b-564e9288cc65" />  

## Expiring an user account using the "chage" command:  
The command **chage** is used to work with the **age** fields of an account's password. Using the **chage** command a SysAdmin can set an account to expire (dsable), but keeping the account intact.   
The command **sudo chage -E 0 tech01** sets user **tech01** password expiry date to a time back in the past (**0 - the first day of the epoch - 01-Jan-1970**) such that the user's account is disabled until a SysAdmin enables the account again. </br>  

### Disabling an Account with chage: </br>  
<img width="1021" height="618" alt="Screenshot From 2026-09-28 13-53-38" src="https://github.com/user-attachments/assets/b6edd6ea-720c-45fb-81c5-fa11fbdaf493" />  

### Enabling an Account with chage: </br>  
<img width="1018" height="501" alt="chage 02" src="https://github.com/user-attachments/assets/42e8c831-0618-46d7-b22a-3738bb857680" />  
