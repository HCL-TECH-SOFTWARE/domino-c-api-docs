##### Function : LDAP
##### ldap_modrdn2_s - Initiate a synchronous ldap modify RDN operation.
---
##### #include <ldap.h>
int LNPUBLIC **ldap_modrdn2_s(**

	LDAP *ld,
	const char *dn,
	const char *newrdn,
	int  deleteoldrdn);
**Description :**
This function initiates a synchronous modify RDN operation.

Implemented as a macro:

#define ldap_modrdn2_s(ld, dn, newrdn, deleteoldrdn)\
	        ND_ldap_modrdn2_s((ld), (dn), (newrdn), (deleteoldrdn))
**Parameters :**
Input :
ld  -  The LDAP session handle.

dn  -  The name of the entry whose RDN is to be changed.  If NULL, a zero length DN is sent to the server.

newrdn  -  The new RDN to give the entry.

deleteoldrdn  -  Boolean value: non-zero indicates that the old RDN value(s) is to be removed, zero indicates that the old RDN value(s) is to be retained as non-distinguished values of the entry.

Output :
(routine)  -  LDAP_SUCCESS  - If the request was successfully sent, or another LDAP result code if not.


**Sample Usage :**
```
    if ( ldap_modrdn2_s( ld, dn, nrdn, 0 ) != LDAP_SUCCESS )
    {
         ldap_perror( ld, "ldap_modrdn2_s" );
         NotesTerm();
         return( 1 );
    }
```
**See Also :**
[](D:/md_files/.md)
---
