##### Data Type : User Registration
##### REG_SERVER_INFO - Structure that defines server registration information.
---
```
#include <reg.h>
```
**Description :**

This structure defines server registration information for the 
REGNewServerExtended2 function.  The entire structure must
be initialized to zero.

The fields in the structure are (all fields that are not used must be NULL/O):

Size  Size of this structure - must be initialized with sizeof (REG_SERVER_INFO)
Name  The name of the new server
OrgUnit    (Optional).  Organizational unit of the new server (hierarchical 
only and in addition to that derived from the certifier context).
ServerTitle   (Optional).  The server title to be stored in the Domino Directory
DomainName   The Notes domain of the new server
NetworkName   (Optional).  The name of the network for the new server.   Do not 
pass in a literal constant.
AdminName   (Optional).  The name of the administrator for the new server.
Password    (Optional).  The password for the new server
PasswordQuality Quality of password required for this server (0 - 16)
Flags    Flags that are set to specify options.  See Symbolic Value, fREGxxx, 
in this reference.  Note that registration flags pertaining to the creation of 
a mail file  (fREGCreateMailFileNow    and fRegCreateMailFileLocally) are not 
applicable to this function.
Hostname  (Optional).  The hostname of this server for SSL purposes.  Required 
when setting up server SSL
hInternetCertCtx (Optional).  The internet certifier context for SSL purposes.  
Required when setting up server SSL
KeyringFileName (Optional).  The filename of the keyring created for SSL 
purposes.  
KeyringPassword (Optional).  The password of the keyring file created for SSL 
purposes.  Required when setting up server SSL.
IDInfo  (Optional).  Pointer to a structure of REG_ID_INFO
MiscInfo  (Optional).  Pointer to a structure of REG_MISC_INFO
Reserved  Reserved - must be 0
pReserved  Reserved - must be NULL


**See Also :**
[fREGxxx](/domino-c-api-docs/reference/Symb/fREGxxx)
[REGNewServerExtended2](/domino-c-api-docs/reference/Func/REGNewServerExtended2)
[REG_ID_INFO](/domino-c-api-docs/reference/Data/REG_ID_INFO)
[REG_MISC_INFO](/domino-c-api-docs/reference/Data/REG_MISC_INFO)
---
