# Access Control List  
From the mistakes made and lessons learnt from **005-access-control-list.md** and **001-acl.md respectively**, I have made changes to the lab setup. </br>  
The Users and Groups information is presented below: </br>  
## Users

| User | Groups | Role |
|---|---|---|
| `as` | `as`, `public` | Administrator (runs all commands with `sudo`) |
| `joe` | `joe`, `ithelpdesk`, `public` | IT Helpdesk |
| `robin` | `robin`, `ithelpdesk`, `public` | IT Helpdesk |
| `christina` | `christina`, `accounting`, `public` | Accounting |
| `katie` | `katie`, `accounting`, `public` | Accounting |

## Groups

| Group | Members | Owns directory |
|---|---|---|
| `ithelpdesk` | `joe`, `robin` | `/stor/itsupport` |
| `accounting` | `christina`, `katie` | `/stor/accounts` |
| `public` | `as`, `joe`, `robin`, `christina`, `katie` | `/stor/public` |

Here's how the directory structure looks now </br>  

| Path | Owner:group | Mode |
|---|---|---|
| `accounts` | `root:accounting` | `drwxrws--T` (`3770`) |
| `accounts/itinvoices` | `root:accounting` | `drwxrws--T` (`3770`) |
| `itsupport` | `root:ithelpdesk` | `drwxrws--T` (`3770`) |
| `itsupport/capex` | `root:ithelpdesk` | `drwxrws--T` (`3770`) |
| `itsupport/capex/oct2026.xlsx` | `root:ithelpdesk` | `-rw-rw----` (`660`) |
| `public` | `root:public` | `drwxrwxrwt` (`1777`) |

In the new structure, **root** is the **User Owner** of all the directories. The **accounts** and **itsupport** directories are **Group** owned by the respective
departments. </br>  

Using **sudo** with the **getfacl** command ensures that the **Set GID** and **Sticky Bit** special permissions are preserved. </br>  
<img width="800" height="876" alt="image" src="https://github.com/user-attachments/assets/f304d021-2e4c-40de-b987-3b9b2d44dd45" /> </br>  
So when **Robin** from the **ithelpdesk** group creates the **invoice01.pdf** file in the **accounts/itinvoices** directory, the **accounting** group by default owns it. </br>  
<img width="666" height="643" alt="image" src="https://github.com/user-attachments/assets/6a7904f7-1d5a-46a6-82de-3dddf24d3404" /> </br>  
The following image shows that **Christina** can **read** and **write** to the **oct2026.xlsx** file inside the **ithelpdesk/capex** directory while **katie** cannot

