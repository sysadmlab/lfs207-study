# Shell Variables and Environment Variables  
Shell Variables live within the current shell and cannot be accessed by another child process. As an example, when I create a Variable in a terminal and open another terminal, I cannot use the Variable I created. Environment Variables on the contrary can be accessed by child processes. </br>  

# How to view Shell and Environment Variables  
The following commands without an option list the Variables:  
1. env
2. printenv
3. export
4. set </br>

# How do the commands env, printenv, export, and set differ:  
1. The **env** command and the **printenv** commands are external commands whereas the **export** command and the **set** command are Shell Built-in commands.  
2. The **env** and the **printenv** commands display all the **environment** variables.  
3. The **export** command exports a Shell Variable to Environment Variable. Without any options or arguments, the **export** command lists all the exported variables.  
4. The **set** command lists all Shell Variables, Environment Variables, and Shell functions. This command gives the most elaborate result of all the above commands. </br>

The results of these four commands are shown below: </br>  
<img width="1398" height="925" alt="Screenshot From 2026-08-27 16-22-53" src="https://github.com/user-attachments/assets/3c00688e-df70-45c9-a0cf-6ebba8ed8943" />  </br>  

A few other Environment Variables are - as shown in the image below: </br>  
<img width="866" height="205" alt="Screenshot From 2026-08-27 16-27-08" src="https://github.com/user-attachments/assets/7b20378f-be8f-4fbd-aedd-1d6173798075" /> </br>  

In the image above, the **echo** command prints the given argument. To display the value of a variable, the variable MUST be prefixed with a **$** dollar symbol. Else, **echo** command will consider it a string and print as such. See image below for the difference: </br>  
<img width="487" height="134" alt="Screenshot From 2026-08-27 16-31-35" src="https://github.com/user-attachments/assets/c0e1b506-6946-4e69-8010-43bf8492b6f9" /> </br>  

### Side Note: The **-e** option with the **echo** command ensures that **\n** prints the result in a new line. Without the option **-e**, **echo** command would treat **\n** as **n**. The image below shows the difference. </br>  
<img width="592" height="212" alt="Screenshot From 2026-08-27 16-46-20" src="https://github.com/user-attachments/assets/6e4b3c6a-6843-4027-88af-5d814ebec8f6" />  

# How to declare a variable  
VARIABLE=VALUE is the simple way to declare a variable. **Note** that the **=** symbol must not be preceded or succeeded with a blank space.  
For example: HOWSTHEWEATHER=ITSSUNNYOUTSIDE assigns the value **ITSSUNNYOUTSIDE** to the variable **HOWSTHEWEATHER**.  
**echo** $HOWSTHEWEATHER will print ITSSUNNYOUTSIDE. </br>  
<img width="583" height="151" alt="Screenshot From 2026-08-27 16-52-08" src="https://github.com/user-attachments/assets/afaeca80-acc1-43ae-944a-af5877163567" />  

# Distinction between Shell Variable and Environment Variable  
In the previous step, I have created a variable. This is a Shell Variable - which means that this variable cannot be accessed by Child Processes. I am going to demonstrate that below: </br>  
<img width="676" height="307" alt="image" src="https://github.com/user-attachments/assets/6378d811-8ee2-4ae8-b9f5-82dbf12640aa" />  

