# Creating User Accounts with useradd command:  
The command **useradd** can be used to create new users in a Linux computer.  
The basic usage of the command is **sudo useradd <username>**. Obviously, the command **useradd** requires elevated privileges.  
The default values that apply for the command **useradd** command can be found at two places: 1. **/etc/login.defs** 2. **/etc/default/useradd** </br>  
<img width="1557" height="630" alt="image" src="https://github.com/user-attachments/assets/bd5e1653-6a2b-4618-8cfc-c0f02b351501" />  
The image above shows some of the defaults defined in the **/etc/login.defs** file. Likewise, the settings defined in the file **/etc/default/useradd** is shown below: </br>  
<img width="448" height="274" alt="Screenshot From 2026-09-18 19-56-25" src="https://github.com/user-attachments/assets/47f2a88e-8de9-4585-8382-42b11b4f137a" />  
By using options and passing arguments, custom settings can be passed while creating an user account using **useradd** for example:  
The command **sudo useradd -m -c "Technician01" -s "/usr/bin/sh" tech1** does the following:  
1. creates an user account **tech1**
2. forces the creation of a **HOME** directory with the **-m** option
3. uses the **GECOS** or the comment field with the **-c** option and takes "**Technician01**" as the comment
4. and sets the **SHELL** at "**/usr/bin/sh**" </br>  
<img width="747" height="230" alt="Screenshot From 2026-09-18 20-01-46" src="https://github.com/user-attachments/assets/1141936e-0485-48c4-a241-b23e14bd5c89" /> </br>
The image above shows the creation of user **tech1**  
By default, the files (hidden files) in the **SKEL** directory (Skeleton directory) and copied to the user's home folder. </br>  
<img width="598" height="207" alt="Screenshot From 2026-09-18 20-08-35" src="https://github.com/user-attachments/assets/8d4078e0-53a2-4699-9b58-4e724ed3a005" />  
