# Shell Variables and Environment Variables  
Shell Variables live within the current shell and cannot be accessed by another child process. As an example, when I create a Variable in a terminal and open another terminal, I cannot use the Variable I created. Environment Variables on the contrary can be accessed by child processes. </br>  

# How to view Shell and Environment Variables  
The following commands without an option list the Variables:  
1. env
2. printenv
3. export
4. set </br>

The **env** command and the **printenv** commands are external commands whereas the **export** command and the **set** command are Shell Built-in commands.  
The **env** and the **printenv** commands display all the environment variables.  
The **export** command exports a Shell Variable to Environment Variable. Without any options or arguments, the **export** command lists all the exported variables.  
The **set** command lists all Shell Variables, Environment Variables, and Shell functions. This command gives the most elaborate result of all the above commands.  
