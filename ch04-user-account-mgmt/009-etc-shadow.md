# The shadow file  
The **shadow** file located at /etc/shadow contains the hashed password and password age details for user accounts.  
Each record is one line and consists of 9 fields, and they are:  
1. The exact username as in the **/etc/passwd** file  
2. The hashed password for the user account  
3. Last password change - mentioned as the number of days since the epoch (that is 01 January 1970)  
4. Minimum number of days that must pass before a password change. 0 means no restriction  
5. Maximum number of days a password if valid. By default this field is set to 99999  
6. Number of days before password expiration the user will start receiving warning. By default this field is set to 7  
7. Number of days after password expiration the account is still usable before the account is locked. By default there is no value in this field  
8. Account expiration date mentioned as number of days from the epoch (that is 01 January 1970). By default there's no value in this field.
When the date is set in the past, the account is considered expired. Setting this field to -1 means that the account never expires. 0 means the day of epoch 01 January 1970.  
9. This field is reserved for future use. </br>  

<img width="1009" height="200" alt="Screenshot From 2026-10-05 22-01-50" src="https://github.com/user-attachments/assets/6269ade3-0a47-441e-a4a3-84b07611d039" />  

In the above image, let's consider the 3rd field which is the **Last Password Change**. It has a value 20724 - which is 20724 days since 01 January 1970. This number denotes Monday 28th September 2026 - the day the account **tech01**'s password was last changed.  
