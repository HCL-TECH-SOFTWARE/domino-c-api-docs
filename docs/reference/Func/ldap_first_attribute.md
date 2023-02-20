##### Function : LDAP
##### ldap_first_attribute - Get the first of the attribute types returned with an entry.
---
```
#include <ldap.h>
char *LNPUBLIC ldap_first_attribute(

	LDAP *ld,
	LDAPMessage *entry,
	BerElement **ber);
```
**Description :**

This function is used to get the first of the of attribute types returned with 
an entry.

Implemented as a macro:

#define ldap_first_attribute(ld, entry, ber) ND_ldap_first_attribute((ld), 
(entry), (ber))

**Parameters :**
Input :
ld  -  The LDAP session handle.

entry  -  The entry whose attributes are to be stepped through, as returned by ldap_first_entry or ldap_next_entry.

Output :
(routine)  -  A pointer to an allocated buffer containing the current attribute name. The attribute type names returned are suitable for passing in a call to ldap_get_values.  This SHOULD be freed when no longer in use by calling ldap_memfree.

NULL  - If the end of the attributes is reached, or if there is an error, in which case the error parameters in the session handle ld will be set to indicate the error.


ber  -  The address of a pointer used internally to keep track of the current position in the entry.   This pointer MAY be passed in subsequent calls to ldap_next_attribute to step through the entry's attributes.  

After a set of calls to ldap_first_attribute and ldap_next_attribute, if ptr is non-NULL, it SHOULD be freed by calling ber_free( ber, 0 ).  Note that it is very important to pass the second parameter as 0 (zero) in this call, since the buffer associated
with the BerElement does not point to separately allocated memory. See ber_free.


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
[BerElement](/reference/Data/BerElement)
[ber_free](/reference/Func/ber_free)
[ldap_memfree](/reference/Func/ldap_memfree)
[ldap_next_attribute](/reference/Func/ldap_next_attribute)
---
