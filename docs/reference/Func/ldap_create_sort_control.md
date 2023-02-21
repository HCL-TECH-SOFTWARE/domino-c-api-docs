##### Function : LDAP
##### ldap_create_sort_control - Create and encode the server-side sort control.
---
```
#include <ldap.h>
int LNPUBLIC ldap_create_sort_control(

	LDAP *ld,
	LDAPsortKey **keyList,
	char  isCritical,
	LDAPControl **ctrlp);
```
**Description :**

This function will  create and encode the server-side sort control.

Implemented as a macro:

#define ldap_create_sort_control(ld, keyList, isCritical, ctrlp)\
	        ND_ldap_create_sort_control((ld), (keyList), (isCritical), 
(ctrlp))

**Parameters :**
Input :
ld  -  The LDAP session handle.

keyList  -  Pointer to a NULL terminated array of pointers to LDAPsortKey structures.

isCritical  -  Zero indicates the control is not critical to the operation, and non-zero indicates the control is critical to the operation.

Output :
(routine)  -  LDAP_SUCCESS  - If the sort control was successfully created, or another LDAP result code if not.


ctrlp  -  Returns a pointer to the LDAPControl created.  This control SHOULD be freed by calling ldap_control_free when done.


**See Also :**
[ldap_control_free](/domino-c-api-docs/reference/Func/ldap_control_free)
---
