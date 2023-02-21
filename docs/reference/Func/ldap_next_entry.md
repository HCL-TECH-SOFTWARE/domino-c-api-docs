##### Function : LDAP
##### ldap_next_entry - Retrieve the next entry from a search result chain.
---
```
#include <ldap.h>
LDAPMessage *LNPUBLIC ldap_next_entry(

	LDAP *ld,
	LDAPMessage *entry);
```
**Description :**

This function is used to step through and retrieve the list of entries from a 
search result chain.

Implemented as a macro:

#define ldap_next_entry(ld, entry) ND_ldap_next_entry((ld), (entry))

**Parameters :**
Input :
ld  -  The LDAP session handle.

entry  -  The entry returned by a previous call to ldap_first_entry or ldap_next_entry.

Output :
(routine)  -  Pointer to the next entry in a chain of entries.

NULL  - When no more entries or references exist in the result set to be returned or if an error occurs while stepping through the entries or references, in which case the error parameters in the session handle ld will be set to indicate the error.



**Sample Usage :**
```
    for ( e = ldap_first_entry( ld, result ); e != NULL;
          e = ldap_next_entry( ld, e ) )
    {
         if ( (sdn = ldap_get_dn( ld, e )) != NULL )
         {
             printf( "\tdn: %s\n", sdn );
             ldap_memfree( sdn );
         }
         for ( a = ldap_first_attribute( ld, e, &ber );
               a != NULL; a = ldap_next_attribute( ld, e, ber ) )
         {
             if ((vals = ldap_get_values( ld, e, a)) != NULL )
             {
                 for ( j = 0; vals[j] != NULL; j++ )
                 {
                     printf( "\t%s: %s\n", a, vals[j] );
                 }
                 ldap_value_free( vals );
             }
             ldap_memfree(a);
         }
         ber_free(ber, 0);
    }
    ldap_msgfree( result );

```
**See Also :**
[ldap_count_entries](/domino-c-api-docs/reference/Func/ldap_count_entries)
[ldap_first_entry](/domino-c-api-docs/reference/Func/ldap_first_entry)
[ldap_result](/domino-c-api-docs/reference/Func/ldap_result)
---
