##### Data Type : User Registration
##### REG_MAIL_INFO_EXT - Structure that defines User Registration Extended Mail Creation Information.
---
##### #include <reg.h>
**Description :**
This structure defines user registration extended mail creation information. 
for the REGNewPerson function.  The entire structure must be initialized to 
zero.

 The fields in the structure are (all fields that are not used must be NULL/O):

Size    Size of this structure - must be initialized with sizeof 
(REG_MAIL_INFO_EXT).
MailSystem    Defines the type of mail system.
MailOwnerAccess   Mail owner's ACL priviledges (see REG_MAIL_OWNER_ACL_xxx).
DbQuotaSizeLimit   Mail file's size limit.   
DbQuotaWarningThreshold  Mail file's warning threshold size.
pMailServerName   Name of server the person's mail file will reside on.
pMailFileName   Path name of 's mail file.
pMailTemplateName         Name of mail template.
pMailForwardAddress  Forwarding address of  a Domino domain or foreign mail 
gateway.
pMailACLManager   ACL Manager's name. 
hReplicaServers   (Optional.) Handle to a text list of server names where 
replica stubs of the mail file should be
                               created.  The list should be constructed with 
ListAllocate and ListAddEntry.  
    OnDuplicate                   one of REG_FILE_DUP_XXX.
Reserved    Reserved - must be 0.
pReserved    Reserved - must be NULL.

**See Also :**
[ListAddEntry](D:/md_files/ListAddEntry.md)
[ListAllocate](D:/md_files/ListAllocate.md)
[READ_MASK_xxx](D:/md_files/READ_MASK_xxx.md)
[REGNewPerson](D:/md_files/REGNewPerson.md)
[REG_FILE_DUP_xxx](D:/md_files/REG_FILE_DUP_xxx.md)
[REG_MAIL_OWNER_ACL_xxx](D:/md_files/REG_MAIL_OWNER_ACL_xxx.md)
---
