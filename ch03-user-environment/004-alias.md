# Alias
As the name suggests an "Alias" stands in place of a command that I want to execute.  
Executing the command **alias** as such without an argument displays all the aliases. In the image below, the alias **ls** actually executes **ls --color=auto** </br>  
<img width="1161" height="327" alt="Screenshot From 2026-09-08 18-57-34" src="https://github.com/user-attachments/assets/9a4755d4-2548-405d-ba62-89b6e8c72f0a" /> </br>  

## Creating an Alias  
I can create an **alias** for the command I want to run. For example, every time I execute **hclr** I want to clear bash history. To achieve this, using the command **alias 'hclr=history -c'**. There must be **NO** white before and after the **=** symbol; and I have encapsulated the definition in single quotes. </br>  
<img width="446" height="215" alt="Screenshot From 2026-09-08 19-05-30" src="https://github.com/user-attachments/assets/9512eba4-452c-428d-b705-e6fe7d4daab3" />  
As seen in the image above, there were about 100+ items in bash history when I defined my new **alias**. Then I executed the alias **hclr** the command **history -c** was executed and the history was cleared. This is a basic example to demonstrate the usage of alias. </br>  

## Removing an Alias  
The command **unalias** can be used to remove an alias. For example, I will use the **unalias** command to remove the alias I just created.  
**unalias hclr** will remove the definition for the alias name **hclr**. </br>  
<img width="445" height="429" alt="Screenshot From 2026-09-08 19-11-45" src="https://github.com/user-attachments/assets/ad73ceb7-6e35-4317-a46c-4642730bd79d" />  
