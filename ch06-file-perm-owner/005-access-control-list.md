# Access Control List  

## Scenario and Lab  
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
  <img width="553" height="150" alt="Screenshot From 2026-10-23 19-49-38" src="https://github.com/user-attachments/assets/7c6f9d82-9a12-4149-9468-fe58d8fbadaf" /> </br>  

  
