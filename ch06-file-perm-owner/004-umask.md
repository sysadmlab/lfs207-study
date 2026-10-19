# umask  
**umask** is the utility that controls the maximum permissions to directories and files during the time of their creation.  
Directories and files have a maximum permission of 777 and 666 respectively, and the **umask** value defines the effective permissions for newly created
files and directories. </br>  
<img width="259" height="220" alt="image" src="https://github.com/user-attachments/assets/e4c3d6cc-6b84-4cf2-a751-42806361f7b8" />  
The **umask** value for both Rocky Linux and openSUSE Leap is **022**. This value is subtracted (bits removed) from the maximum permission.  
So all newly created directories have a permission of **755** and all newly created files have a permission of **644**.  
**umask** in a way ensure security - such that user's do not automatically get **WRITE** permissions on directories and **WRITE** and **EXECUTE** permissions on files. </br>  

While the course material states that **umask** values can be found at **/etc/profile**, in openSUSE Leap it is found at **/usr/etc/login.defs** - it's a bit different
in openSUSE. There a **/etc** and then there's a **/usr/etc**.  
In Rocky Linux, **umask** values are found in **/etc/login.defs** </br>  
<img width="795" height="488" alt="image" src="https://github.com/user-attachments/assets/74bc8d91-6de4-46e1-8833-7bfb64b4bcc8" />  
