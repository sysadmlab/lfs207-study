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
