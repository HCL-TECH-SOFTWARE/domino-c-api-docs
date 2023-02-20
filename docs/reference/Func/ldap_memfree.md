##### Function : LDAP
##### ldap_memfree - Free allocated LDAP memory
---
```
#include <ldap.h>
void LNPUBLIC ldap_memfree(

	char *ptr);
```
**Description :**

This function frees the memory allocated by the LDAP library.

Implemented as a macro:

#define ldap_memfree(ptr) ND_ldap_memfree((ptr))

**Parameters :**
Input :
ptr  -  A pointer to memory allocated by the LDAP library, such as the   attribute type names returned by ldap_first_attribute and ldap_next_attribute, or the DN returned by ldap_get_dn.  If ptr is NULL, the ldap_memfree call does nothing.



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
[ldap_first_attribute](/reference/Func/ldap_first_attribute)
[ldap_get_dn](/reference/Func/ldap_get_dn)
[ldap_next_attribute](/reference/Func/ldap_next_attribute)
---
