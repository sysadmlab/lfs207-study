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
So in my case, I would expect to find the '**authorized keys**' under the directory **/home/sshtstusr/.ssh** in the Rocky Linux SSH Server I am connecting to. </br>  
<img width="683" height="633" alt="image" src="https://github.com/user-attachments/assets/cde06436-fa38-49e4-a310-6983ec6cc262" />
