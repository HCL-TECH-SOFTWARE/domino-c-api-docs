##### Function : LDAP
##### ldap_abandon_ext - Perform an LDAP abandon operation, with controls.
---
##### #include <ldap.h>
int LNPUBLIC **ldap_abandon_ext(**

	LDAP *ld,
	int  msgid,
	LDAPControl**serverctrls,
	LDAPControl**clientctrls);
**Description :**
This function will perform an LDAP abandon, with controls, of an operation in 
progress.

Implemented as a macro:

#define ldap_abandon_ext(ld, msgid, serverctrls, clientctrls)\
	        ND_ldap_abandon_ext((ld), (msgid), (serverctrls), 
(clientctrls))
**Parameters :**
Input :
ld  -  The LDAP session handle.

msgid  -  Message ID of the request to be abandoned.

serverctrls  -  Pointer to a list of LDAP server controls.  NULL if no server controls are to be used.

clientctrls  -  Pointer to a list of LDAP client controls.  NULL if no client controls are to be used.

Output :
(routine)  -  LDAP_SUCCESS  - If the request was successfully sent, or another LDAP result code if not.


**See Also :**
[](D:/md_files/.md)
---
