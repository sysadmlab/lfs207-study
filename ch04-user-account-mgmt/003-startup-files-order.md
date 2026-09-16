# Startup Files Order:  

The file **/etc/profile** is the system-wide login startup file and is read and evaluated once per login shell. </br>  
<img width="742" height="324" alt="image" src="https://github.com/user-attachments/assets/db1db393-baaf-4223-885d-4c3fb01f381a" /> </br>  

After this, the following startup files are searched for in order. Each file is read once during user login.

1. **/home/<username>/.bash_profile**
2. **/home/<username>/.bash_login**
3. **/home/<username>/.profile**

If the startup file **.bash_profile** is found, it is read, and **~/.bash_login** and **~/.profile** are ignored. I note that distributions differ in the startup file used. </br>  
