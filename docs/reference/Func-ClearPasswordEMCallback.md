##### Function : Extension Manager
##### ClearPasswordEMCallback - Extension Manager callback for EM_CLEARPASSWORD
---
##### #include <extmgr.h>
STATUS LNPUBLIC **ClearPasswordEMCallback(**
void);
**Description :**
EM_CLEARPASSWORD occurs when a password is to be "cleared" either due to a 
timeout or because the user has pressed F5.  EM_CLEARPASSWORD can only be 
registered with the EM_REG_BEFORE flag.  An extension manager hook for 
EM_CLEARPASSWORD cannot be called after Domino or Notes processes this 
operation.
**Parameters :**

Output :
(routine)  -  
ERR_EM_CONTINUE


**See Also :**
[EM_xxx](D:/md_files/EM_xxx.md)
---
