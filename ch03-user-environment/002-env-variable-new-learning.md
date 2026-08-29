# Creating entries in the .bashrc file  
Another way to achieve the **export** of a "Shell Variable" is to make an entry in the .bashrc file. This method is a permanent way to export a shell variable.  
The .bashrc file is a hidden file (because of the preceeding **.**) and it is part of the every user's **home** directory.  
The command **ls -la** displays the hidden files in a directory: </br>  
<img width="615" height="239" alt="Screenshot From 2026-08-29 08-47-27" src="https://github.com/user-attachments/assets/0a66e4db-6d1e-4b93-b7ea-616bb736e7ed" />  
1. I am going to create a new variable (VARNOW) and set the results of the **date** command to this variable.
2. Then I am going to export the variable - only this time - with an entry in .bashrc.
3. Then I am going to run the command **source** with .bashrc as the argument. This ensures that contents of file .bashrc are run in the same shell.
4. Another way to achieve the same result mentioned in point 3 is to exit the current terminal window and open a new terminal so that the .bashrc file's contents are loaded.
5. Then I will print the contents of the variable **VARNOW**.
6. Open a child process by executing the **bash** command and print the contents of **VARNOW**
The image below is a demonstration of the steps mentioned above: </br>
<img width="1070" height="945" alt="image" src="https://github.com/user-attachments/assets/b3003f9c-8d90-4719-a8d7-86a1009f0b5e" />



