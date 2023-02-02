##### Function : LDAP
##### ldap_bind_s - Initiate a synchronous bind operation
---
##### #include <ldap.h>
int LNPUBLIC **ldap_bind_s(**

	LDAP *ld,
	const char *who,
	const char *passwd,
	int  authmethod);
**Description :**
This function initiates a synchronous bind operation to bind to the ldap server.

Implemented as a macro:

#define ldap_bind_s(ld, who, cred, method) ND_ldap_bind_s((ld), (who), (cred), 
(method))
**Parameters :**
Input :
ld  -  The LDAP session handle.

who  -  The distinguished name of the entry to bind as.

passwd  -  Password of the entry to which to bind, depending on authentication method.

authmethod  -  Authentication method.  See LDAP_AUTH_xxx.

Output :
(routine)  -  LDAP_SUCCESS  - If the request was successfully sent, or another LDAP result code if not.


**Sample Usage :**
```
ldap_bind_s( ld, "cn=manager, o=university of michigan, c=us", "secret", 
LDAP_AUTH_SIMPLE )
```
**See Also :**
[ldap_bind](D:/md_files/ldap_bind.md)
---
