##### Function : LDAP
##### ldap_simple_bind - Initiate an asynchronous simple bind operation
---
##### #include <ldap.h>
int LNPUBLIC **ldap_simple_bind(**

	LDAP *ld,
	const char *who,
	const char *credentials);
**Description :**
This function initiates an asynchronous bind operation to bind to the ldap 
server using simple authentication.

Implemented as a macro:

#define ldap_simple_bind(ld, who, passwd)  ND_ldap_simple_bind((ld), (who), 
(passwd))
**Parameters :**
Input :
ld  -  The LDAP session handle.

who  -  The distinguished name of the entry to bind as.

credentials  -  Password of the entry to which to bind.

Output :
(routine)  -  Message ID - This ID can be used in subsequent calls to ldap_result to obtain the result(s) of the operation.

-1 - If an error occurs.


**Sample Usage :**
```
ldap_simple_bind( ld, "cn=manager, o=university of michigan, c=us", 
"ManagerPassword" )
```
**See Also :**
[ldap_simple_bind_s](D:/md_files/ldap_simple_bind_s.md)
---
