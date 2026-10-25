# Access Control List  
From the mistakes made and lessons learnt from **005-access-control-list.md** and **001-acl.md respectively**, I have made changes to the lab setup.
Here's how the directory structure looks now </br>  

| Path | Owner:group | Mode |
|---|---|---|
| `accounts` | `root:accounting` | `drwxrws--T` (`3770`) |
| `accounts/itinvoices` | `root:accounting` | `drwxrws--T` (`3770`) |
| `itsupport` | `root:ithelpdesk` | `drwxrws--T` (`3770`) |
| `itsupport/capex` | `root:ithelpdesk` | `drwxrws--T` (`3770`) |
| `itsupport/capex/oct2026.xlsx` | `root:ithelpdesk` | `-rw-rw----` (`660`) |
| `public` | `root:public` | `drwxrwx--T` (`1770`) |
