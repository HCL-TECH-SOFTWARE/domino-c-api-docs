##### Function : LDAP
##### ldap_modify_ext_s - Synchronously modify an existing LDAP entry with controls.
---
##### #include <ldap.h>
int LNPUBLIC **ldap_modify_ext_s(**

	LDAP *ld,
	const char *dn,
	LDAPMod **mods,
	LDAPControl **serverctrls,
	LDAPControl **clientctrls);
**Description :**
This function initiates a synchronous modify operation with controls.

Implemented as a macro:

#define ldap_modify_ext_s(ld, dn, mods, serverctrls, clientctrls) \
	        ND_ldap_modify_ext_s((ld), (dn), (mods), (serverctrls), 
(clientctrls))
**Parameters :**
Input :
ld  -  The LDAP session handle.

dn  -  The distinguished name of the entry to modify.  If NULL, a zero length DN is sent to the server.

mods  -  List of modifications to make.  This is null-terminated array of struct ldapmod's, specifying the modifications to perform.

serverctrls  -  Pointer to a list of LDAP server controls.  NULL if no server controls are to be used.

clientctrls  -  Pointer to a list of LDAP client controls.  NULL if no client controls are to be used.

Output :
(routine)  -  LDAP_SUCCESS  - If the operation was successful, or another LDAP result code if not.


**See Also :**
[LDAPMod](D:/md_files/LDAPMod.md)
[LDAP_OPT_xxx](D:/md_files/LDAP_OPT_xxx.md)
---
