##### Function : LDAP
##### ldap_get_values - Retrieve the values of a given attribute.
---
```
#include <ldap.h>
char **LNPUBLIC ldap_get_values(

	LDAP *ld,
	LDAPMessage *entry,
	const char *target);
```
**Description :**

This function is used to retrieve the values of a given attribute from an entry 
and is only suitable for use with non-binary character string data.

Note that the values returned are dynamically allocated and SHOULD be freed by 
calling ldap_value_free when no longer in use.

Implemented as a macro:

#define ldap_get_values(ld, entry, target) ND_ldap_get_values((ld), (entry), 
(target))

**Parameters :**
Input :
ld  -  The LDAP session handle.

entry  -  The entry from which to retrieve values, as returned by ldap_first_entry or ldap_next_entry.

target  -  The attribute whose values are to be retrieved, as returned by ldap_first_attribute or ldap_next_attribute, or a caller supplied string (e.g., "mail").

Output :
(routine)  -  A pointer to an allocated buffer containing the given attribute values.

NULL - If no values are found or if an error occurs.



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
[ldap_count_values](/domino-c-api-docs/reference/Func/ldap_count_values)
[ldap_count_values_len](/domino-c-api-docs/reference/Func/ldap_count_values_len)
[ldap_first_attribute](/domino-c-api-docs/reference/Func/ldap_first_attribute)
[ldap_first_entry](/domino-c-api-docs/reference/Func/ldap_first_entry)
[ldap_get_values_len](/domino-c-api-docs/reference/Func/ldap_get_values_len)
[ldap_next_attribute](/domino-c-api-docs/reference/Func/ldap_next_attribute)
[ldap_next_entry](/domino-c-api-docs/reference/Func/ldap_next_entry)
[ldap_value_free](/domino-c-api-docs/reference/Func/ldap_value_free)
[ldap_value_free_len](/domino-c-api-docs/reference/Func/ldap_value_free_len)
---
