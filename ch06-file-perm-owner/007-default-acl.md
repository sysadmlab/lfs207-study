# Setting a default ACL  

## Demonstration  
A **default ACL** can only be set on directories. The **default ACL** gets copied to sub-directories and files. </br>  
<img width="520" height="89" alt="Screenshot From 2026-10-26 21-15-26" src="https://github.com/user-attachments/assets/62942eb2-4f38-4c2b-a668-c0e51e3647c0" />  
For demonstration, I have created a directory **infodocs** under **/stor**. Currently **root:root** is the user owner and group owner.  

## Users, Groups, and special permissions  
Further, I have created a group **hrd** and a user **hrm**, and I added **hrm** to the group **hrd**. </br>  
<img width="750" height="457" alt="Screenshot From 2026-10-26 21-27-31" src="https://github.com/user-attachments/assets/91ae54c1-7e45-4ca6-853e-84ca3663fb04" />  
As shown in the image, I have executed the **chgrp** command to change the group owner to **hrd**. Then using the **chmod** command, I have Set GID on the
**infodocs** directory. </br>  

When I run the command **getfacl** on the **infodocs** directory, I note the **flags** **-s-** to denote that **Set GID** is enabled. </br>  
<img width="610" height="198" alt="image" src="https://github.com/user-attachments/assets/689aaae8-6b87-4a27-949f-fcb61c52d92d" />  

## Scenario  
The objective here is to ensure that the Human Resources Manager and the IT Manager collaborate in creating and maintaining the **information documents** for the company. </br>  
As noted, the **infodocs** directory is owned by user **root** and group **hrd**.  

## Setting the named access ACL  
Then I execute the **setfacl** with **sudo** permissions to make a named entry, providing the user **as** with **read, write, and execute** access to the
**infodocs** directory. </br>  
<img width="611" height="236" alt="image" src="https://github.com/user-attachments/assets/fbac0bc2-6852-4ae4-9dfe-96e684eb4e73" />  
### Things to note  
The above access ACL provides the appropriate access to user **as** for this particular directory alone.  
The above access ACL does **NOT** apply to existing sub-directories and files under the **infodocs** directory or the ones to be created hereafter.  

## Setting the default ACL  
I use the **setfacl** command again with **sudo** permissions to set the **default ACL**, providing user **as** with **read, write, and execute**
permissions. </br>  
<img width="609" height="361" alt="image" src="https://github.com/user-attachments/assets/ee065b4c-5670-4e98-90cf-170214a1a475" />  
### Things to note  
The **default ACL** is copied only to the sub-directories and files under the **infodocs** directory. The **default ACL** does **NOT** apply to **infodocs**.  
The **default ACL** applies only to sub-directories and files that are created after setting the **default ACL**. **Already existing** items do **NOT** get it.  
That is why I MUST first ensure that I apply the access ACL for the **infodocs** directory and then set the **default ACL** for the same directory. </br>  

## Checking if the settings worked  
From the image below, I note that the user **hrm** is able to create directories and files in the **infodocs** directory.  
I also notice that the **User Owner** and **Group Owner** ownerships are working as expected.  
The **Set GID** special permission is also working as expected. </br>  
<img width="955" height="528" alt="image" src="https://github.com/user-attachments/assets/7b353d65-97ae-4636-96ee-b2277f8d9414" />  

The user **as** who is the IT Manager is also able to change to the infodocs directory, list contents, navigate through sub-directories, create new files, read and write to files. </br>  
<img width="955" height="363" alt="image" src="https://github.com/user-attachments/assets/6cf35e25-6b0d-4811-bf10-82dd8aeb3010" />  
