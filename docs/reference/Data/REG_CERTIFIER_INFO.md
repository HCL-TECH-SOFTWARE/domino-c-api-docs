##### Data Type : User Registration
##### REG_CERTIFIER_INFO - Structure that defines certifier registration information.
---
```
#include <reg.h>
```

**Definition :**
```
typedef struct
	{
	DWORD   Size;   /* size of this structure - must initialize with sizeof 
(REG_CERTIFIER_INFO) */

	/* certifier name information */
	char    *Country;
	char    *Org;
	char    *OrgUnit;

	/* certifier password information */
	char   *Password;
	WORD   PasswordQuality;

	/* certifier mail information */
	char    *MailServerName;
	char    *MailFileName;
	char    *ForwardAddress;

	/* control flags */
	REGFlags  Flags;

	/* ID file information */
	REG_ID_INFO  *IDInfo;

	/* generic information */
	REG_MISC_INFO *MiscInfo;
	
	DWORD Reserved[4];
	void *pReserved[4];
	} REG_CERTIFIER_INFO;


```

**Description :**

<br>
This structure defines certifier registration information for the REGNewCertifierExtended function.  The entire structure must<br>
be initialized to zero.<br>

<ul>The fields in the structure are (all fields that are not used must be NULL/O):<br>
<br>
Size		Size of this structure - must be initialized with sizeof (REG_CERTIFIER_INFO)<br>
Country		(Optional).  Country code of certifier.<br>
Org  		Organization of the new certifier if of type ORG.<br>
OrgUnit 		Organization unit of the new certifier if of type ORGUNIT.<br>
Password  		(Optional).  The password for the new certifier<br>
PasswordLength	Quality of password required for this certifier (0 - 16)<br>
MailServerName  	(Optional).  Name of mail server where the mail file is to be created.  If the flag fREGCreateMailFileNow is specified and no mail server name is supplied (the pointer is NULL), the 			mail file will be created on the local system.<br>
MailFileName  	(Optional;  required if the flag fREGCreateMailFileNow is specified).  Name of the mail file to create.<br>
ForwardAddress  	(Optional).  Another Notes domain or foreign mail gateway where mail is to be forwarded.<br>
Flags		Flags that are set to specify options.  See Symbolic Value, fREGxxx, in this reference<br>
IDInfo		(Optional). pointer to a structure of REG_ID_INFO<br>
MiscInfo		(Optional). Pointer to a structure of REG_MISC_INFO<br>
Reserved		Reserved - must be 0<br>
pReserved		Reserved - must be NULL</ul>



**See Also :**
[REGNewCertifierExtended](/domino-c-api-docs/reference/Func/REGNewCertifierExtended)
---
