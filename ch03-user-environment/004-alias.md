# Alias
As the name suggests an "Alias" stands in place of a command that I want to execute.  
Executing the command **alias** as such without an argument displays all the aliases. In the image below, the alias **ls** actually executes **ls --color=auto** </br>  
<img width="1161" height="327" alt="Screenshot From 2026-09-08 18-57-34" src="https://github.com/user-attachments/assets/9a4755d4-2548-405d-ba62-89b6e8c72f0a" /> </br>  

## Creating an Alias  
I can create an **alias** for the command I want to run. For example, every time I execute **hclr** I want to clear bash history. To achieve this, using the command **alias hclr='history -c'**. There must be **NO** white before and after the **=** symbol; and I have encapsulated the definition in single quotes. </br>  
<img width="446" height="215" alt="Screenshot From 2026-09-08 19-05-30" src="https://github.com/user-attachments/assets/9512eba4-452c-428d-b705-e6fe7d4daab3" />  
As seen in the image above, there were about 100+ items in bash history when I defined my new **alias**. Then I executed the alias **hclr** the command **history -c** was executed and the history was cleared. This is a basic example to demonstrate the usage of alias. </br>  

## Removing an Alias  
The command **unalias** can be used to remove an alias. For example, I will use the **unalias** command to remove the alias I just created.  
**unalias hclr** will remove the definition for the alias name **hclr**. </br>  
<img width="445" height="429" alt="Screenshot From 2026-09-08 19-11-45" src="https://github.com/user-attachments/assets/ad73ceb7-6e35-4317-a46c-4642730bd79d" />  

## Persistent Alias  
Aliases created in a interactive bash shell will remain until the shell is closed. This means that a child process cannot access the alias that I created. Similar to the environment variables I came across in the earlier lesson, to make an alias persistent, an entry has to be made in the **.bashrc** file. </br>  
<img width="643" height="433" alt="image" src="https://github.com/user-attachments/assets/bd8778af-3d47-4eaf-a49a-7bf1e1988022" />  
As can be noted in the image above, I created an alias **hclr**, and, obviously, it was accessible in the current shell. Then I opened a new shell with the command **bash**. The alias **hclr** was **NOT** available for the child process. For this reason, an entry in the **.bashrc** file is carried out.  
<img width="881" height="622" alt="image" src="https://github.com/user-attachments/assets/c171a36f-9513-42b7-80c4-61eb45176066" />  
As seen in the image below, I have made an entry in the **.bashrc** file, and I confirm this with the **grep** command. Meanwhile, I ran the **source .bashrc** command to implement the changes I made the the **.bashrc** file. By executing the command **bash** I opened a new shell (a child process) and the alias is accessible by the child process. I have confirmed this using the command **ps -ef**. As I can see the **-bash** with the "hyphen" is my login shell and **bash** is the child process the process IDs will reveal the **parent-child** relationship. </br>  
<img width="782" height="615" alt="image" src="https://github.com/user-attachments/assets/e296727e-7688-4cc7-a005-d99785f25fa2" />  

# NOTE TO SELF  
**DO NOT QUOTE THE ENTIRE ALIAS DEFINITION; JUST THE DEFINITION.**  
alias 'hclr=history -c' is **NOT** incorrect **BUT** the definition is **NOT** appropriate. Instead, **alias hclr='history -c'** is the appropriate definition.  
