##### Data Type : User Registration
##### REG_MAIL_INFO_EXT - Structure that defines User Registration Extended Mail Creation Information.
---
```
#include <reg.h>
```

**Definition :**

typedef struct
	{
	DWORD Size;   /* size of this structure - must initialize with sizeof 
(REG_MAIL_INFO_EXT) */
	WORD  MailSystem;
	WORD  MailOwnerAccess;
	DWORD DbQuotaSizeLimit;
	DWORD DbQuotaWarningThreshold;
	char  *pMailServerName;
	char  *pMailFileName;
	char  *pMailTemplateName;
	char  *pMailForwardAddress;
	char  *pMailACLManager;
	DHANDLE hReplicaServers;
	WORD OnDuplicate;  /* one of REG_FILE_DUP_XXX */

	DWORD Reserved[4];
	void *pReserved[4];
	} REG_MAIL_INFO_EXT;



**Description :**

This structure defines user registration extended mail creation information. for the REGNewPerson function.  The entire structure must be initialized to zero.
<ul><br>
<br>
 The fields in the structure are (all fields that are not used must be NULL/O):<br>
<br>
Size				Size of this structure - must be initialized with sizeof (REG_MAIL_INFO_EXT).<br>
MailSystem				Defines the type of mail system.<br>
MailOwnerAccess			Mail owner's ACL priviledges (see REG_MAIL_OWNER_ACL_xxx).<br>
DbQuotaSizeLimit			Mail file's size limit.			<br>
DbQuotaWarningThreshold		Mail file's warning threshold size.<br>
pMailServerName			Name of server the person's mail file will reside on.<br>
pMailFileName			Path name of 's mail file.<br>
pMailTemplateName		       Name of mail template.<br>
pMailForwardAddress		Forwarding address of  a Domino domain or foreign mail gateway.<br>
pMailACLManager			ACL Manager's name.	<br>
hReplicaServers			(Optional.) Handle to a text list of server names where replica stubs of the mail file should be<br>
                               created.  The list should be constructed with ListAllocate and ListAddEntry.  </ul>
    OnDuplicate                   one of REG_FILE_DUP_XXX.
<ul>Reserved				Reserved - must be 0.<br>
pReserved				Reserved - must be NULL.</ul>



**See Also :**
[ListAddEntry](/domino-c-api-docs/reference/Func/ListAddEntry)
[ListAllocate](/domino-c-api-docs/reference/Func/ListAllocate)
[READ_MASK_xxx](/domino-c-api-docs/reference/Symb/READ_MASK_xxx)
[REGNewPerson](/domino-c-api-docs/reference/Func/REGNewPerson)
[REG_FILE_DUP_xxx](/domino-c-api-docs/reference/Symb/REG_FILE_DUP_xxx)
[REG_MAIL_OWNER_ACL_xxx](/domino-c-api-docs/reference/Symb/REG_MAIL_OWNER_ACL_xxx)
---
