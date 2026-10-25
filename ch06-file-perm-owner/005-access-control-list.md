# Access Control List  

## Lab Setup  
Joe and Robin are part of the IT Helpdesk in a company. They belong to the group **ithelpdesk**. </br>  
Christina and Katie are part of Accounting and belong to the **accounting** group. </br>  
I have created the **ithelpdesk** and **accounting** groups a directory each under **/stor** named **itsupport** and **accounts** respectively. </br>  
I have also created a directory named **public** which everyone in the company can access. </br>  


  ### Permissions for directories  
  The directory **/stor** is owned by me **as** and my **upg**. </br>  
  I have enabled **sticky bit** for the **/stor/public** directory. By this setting, only **root** or the **owner** of a file can delete their content. </br>  
  <img width="499" height="344" alt="Screenshot From 2026-10-23 19-33-33" src="https://github.com/user-attachments/assets/b4e62475-dba7-4929-99c7-a94733919f0f" /> </br>  
  I have set **Set GID** bit for the **/stor/itsupport** and **/stor/accounts** directories. By this setting, when users from respective groups create new files
  under their respective directories, the group owner permissions always gets inherited. </br>  
  <img width="638" height="663" alt="Screenshot From 2026-10-23 19-44-28" src="https://github.com/user-attachments/assets/d2eb144b-b0fc-44ac-be4e-e38baccaf820" /> </br>  
  I have also removed access to **Others/World** to the **itsupport** and **accounts** directories. The file **oct2026.xlsx** under **/stor/itsupport/capex** has been created. </br>  
  <img width="632" height="316" alt="Screenshot From 2026-10-25 06-28-37" src="https://github.com/user-attachments/assets/2aaeb03a-ea01-47b2-973f-66798adaccbc" /> </br>  


  ### Scenario  
  Only the **owner** and members of the group **ithelpdesk** can access the directories and files under **itsupport**.  **Christina** from the **accounting** department
  requires **read and write** access to the **oct2026.xlsx** file located at **/stor/itsupport/capex**. </br>  

  ### Solution  
  Since **Christina** alone requires access to the specific directories and files in **itsupport**, it would not be ideal to enable **Read** and **Execute** permissions
  to **Others** which would ideally allow everyone to **traverse(change directory)** into **itsupport** and **list** contents. </br>  
  It would NOT be ideal to add **Christina** to the **ithelpdesk** group which would give her access to everything the **ithelpdesk** group owns. </br>  
  Hence for such occasions when a specific user requires specific access to files, the Access Control List comes into play. </br>  

  ### Linux File Access Control List  
  For the XFS filesystem, access control list is enabled by default. This may NOT be the case for other filesystems. Hence, whether ACL is enabled for the filesystem
  must be checked and it can be verified as follows. </br>  
  <img width="952" height="305" alt="image" src="https://github.com/user-attachments/assets/0112fc4f-eb03-4042-b331-8458d3a8e95f" /> </br>  
  Using the command **grep -i 'acl' "/boot/config-$(uname -r)"**, I can search for the string **acl** in the Kernel **config** file to see which
  filesystems have **acl** **enabled**. The setting **CONFIG_XFS_POSIX_ACL=y** confirms that **acl** is enabled for the **XFS** filesystem. </br>  
