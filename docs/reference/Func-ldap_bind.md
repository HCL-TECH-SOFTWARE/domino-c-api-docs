##### Function : LDAP
##### ldap_bind - Initiate an asynchronous bind operation
---
##### #include <ldap.h>
int LNPUBLIC **ldap_bind(**

	LDAP *ld,
	const char *who,
	const char *passwd,
	int  authmethod);
**Description :**
This function initiates an asynchronous bind operation to bind to the ldap 
server.

Implemented as a macro:

#define ldap_bind(ld, who, passwd, authmethod) ND_ldap_bind((ld), (who), 
(passwd), (authmethod))
**Parameters :**
Input :
ld  -  The LDAP session handle.

who  -  The distinguished name of the entry to bind as.

passwd  -  Password of the entry to which to bind, depending on authentication method.

authmethod  -  Authentication method.  See LDAP_AUTH_xxx.

Output :
(routine)  -  Message ID - This ID can be used in subsequent calls to ldap_result to obtain the result(s) of the operation.

-1 - If an error occurs.


**Sample Usage :**
```
ldap_bind( ld, "cn=manager, o=university of michigan, c=us", "secret", 
LDAP_AUTH_SIMPLE )
```
**See Also :**
[ldap_bind_s](D:/md_files/ldap_bind_s.md)
---
