# History
The commands that we execute in the command prompt are retained in history. If I execute the command **set | grep HIST**, the variables that are related to history show up. As shown in the image below, there are 3 items of interest:  </br>  
<img width="327" height="556" alt="image" src="https://github.com/user-attachments/assets/235d5dba-6a1f-40e0-8fe1-ef5039446709" />  
**HISTFILE** is the location of the file that stores the history of the commands that I executed. As shown in the image, in the distributions I use, this file -which is a hidden file- is stored at **/home/(userid)/.bash_history**.  
**HISTSIZE** is the maximum number of items the history file can accommodate for the current session.  
**HISTFILESIZE** is the maximum number of items the history file can accommodate.  
From the image above, I note that Ubuntu has a bigger **HISTFILESIZE** than Rocky Linux and openSUSE Leap. </br>  

Executing the **history** command lists all the history items: </br>  
<img width="425" height="380" alt="image" src="https://github.com/user-attachments/assets/4eac0d49-f89a-40ba-ab48-1164dc38c2e9" />  
After the history is displayed, entering the exclamatory sign and a number - for example !9 - executes the ninth command in the list shown; Image below </br>  
<img width="386" height="381" alt="image" src="https://github.com/user-attachments/assets/a0b37644-97a2-461c-9915-b983b867d79c" />  
Executing the command **history (n)** where **n** is a number lists the **n** number of commands from the bottom of the history list; Image below </br>  
<img width="487" height="735" alt="image" src="https://github.com/user-attachments/assets/c6fac956-0462-407c-a556-ff4bd40546e0" />  
