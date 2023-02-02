##### Function : LDAP
##### ldap_add_ext_s - Initiate a synchronous ldap add operation with controls.
---
##### #include <ldap.h>
int LNPUBLIC **ldap_add_ext_s(**

	LDAP *ld,
	const char *dn,
	LDAPMod **attrs,
	LDAPControl **serverctrls,
	LDAPControl **clientctrls);
**Description :**
This function will initiate a synchronous ldap add operation with controls.

Note that the parent of the entry being added must already exist or the parent 
must be empty (i.e., equal to the root DN) for an add to succeed.

Implemented as a macro:

#define ldap_add_ext_s(ld, dn, attrs, serverctrls, clientctrls)\
	        ND_ldap_add_ext_s((ld), (dn), (attrs), (serverctrls), 
(clientctrls))
**Parameters :**
Input :
ld  -  The LDAP session handle.

dn  -  The distinguished name of the entry to add.  If NULL, a zero length DN is sent to the server.

attrs  -  The entry's attributes, specified using the LDAPMod structure defined for ldap_modify. The mod_type and mod_vals fields MUST be filled in.  The mod_op field is ignored unless ORed with the constant LDAP_MOD_BVALUES, used to select the mod_bvalues case of the mod_vals union. (See: ldap_modify, mod_xxx; LDAP_MOD_xxx)

serverctrls  -  Pointer to a list of LDAP server controls.  NULL if no server controls are to be used.

clientctrls  -  Pointer to a list of LDAP client controls.  NULL if no client controls are to be used.

Output :
(routine)  -  LDAP_SUCCESS  - If the request was successfully sent, or another LDAP result code if not.


**See Also :**
[ldap_modify](D:/md_files/ldap_modify.md)
[LDAP_MOD_xxx](D:/md_files/LDAP_MOD_xxx.md)
[LDAP_OPT_xxx](D:/md_files/LDAP_OPT_xxx.md)
[mod_xxx](D:/md_files/mod_xxx.md)
---
