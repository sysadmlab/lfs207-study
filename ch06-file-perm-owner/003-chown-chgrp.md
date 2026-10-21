# Change User Owner and Group Owner for Directories and Files  

## chown command  
The **chown** command can be used to modify the **User Owner** and **Group Owner** permissions for Directories and Files - with some conditions.    

### Condition 1:  
A regular user, even as the owner of a file or directory **MUST NEED sudo** to change its **User Owner**.  

### Condition 2:  
**Without sudo**, the owner of a file or directory can use **chown** **ONLY** to change the **Group Owner**, and **ONLY** to a group they are a **member of**.  


# Scenario  
For this lesson, I did not want to create a directory in my home directory and use the **chown** and **chgrp** commands to change ownership.  
Instead, I wanted to create a separate directory, something that is common for all users to access.  

## Steps taken:  
1. I created a separate SATA disk of size 1GB using the Virtual Machine Manager </br>  
<img width="634" height="277" alt="Screenshot From 2026-10-16 21-22-09" src="https://github.com/user-attachments/assets/306d1c76-1f94-4a4f-9ab0-cdb9d42f573f" /> </br>  
2. After rebooting the system, I had to initialise the disk, I knew I had to use the **fdisk** command. However, I did not know how to proceed further. </br>  
3. I executed **sudo fdisk --help** and then **sudo fdisk -l**. This listed the new block device **/dev/sdb**. </br>  
4. Now I executed **sudo fdisk /dev/sdb** and using the menu I **create a new label** by selecting option **g** - create an empty GPT partition table. </br>  
5. Pressing **w** saved the changes and exited the fdisk application. </br>  
6. Then I went back to the **fdisk** command and this time I selected option **n** to create new partition. I accepted the **default** start and end parameters for the partition. </br>  
7. Again, I saved the changes and exited the **fdisk** application by selecting option **w**. </br>  
8. Now at this point, I created a partition **sdb1** - **/dev/sdb1**. </br>  
9. Now that I create the patition, I did not know which command to use to put a filesystem in the new partition. </br>  
10. So I used the **apropos filesystem** command which guided me towards the command **mkfs**. </br>  
11. Because I not used to **mkfs** command many times, I used the **sudo mkfs --help** to go through the command options. </br>  
12. Keeping it simple, I executed the command **sudo mkfs -t ext4 /dev/sdb1** to put an **ext4** filesystem on partition **/dev/sdb1**. </br>  
13. At this point when I executed the command **lsblk -f**, I could see the device tree for **/dev/sdb** and **/dev/sdb1**. </br>  
14. However when I executed **df -hT** I could not see the partition **/dev/sdb1**. </br>  
15. At this point I realised that only if I **mount** the partition **/dev/sdb1** to a **mount point** will it show in the **df -hT** command result. </br>  
16. So with elevated priveleges (**sudo**) I created a directory **stor** in the root (/) partition. </br>  
17. Then using the command **sudo mount /dev/sdb1 /stor** </br>  
18. I knew that although I can mount the partition using the **mount** command, it would NOT be permanent unless I make an entry in the **/etc/fstab** file. </br>  
19. I knew I had to get the UUID of the device **/dev/sdb1** and make an entry in the **/etc/fstab** file, but how do I paste it in the file was the challenge. </br>  
20. I executed **lsblk -f /dev/sdb1** to get the **UUID** of the device and saved it in a text file. </br>  
21. However, when I used the **nano** text editor was the real challenge to copy the UUID and paste it in the fstab file. </br>  
22. When I select the UUID, copy it, close the nano editor, open the fstab file using nano and paste it, the buffer was empty and nothing got copied. </br>  
23. After trying this a few times, I really didn't know how to go further. </br>  
24. At this point, I decided to login as root **su -l root** and execute **lsblk -f /dev/sdb1 >> /etc/fstab** to append the result directly to the fstab file. </br>  
25. Then I opened the fstab file and removed everything else than the UUID. </br>  
<img width="1120" height="317" alt="image" src="https://github.com/user-attachments/assets/5f1a7467-126d-4294-9662-136e95c57dab" /> </br>   
26. After saving the above entry and rebooting my virtual machine, the device was mounted at the designated directory. </br>  
<img width="893" height="491" alt="image" src="https://github.com/user-attachments/assets/955373e1-cf4a-4921-8a21-fef8e1b74fc5" /> </br>  
27. Then using the command **sudo chown as:as /stor** I changed ownership of the directory from **root:root** to **as:as** </br>  

## chown demo  
For the purpose of these demos I have created two more user accounts and two groups. The user accounts **tmpusr01** and **tmpusr02** belong to group **helpdesk**. My user account **as** belongs to group **boss**. </br>  
<img width="766" height="524" alt="Screenshot From 2026-10-18 17-42-22" src="https://github.com/user-attachments/assets/30e0b8b2-c35c-4e6c-99bc-2574d124fa7e" /> </br>  
The **chown** command requires elevated privileges; executing the command without **sudo** results in an error. </br>  

1. In the first command, using **sudo**, I have changed the **user owner** to **tmpusr01** - **sudo chown tmpusr01:as chowntest**. In the command the colon (:) symbol separates the **user_owner:group_owner**. </br>  
2. In the second command, I wanted to change only the **user owner**, hence I've executed **sudo chown as: chowntest**. Here I have left a blank space after the colon - this means
that there is no change to the **group owner**. </br>  
3. In the third command which is **sudo chown :boss chowntest**, I have changed only the **group owner** to **boss**. I have left a blank space before the colon symbol, denoting that
I do NOT want to change the **user owner**. </br>  
4. In the fourth command, I have changed both the **user owner** and the **group owner** by using the command **sudo chown tmpusr02:helpdesk chowntest**. </br>  
<img width="696" height="720" alt="image" src="https://github.com/user-attachments/assets/2fe8f167-3c33-4160-8ba5-6d50287dc1bb" /> </br>  


## chgrp demo  
The **chgrp** command is used to change the **group owner** and as mentioned earlier, the **chgrp** command does NOT require **sudo** privileges when used to by the **user owner**
to change to a group that he is a member of. </br>  
<img width="660" height="384" alt="image" src="https://github.com/user-attachments/assets/d5192956-7076-4ebb-b60c-65ed60f38a8f" /> </br>  

From the image above, it can be inferred that a user who is the **user owner** of a file can use the **chgrp** command to change the **group owner** of the file - provided
he belongs to the **target group owner**. Else, **sudo** permissions will be required to complete the operation. </br>  


### Followed the "Scenario" mentioned above in my Rocky Linux VM for the **facl** demo:  
<img width="1177" height="477" alt="image" src="https://github.com/user-attachments/assets/e1a734ac-f79a-4576-986e-2b19f6e5fd71" />  
<img width="758" height="201" alt="Screenshot From 2026-10-21 16-36-32" src="https://github.com/user-attachments/assets/2eb19f31-370a-4534-93f3-3b11db4c3d6a" />  
<img width="830" height="155" alt="Screenshot From 2026-10-21 16-37-46" src="https://github.com/user-attachments/assets/c7682f11-0e7f-483d-8244-b679610e0f1d" />  



