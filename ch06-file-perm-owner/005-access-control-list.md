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
  Also, classic permissions (minimal ACL) only allow one **owner** and **group** for an item. </br>  
  Hence for such occasions when a specific user requires specific access to files, the Access Control List (extended ACL) comes into play. </br>  

  ### Linux File Access Control List  
  For the XFS filesystem, access control list is enabled by default. This may NOT be the case for other filesystems. Hence, whether ACL is enabled for the filesystem
  must be checked and it can be verified as follows. </br>  
  <img width="952" height="305" alt="image" src="https://github.com/user-attachments/assets/0112fc4f-eb03-4042-b331-8458d3a8e95f" /> </br>  
  Using the command **grep -i 'acl' "/boot/config-$(uname -r)"**, I can search for the string **acl** in the Kernel **config** file to see which
  filesystems have **acl** **enabled**. The setting **CONFIG_XFS_POSIX_ACL=y** confirms that **acl** is enabled for the **XFS** filesystem. </br>  
  <img width="632" height="318" alt="image" src="https://github.com/user-attachments/assets/39671d59-9f92-4617-9836-8b287737aebf" /> </br>  
  Access Control List allows additional **users** and **groups** to be added in addition to the classic **user owner**, **group owner**, and **Others**. </br>  
  **NOTE** The following image shows the current permissions of the files and directories. The permissions are followed by a **.** symbol - denoting SELinux. </br>  
  <img width="640" height="363" alt="image" src="https://github.com/user-attachments/assets/61ebaa5e-c147-4d10-9cc3-c03dbf90e7ec" /> </br>  

  ### Commands used  
  **getfacl**  - to display the current access control list </br>  
  **setfacl** - to add or remove users from the access control list </br>  

  ### Adding named users and groups entries  
  The following image shows the results when I execute the **getfacl** command against the directories and file. </br>  
  <img width="773" height="859" alt="image" src="https://github.com/user-attachments/assets/b093c137-9a25-4c14-a0b9-d41ff24a7caf" /> </br>  
  Using the **setfacl** command with option **-m** modifies the extended access control list to add or replace entries. To remove an entry, the option **-x**
  should be used. </br>  
  Currently I'm at the **/stor** directory and I'm going to use the command **setfacl -m user:christina:x itsupport** to allow **Christina** to change to the **itsupport** directory. </br>  
  <img width="590" height="383" alt="image" src="https://github.com/user-attachments/assets/956f0387-8e02-4d06-96e5-9d56b0d1ee2f" /> </br>  
  The first thing I note after executing the **setfacl** command to give **Christina** execute permissions is how the **dot** **.** has changed to a **plus** **+** denoting
  that there is something more to the **itsupport** directory. </br>  
  <img width="612" height="191" alt="image" src="https://github.com/user-attachments/assets/612375fd-5070-4f32-bbeb-1c525361004e" /> </br>  
  Next, when I execute **getfacl** I note the change in permissions. Now, there is a second **user** entry with **Christina** and she has **execute** permissions. </br>  
  To verify this, I switch user to Christina and tried to change the directory to **itsupport** and **it works** Christina can now change directory to **itsupport** but she
  cannot list the contents of the directory, because I have not given her **read** permissions in the **setfacl** command above. </br>  
  <img width="634" height="448" alt="image" src="https://github.com/user-attachments/assets/ab7715c9-52e8-442b-8619-981d61f8c01f" /> </br>  
  Further, I executed the command **setfacl -m u:christina:r-x capex** to give **read** and **execute** permissions to **Christina**. Note that instead
  of **user** I have used **u** and instead of permissions **rx** I have used **r-x**. They mean the same. </br>  
  <img width="715" height="485" alt="image" src="https://github.com/user-attachments/assets/16f68df5-780c-495b-b808-b53e80ebee9b" /> </br>  
  With the named permissions given to Christina, she can now **cd** to the **capex** directory and with the **read** permission, she can list the directory's contents. </br>  
  As a next step, using the command **setfacl -m u:christina:rw- oct2026.xlsx** to provide **read** and **write** access to the file. </br>  
  

