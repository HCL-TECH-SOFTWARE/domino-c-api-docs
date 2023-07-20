##### Data Type : User Registration
##### REG_SERVER_INFO - Structure that defines server registration information.
---
```
#include <reg.h>
```

**Definition :**
```
typedef struct
	{
	DWORD Size;  /* size of this structure - must initialize with sizeof 
(REG_SERVER_INFO) */

	/* server name information */
	char *Name;
	char *OrgUnit;
	char *Title;
	char *DomainName;
	char *NetworkName;
	char *AdminName;

	/* server password information */
	char   *Password;
	WORD   PasswordQuality;

	/* control flags */
	REGFlags  Flags;

	/* server internet information */
	char *HostName;
	HCERTIFIER hInternetCertCtx;
	char *KeyringFileName;
	char *KeyringPassword;

	/* ID file information */
	REG_ID_INFO  *IDInfo;

	/* generic information */
	REG_MISC_INFO *MiscInfo;

	DWORD Reserved[4];
	void *pReserved[4];
	} REG_SERVER_INFO;


```

**Description :**

<br>
This structure defines server registration information for the REGNewServerExtended2 function.  The entire structure must<br>
be initialized to zero.<br>

<ul>The fields in the structure are (all fields that are not used must be NULL/O):<br>
<br>
Size		Size of this structure - must be initialized with sizeof (REG_SERVER_INFO)<br>
Name		The name of the new server<br>
OrgUnit  		(Optional).  Organizational unit of the new server (hierarchical only and in addition to that derived from the certifier context).<br>
ServerTitle  	(Optional).  The server title to be stored in the Domino Directory<br>
DomainName  	The Notes domain of the new server<br>
NetworkName  	(Optional).  The name of the network for the new server.   Do not pass in a literal constant.<br>
AdminName  	(Optional).  The name of the administrator for the new server.<br>
Password  		(Optional).  The password for the new server<br>
PasswordQuality	Quality of password required for this server (0 - 16)<br>
Flags  		Flags that are set to specify options.  See Symbolic Value, fREGxxx, in this reference.  Note that registration flags pertaining to the creation of a mail file  (fREGCreateMailFileNow 			and fRegCreateMailFileLocally) are not applicable to this function.<br>
Hostname		(Optional).  The hostname of this server for SSL purposes.  Required when setting up server SSL<br>
hInternetCertCtx	(Optional).  The internet certifier context for SSL purposes.  Required when setting up server SSL<br>
KeyringFileName	(Optional).  The filename of the keyring created for SSL purposes.  <br>
KeyringPassword	(Optional).  The password of the keyring file created for SSL purposes.  Required when setting up server SSL.<br>
IDInfo		(Optional).  Pointer to a structure of REG_ID_INFO<br>
MiscInfo		(Optional).  Pointer to a structure of REG_MISC_INFO<br>
Reserved		Reserved - must be 0<br>
pReserved		Reserved - must be NULL</ul>



**See Also :**
[fREGxxx](/domino-c-api-docs/reference/Symb/fREGxxx)
[REGNewServerExtended2](/domino-c-api-docs/reference/Func/REGNewServerExtended2)
[REG_ID_INFO](/domino-c-api-docs/reference/Data/REG_ID_INFO)
[REG_MISC_INFO](/domino-c-api-docs/reference/Data/REG_MISC_INFO)
---
