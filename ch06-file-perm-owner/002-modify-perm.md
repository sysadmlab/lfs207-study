# Modifying Permissions  

## chmod command  
Every user can modify the permissions for directories and files he owns (**User Owner**). To modify permissions for items owned by other users, then **sudo** privileges are required.  
Needless to say that **root** can modify permissions for all.  

## Symbolic Method  
The symbolic method uses alphabets and symbols to modify permissions. In the symbolic method the **User Owner** is assigned **u**, the **Group Owner** is assigned **g**
and **Others** is assigned **o**. To add permissions for **All (User Owner, Group Owner, and Others)** the assigned alphabet is **a**.  
To **add** permissions the **addition** symbol **+** is used.  
To **remove** permissions the **subtraction** symbol **-** is used.  

### Scenario - Symbolic Method  
As shown in the image below, the user **tmpusr01** is the **User Owner** of the **/home/tmpusr01** and the group **helpdesk** is the **Group Owner** of the directory.  
**tmpusr01** is providing Read, Write, Execute permissions to the Group Owner and Read, Execute permissions to Others.  
Permissions for can be provided one at a time or combined together.  
For Example, in the image below, chmod **o+x** provides **Execute** permission to **Others**. chmod **g+rw** provides **Read and Write** permissions to the **Group Owner**.  
Likewise, chmod **o-rx** removes **Read and Execute** for **Others**. chmod **g+rw**,**o+r** provides **Read Write** permissions to **Group Owner** and **Read** permission to **Others**. </br>  
<img width="654" height="878" alt="image" src="https://github.com/user-attachments/assets/2c8bb80e-f1f9-41b7-8fbb-932721016564" /> </br>  

### Note
In the above scenario, the user **tmpusr01** has provided permissions to his **Home** folder and contents (tmpusr01 is the User Owner). However, if one is **NOT** the **User Owner** one
requires elevated privileges.  

## Octal Method  
The octal method uses numbers to modify permissions. **Read** is assigned **4**, **Write** is assigned **2**, and **Execute** is assigned **1**. If **Read, Write, and Execute**
permission must be given, then the permission values are added - so **7** (4+2+1). If **Read and Execute** permissions must be given, then the total value is **5** (4+1).  
If **Read** or **Write** or **Execute** alone must be given, then the value is **4** or **2** or **1**. These values apply separately to **User Owner**, **Group Owner**, and **Others**. </br>  

### Scenario - Octal Method  
The user **tmpusr01** wants to enable **Read and Execute** permissions to both **Group Owner** and **Others**. He already has **Read, Write, and Execute** permissions for his **Home** directory.  
So he executes the command **chmod 755 /home/tmpusr01**. In this command the permissions 755 are denote the permissions **Read, Write, and Execute (7)** for **User Owner**, **Read and Execute (5)**
for **Group Owner** and the same permissions (**5**) for **Others**.  
In this example, the first place holder has 7, the second placeholder has 5, and the third placeholder has 5.  
A value of **0** means no permission, so 640 would assign **Read and Write** to **User Owner**, **Read** for **Group Owner** and nothing for **Others**. See image below: </br>  
<img width="636" height="549" alt="image" src="https://github.com/user-attachments/assets/9e753157-bf82-4964-be56-6acc9734bde2" />  
