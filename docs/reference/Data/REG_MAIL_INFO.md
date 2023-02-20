##### Data Type : User Registration
##### REG_MAIL_INFO - Structure that defines User Registration Mail Creation Information. 
---
```
#include <reg.h>
```
**Description :**

This structure is used for creating a user's mail file with the REGNewUser 
function. 

        The fields in the structure are:

         MailSystem   defines the type of mail system.
         MailOwnerAccess  mail owner's ACL priviledges (see REG_MAIL_OWNER_xxx).
         DbQuotaSizeLimit  mail file's size limit.   
         DbQuotaWarningThreshold mail file's warning threshold size.
         pMailServerName  name of server the user's mail file will reside on.
         pMailFileName   path name of user's mail file.
         pMailTemplateName  name of mail template
         pMailForwardAddress  forwarding address of  a Domino domain or foreign 
mail gateway.
         pMailACLManager  ACL Manager's name. 
         Spare


**See Also :**
[REGNewUser](/reference/Func/REGNewUser)
[REG_MAIL_OWNER_ACL_xxx](/reference/Symb/REG_MAIL_OWNER_ACL_xxx)
---
