##### Function : LDAP
##### ldap_simple_bind_s - Initiate a synchronous simple bind operation
---
```
#include <ldap.h>
int LNPUBLIC ldap_simple_bind_s(

	LDAP *ld,
	const char *who,
	const char *credentials);
```
**Description :**

This function initiates a synchronous bind operation to bind to the ldap server 
using simple authentication.

Implemented as a macro:

#define ldap_simple_bind_s(ld, who, passwd)  ND_ldap_simple_bind_s((ld), (who), 
(passwd))

**Parameters :**
Input :
ld  -  The LDAP session handle.

who  -  The distinguished name of the entry to bind as.

credentials  -  Password of the entry to which to bind.

Output :
(routine)  -  LDAP_SUCCESS  - If the request was successfully sent, or another LDAP result code if not.



**Sample Usage :**
```
    if ( ldap_simple_bind_s( ld, DN, PASSWORD ) != LDAP_SUCCESS )
    {
	ldap_perror( ld, "ldap_simple_bind_s" );
	NotesTerm();
	return( 1 );
    }
```
**See Also :**
[ldap_simple_bind](/domino-c-api-docs/reference/Func/ldap_simple_bind)
---
