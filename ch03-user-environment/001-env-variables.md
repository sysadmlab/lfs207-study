# Shell Variables and Environment Variables  
Shell Variables live within the current shell and cannot be accessed by another child process. As an example, when I create a Variable in a terminal and open another terminal, I cannot use the Variable I created. Environment Variables on the contrary can be accessed by child processes. </br>  

# How to view Shell and Environment Variables  
The following commands without an option list the Variables:  
1. env
2. printenv
3. export
4. set </br>

1. The **env** command and the **printenv** commands are external commands whereas the **export** command and the **set** command are Shell Built-in commands.  
2. The **env** and the **printenv** commands display all the **environment** variables.  
3. The **export** command exports a Shell Variable to Environment Variable. Without any options or arguments, the **export** command lists all the exported variables.  
4. The **set** command lists all Shell Variables, Environment Variables, and Shell functions. This command gives the most elaborate result of all the above commands.  
The results of these four commands are shown below: </br>  
<img width="1398" height="925" alt="Screenshot From 2026-08-27 16-22-53" src="https://github.com/user-attachments/assets/3c00688e-df70-45c9-a0cf-6ebba8ed8943" />  </br>  
A few other Environment Variables are - as shown in the image below: </br>  
<img width="866" height="205" alt="Screenshot From 2026-08-27 16-27-08" src="https://github.com/user-attachments/assets/7b20378f-be8f-4fbd-aedd-1d6173798075" />  
In the above image, **echo** command prints the given argument. To display the value of a Variable, the Variable MUST be prefixed with a **$** dollar symbol. Else, **echo** command will consider it a string and print as such. See image below: </br>  
<img width="487" height="134" alt="Screenshot From 2026-08-27 16-31-35" src="https://github.com/user-attachments/assets/c0e1b506-6946-4e69-8010-43bf8492b6f9" />  


