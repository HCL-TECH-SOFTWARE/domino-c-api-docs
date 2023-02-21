##### Function : LDAP
##### ldap_value_free - Free the values retreived by ldap_get_values.
---
```
#include <ldap.h>
void LNPUBLIC ldap_value_free(

	char **vals);
```
**Description :**

This function is used to free the values retrieved by ldap_get_values.

Implemented as a macro:

#define ldap_value_free(vals) ND_ldap_value_free((vals))

**Parameters :**
Input :
vals  -  The values returned by a previous call to ldap_get_values.  If a NULL is passed, nothing is done.



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
[ldap_get_values](/domino-c-api-docs/reference/Func/ldap_get_values)
---
