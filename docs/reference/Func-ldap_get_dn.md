##### Function : LDAP
##### ldap_get_dn - Retrieve the name of an entry.
---
##### #include <ldap.h>
char *LNPUBLIC **ldap_get_dn(**

	LDAP *ld,
	LDAPMessage *entry);
**Description :**
This function is used to retrieve the distinguished name of an entry.

Implemented as a macro:

#define ldap_get_dn(ld, entry) ND_ldap_get_dn((ld), (entry))
**Parameters :**
Input :
ld  -  The LDAP session handle.

entry  -  The entry whose name is to be retrieved, as returned by ldap_first_entry or ldap_next_entry.

Output :
(routine)  -  A pointer to newly allocated space containg the DN.  The caller SHOULD free this space by calling ldap_memfree when it is no longer in use.  Note the root DN is returned as a zero length string ("").

NULL - If there is some error parsing the dn, setting error parameters in the session handle ld to indicate the error.


**Sample Usage :**
```
      if ( (sdn = ldap_get_dn( ld, e )) != NULL )
      {
          printf( "\tdn: %s\n", sdn );
          ldap_memfree( sdn );
      }

```
**See Also :**
[ldap_dn2ufn](D:/md_files/ldap_dn2ufn.md)
[ldap_explode_dn](D:/md_files/ldap_explode_dn.md)
[ldap_explode_rdn](D:/md_files/ldap_explode_rdn.md)
[ldap_first_entry](D:/md_files/ldap_first_entry.md)
[ldap_next_entry](D:/md_files/ldap_next_entry.md)
---
