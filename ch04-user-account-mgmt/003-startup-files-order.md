# Startup Files Order:  

The file **/etc/profile** is the system-wide login startup file and is read and evaluated for every login shell. </br>  
<img width="742" height="324" alt="image" src="https://github.com/user-attachments/assets/db1db393-baaf-4223-885d-4c3fb01f381a" /> </br>  

After this, the following login shell startup files are searched for in order.  

1. **~/.bash_profile** - highest priority; read first if it exists while **~/.bash_login** and **~/.profile** are ignored.  
2. **~/.bash_login** - read **only** if **~/.bash_profile** does **NOT** exist; if this file exists, **~/.profile** is ignored.  
3. **~/.profile** - read **only** if both **~/.bash_profile** and **~/.bash_login** are absent.  

I note that distributions differ in the login startup files used. </br>  
<img width="618" height="963" alt="image" src="https://github.com/user-attachments/assets/7466ac4a-b82b-4eb9-b701-cf77a45536e4" />  
