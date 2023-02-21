##### Function : LDAP
##### ldap_add - Initiate an asynchronous ldap add operation.
---
```
#include <ldap.h>
int LNPUBLIC ldap_add(

	LDAP *ld,
	const char *dn,
	LDAPMod **attrs);
```
**Description :**

This function will initiate an asynchronous ldap add operation.

Note that the parent of the entry being added must already exist or the parent 
must be empty (i.e., equal to the root DN) for an add to succeed.

Implemented as a macro:

#define ldap_add(ld, dn, attrs) ND_ldap_add((ld), (dn), (attrs))

**Parameters :**
Input :
ld  -  The LDAP session handle.

dn  -  The distinguished name of the entry to add.  If NULL, a zero length DN is sent to the server.

attrs  -  The entry's attributes, specified using the LDAPMod structure defined for ldap_modify. The mod_type and mod_vals fields MUST be filled in.  The mod_op field is ignored unless ORed with the constant LDAP_MOD_BVALUES, used to select the mod_bvalues case of the mod_vals union. (See: ldap_modify, mod_xxx; LDAP_MOD_xxx)

Output :
(routine)  -  Message ID - This ID can be used in subsequent calls to ldap_result to obtain the result(s) of the operation.

-1 - If an error occurs.



**Sample Usage :**
```
LDAPMod *attrs[] = { 
                       { 0, "cn", { "babs jensen", "babs", 0 } },
                       { 0, "sn", { "jensen", 0 } },
                       { 0, "objectClass", { "person", 0 } },
                       0
                    }

msgid = ldap_add( ld, dn, attrs );
```
**See Also :**
[ldap_modify](/domino-c-api-docs/reference/Func/ldap_modify)
[LDAP_MOD_xxx](/domino-c-api-docs/reference/Symb/LDAP_MOD_xxx)
[mod_xxx](/domino-c-api-docs/reference/Symb/mod_xxx)
---
