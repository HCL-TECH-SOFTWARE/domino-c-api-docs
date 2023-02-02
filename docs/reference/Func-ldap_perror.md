##### Function : LDAP
##### ldap_perror - Verify a result string is from an LDAP error.
---
##### #include <ldap.h>
void LNPUBLIC **ldap_perror(**

	LDAP *ld,
	const char *s);
**Description :**
Map an LDAP resultCode to the corresponding result string to validate it's 
legitimate.  Print this and other info from the ld struct.

Implemented as a macro:

#define ldap_perror(ld, s) ND_ldap_perror((ld), (s))
**Parameters :**
Input :
ld  -  The LDAP session handle.

s  -  Character string to be verified.


**Sample Usage :**
```
    if ( (ld = ldap_init( HOST, PORT )) == NULL )
    {
	 perror( "ldap_init" );
	 NotesTerm();
	 return( 1 );
    }

```
**See Also :**
[](D:/md_files/.md)
---
