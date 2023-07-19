##### Data Type : User Registration
##### REG_MAIL_INFO - Structure that defines User Registration Mail Creation Information. 
---
```
#include <reg.h>
```

**Definition :**

typedef struct {
   WORD   MailSystem;
   WORD   MailOwnerAccess;
   DWORD  DbQuotaSizeLimit;
   DWORD  DbQuotaWarningThreshold;
   char * pMailServerName;
   char * pMailFileName;
   char * pMailTemplateName;
   char * pMailForwardAddress;
   char * pMailACLManager;
   DWORD  Spare[4];
} REG_MAIL_INFO;

**Description :**

This structure is used for creating a user's mail file with the REGNewUser function. 
<ul><br>
<br>
        The fields in the structure are:<br>
<br>
         MailSystem			defines the type of mail system.<br>
         MailOwnerAccess		mail owner's ACL priviledges (see REG_MAIL_OWNER_xxx).<br>
         DbQuotaSizeLimit		mail file's size limit.			<br>
         DbQuotaWarningThreshold	mail file's warning threshold size.<br>
         pMailServerName		name of server the user's mail file will reside on.<br>
         pMailFileName			path name of user's mail file.<br>
         pMailTemplateName		name of mail template<br>
         pMailForwardAddress		forwarding address of  a Domino domain or foreign mail gateway.<br>
         pMailACLManager		ACL Manager's name.	<br>
         Spare</ul>



**See Also :**
[REGNewUser](/domino-c-api-docs/reference/Func/REGNewUser)
[REG_MAIL_OWNER_ACL_xxx](/domino-c-api-docs/reference/Symb/REG_MAIL_OWNER_ACL_xxx)
---
