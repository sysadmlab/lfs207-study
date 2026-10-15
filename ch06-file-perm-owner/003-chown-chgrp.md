# Change User Owner and Group Owner for Directories and Files  

## chown command  
The **chown** command can be used to modify the **User Owner** and **Group Owner** permissions for Directories and Files.  

### Condition 1:  
A regular user, even as the owner of a file or directory, **CANNOT** use **chown** to change its **User Owner** **without sudo**.  
**Only root** can transfer **User Owner** to a different user.  

### Condition 2:  
**Without sudo**, the owner of a file or directory can use **chown** **ONLY** to change the **Group Owner**, and **ONLY** to a group they are a **member of**.  
The user part must be **left out** or must **match the current owner**.  
