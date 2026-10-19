# umask  
**umask** is the utility that controls the maximum permissions to directories and files during the time of their creation. </br>  
Directories and files have a maximum permission of 777 and 666 respectively, and the **umask** value defines the effective permissions for newly created
files and directories. </br>  
<img width="259" height="220" alt="image" src="https://github.com/user-attachments/assets/e4c3d6cc-6b84-4cf2-a751-42806361f7b8" /> </br>    
The **umask** value for both Rocky Linux and openSUSE Leap is **022**. This value is subtracted (bits removed) from the maximum permission. </br>  
So all newly created directories have a permission of **755** and all newly created files have a permission of **644**. </br>  
**umask** in a way ensure security - such that user's do not automatically get **WRITE** permissions on directories and **WRITE** and **EXECUTE** permissions on files. </br>  

While the course material states that **umask** values can be found at **/etc/profile**, in openSUSE Leap it is found at **/usr/etc/login.defs** - it's a bit different
in openSUSE. There a **/etc** and then there's a **/usr/etc**. </br>  
In Rocky Linux and Ubuntu Server, **umask** values are found in **/etc/login.defs** </br>  
<img width="795" height="488" alt="image" src="https://github.com/user-attachments/assets/74bc8d91-6de4-46e1-8833-7bfb64b4bcc8" /> </br>  

It appears that **umask** values may be found in **/etc/bashrc** in some cases and SysAdmins set more restrictive **umask** values in the **~/.bashrc** file for per-user basis.  

## Changing umask  
**umask** value can be changed using the command **umask <value>**. </br>  
I have changed the **umask** to **027**. This change also gets passed-on to **child processes**, however, this change does **NOT** carry over to new logins. </br>  
Hence to have a permanent effect on **umask** the change could be made in, for example, **~/.bashrc**. </br>  
<img width="567" height="353" alt="image" src="https://github.com/user-attachments/assets/aafd704c-76a9-41ec-b569-9582ee89041a" /> </br>  
