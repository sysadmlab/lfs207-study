# Owner, Group, and Others (World)  
When I long list (**ls -l**) directories and files, the output is as shown in the image below: </br>  
<img width="690" height="165" alt="image" src="https://github.com/user-attachments/assets/0041a6d5-1440-4919-a375-5f53a9d6b6e2" />  
For a directory, the first placeholder is the alphabet **d** denoting a directory, and for a regular file the first placeholder is empty, denoted by a dash (**-**).  
While there are other **types of files**, **d** for directory and **-** for a regular file are the most common ones I have noticed. </br>  

Following the **file type** placeholder is the set of 9 placeholders that define the permissions for the directory/file. These 9 placeholders are split into sets of 3, one set each
for **Owner** also known as **User Owner**, **Group** also known as **Group Owner**, and **Others** also known as **World**.  
The permissions **read**, **write**, and **execute** are assigned to each group as shown below. </br>  
<img width="514" height="164" alt="image" src="https://github.com/user-attachments/assets/8ceabeea-ac67-4095-b085-2b84dd71bb98" />  

# Access Permissions  
A dash (**-**) denotes that the specific permission is not available for that particular group.  
In the image below, the **User Owner** has **Read and Write** permissions, the **Group Owner** has only **Read** permission, and **Others/World** has only **Read** permission.  </br>  
<img width="514" height="164" alt="image" src="https://github.com/user-attachments/assets/91cf9a44-1346-4c6c-89de-9451c4b95b6b" />  

Permissions are examined from **left to right**. For instance, when a user wants to read a file, write to a file, or execute a file:  
1. the **User Owner** permissions are examined first - is the requesting user the **User Owner** ? If **YES**, those permissions are applied. If **NO**  
2. the **Group Owner** permissions are examined next - is the requesting user part of the **Group Owner**? If **YES** those permissions are applied. If **NO**  
3. the **Others/World** permission is applied.  

In the image below the **root** **root** correspond to the **user owner** and the **group owner** for the items.  
<img width="545" height="153" alt="image" src="https://github.com/user-attachments/assets/1946e6b3-6b05-434c-b013-6615315d65fc" />  
