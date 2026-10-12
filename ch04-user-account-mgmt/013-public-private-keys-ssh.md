# Generating Private and Public Keys for SSH:  
In addition to password-based authentication, key-based authentication can be enabled for SSH using the command **ssh-keygen**.  
The following image shows the steps I have taken to generate Private and Public keys using the **ssh-keygen** command. </br>  
<img width="972" height="832" alt="image" src="https://github.com/user-attachments/assets/8ff3db63-a9cd-4ee7-b27f-a73ddc987560" /> </br>  

# Sharing Public Key with the remote host:  
The Public and Private keys are linked together. While there is no harm in sharing the Public key, the Private key must be safeguarded by all means. </br>  
<img width="656" height="279" alt="Screenshot From 2026-10-12 05-32-33" src="https://github.com/user-attachments/assets/be558a0a-ce6a-49b5-a36f-562b0f9321f5" />  
In the image above, the file **rock9_id_ed25519.pub** is the Public key: the **.pub** extension denotes that. The file **rock9_id_ed25519** is the Private key and must **NEVER** be shared.  
In order to put Key-based Authentication to use, I have to share the Public key with the remote computer. To achieve this, I can use the command **ssh-copy-id**.  
The Public key is appended to a file named **authorized keys** under the directory **/home/<connectinguser>/.ssh/** of the remote computer accepting the SSH connection.  
So in my case, I would expect to find the '**authorized keys**' under the directory **/home/sshtstusr/.ssh** in the Rocky Linux SSH Server I am connecting to.  
At this point, I have connected to the remote server via SSH and I note that **.ssh** directory does NOT exist. Hence, I am creating the directory, as shown below, and logging out. </br>  
<img width="683" height="633" alt="image" src="https://github.com/user-attachments/assets/3311d197-a05c-4273-82cf-6b02f37fad68" />  
Now, I can perform two actions to transfer the Public key to the remote server; The easiest way is to use the **ssh-copy-id** command in my Alma Linux desktop and allow the 
program to transfer the key to the remote server (**OR**) the less-easy way of opening the Public key (**.pub** file), copying the key, connecting to the remote server, creating a file
named **authorized keys**, and appending the copied Public key to the file.  
For the sake of ease, I will use the command **ssh-copy-id**. </br>  

# ssh-copy-id Command:  
If I see the **man** page for the command **ssh-copy-id**, using the option **-i** I can specify the file that needs to be copied over. </br>  
<img width="903" height="549" alt="image" src="https://github.com/user-attachments/assets/0cc1fd06-e20b-47b1-bd1c-1d47cae327a8" />
