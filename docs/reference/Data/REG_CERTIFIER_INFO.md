##### Data Type : User Registration
##### REG_CERTIFIER_INFO - Structure that defines certifier registration information.
---
```
#include <reg.h>
```
**Description :**

This structure defines certifier registration information for the 
REGNewCertifierExtended function.  The entire structure must
be initialized to zero.

The fields in the structure are (all fields that are not used must be NULL/O):

Size  Size of this structure - must be initialized with sizeof 
(REG_CERTIFIER_INFO)
Country  (Optional).  Country code of certifier.
Org    Organization of the new certifier if of type ORG.
OrgUnit   Organization unit of the new certifier if of type ORGUNIT.
Password    (Optional).  The password for the new certifier
PasswordLength Quality of password required for this certifier (0 - 16)
MailServerName   (Optional).  Name of mail server where the mail file is to be 
created.  If the flag fREGCreateMailFileNow is specified and no mail server 
name is supplied (the pointer is NULL), the    mail file will be created on the 
local system.
MailFileName   (Optional;  required if the flag fREGCreateMailFileNow is 
specified).  Name of the mail file to create.
ForwardAddress   (Optional).  Another Notes domain or foreign mail gateway 
where mail is to be forwarded.
Flags  Flags that are set to specify options.  See Symbolic Value, fREGxxx, in 
this reference
IDInfo  (Optional). pointer to a structure of REG_ID_INFO
MiscInfo  (Optional). Pointer to a structure of REG_MISC_INFO
Reserved  Reserved - must be 0
pReserved  Reserved - must be NULL


**See Also :**
[REGNewCertifierExtended](/reference/Func/REGNewCertifierExtended)
---
