# Change User Owner and Group Owner for Directories and Files  

## chown command  
The **chown** command can be used to modify the **User Owner** and **Group Owner** permissions for Directories and Files - with some conditions.    

### Condition 1:  
A regular user, even as the owner of a file or directory **MUST NEED sudo** to change its **User Owner**.  

### Condition 2:  
**Without sudo**, the owner of a file or directory can use **chown** **ONLY** to change the **Group Owner**, and **ONLY** to a group they are a **member of**.  

