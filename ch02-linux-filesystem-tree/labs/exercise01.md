# Lab Exercise  

## Scenario: Use the du utility to calculate the overall size of each of your system’s top-level directories. </br>  

### Learning:  
1. When using **du** command with the **/** directory, it is essential to use elevated privileges (**sudo**). Else, I get "**Permission Denied**" errors.  
   <img width="791" height="291" alt="Screenshot From 2026-08-20 14-42-41" src="https://github.com/user-attachments/assets/cc115ece-ffa2-467b-ae71-5e10b704c929" />  
2. Then I used the command **sudo du -sh /** to summarise the **Disk Usage** for the **/** directory and provide the details in **human-readable** format (if not, the result will be in bytes). </br>  
3. Executing the above command, results in some errors from the **/proc** directory. </br>  
   <img width="769" height="165" alt="Screenshot From 2026-08-20 14-46-13" src="https://github.com/user-attachments/assets/590eb6ee-65e7-4908-9640-54ad4cec5bd6" />  
4. Since my objective is the find "Disk Usage" of contents stored, I am going to skip the **/proc** directory. This can be achieved by using the **--exclude** option. The list of options can be found using the **du --help** command. I can use the **man** page also.  
5. So I'm going to use the command **sudo du -sh / --exclude=proc**  </br>  
   <img width="518" height="132" alt="Screenshot From 2026-08-20 14-52-55" src="https://github.com/user-attachments/assets/17bc402d-aa1f-4432-ae84-25bc880ce970" />
6. The above image is the result. However, I would like to see every directory listed and corresponding size displayed. From trial and error, I figured out that the command **sudo du -hc -d 1 / --exclude=proc** will do the trick. </br>
   <img width="517" height="419" alt="Screenshot From 2026-08-20 14-56-37" src="https://github.com/user-attachments/assets/0823bc05-2521-4eff-87af-88f55154b0f4" />
7. The option **-c** gives the grand total, **-d** defines the **depth**, that is how deep we want to traverse the filesystem tree. I have set **-d** to **1**.

### Text Book Solution:  
**sudo du --max-depth=1 -hx /**  
The --max-depth=1 is the same as -d 1. The -x option means "Stay on one filesystem; don’t look at directories that are not on the / partition. In this case that means ignore /dev /proc /run /sys".  
Implementing the "Text Book" solution gives the following output: </br>  
<img width="508" height="367" alt="Screenshot From 2026-08-20 15-07-21" src="https://github.com/user-attachments/assets/598ae2e5-943a-468d-acd5-b4e006755d3e" />  
