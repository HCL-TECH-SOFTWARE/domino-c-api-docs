##### Data Type : User Registration
##### REG_ID_INFO - Structure that defines ID registration information.
---
```
#include <reg.h>
```

**Definition :**
```
typedef struct
	{
	DWORD Size;    /* size of this structure - must initialize with sizeof 
(REG_ID_INFO) */
	WORD Type;    /* see KFM_IDFILE_??? */
	WORD KeyWidth;   /* The only valid values are (see bsafe.h):
	      0 - default
	      KEYBITS_630 - Compatible with all releases
	      KEYBITS_1024 - Compatible with R6 and later
	      KEYBITS_2048 - Compatible with R7 and later
	     */
	WORD PasswordKeyWidth;  /* The only valid values are (see bsafe.h):
	      KEYBITS_0 - default (means 64 bits for KeyWidth < 1024 else 128 
bits)
	      KEYBITS_64 - 64 bits
	      KEYBITS_128 - 128 bits 
	     */
	char *FileName;
	DWORD Reserved[4];
	void *pReserved[4];
	} REG_ID_INFO;


```

**Description :**

<br>
This structure defines ID registration information for the REGNewPerson, REGNewCertifierExtended, and REGNewServerExtended2 functions.  The entire structure must<br>
be initialized to zero.<br>

<ul>The fields in the structure are (all fields that are not used must be NULL/O):<br>
<br>
Size			Size of this structure - must be initialized with sizeof (REG_ID_INFO)<br>
Type			See Symbolic Value KFM_IDFILE_TYPE_XXX, in this reference and base on the entity being registered <br>
KeyWidth			Key width in bits - valid values: <br>
					0 - default<br>
					630 - Compatible with all releases<br>
					1024 - Compatible with R6 and later<br>
PasswordKeyWidth		Encryption strength in bits:<br>
					0 - default<br>
					64<br>
					128<br>
FileName			The pathname of the new ID file. If the fREGCreateIDFileNow flag is not specified, then this file must exist. <br>
Reserved			Reserved - must be 0<br>
pReserved			Reserved - must be NULL</ul>



**See Also :**
[REGNewCertifierExtended](/domino-c-api-docs/reference/Func/REGNewCertifierExtended)
[REGNewPerson](/domino-c-api-docs/reference/Func/REGNewPerson)
[REGNewServerExtended2](/domino-c-api-docs/reference/Func/REGNewServerExtended2)
---
