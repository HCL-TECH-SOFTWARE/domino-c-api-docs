##### Function : LDAP
##### ldap_search_s - Synchronous search of the LDAP directory.
---
```
#include <ldap.h>
int LNPUBLIC ldap_search_s(

	LDAP *ld,
	const char *base,
	int  scope,
	const char *filter,
	char **attrs,
	int  attrsonly,
	LDAPMessage **res);
```
**Description :**

This function performs a synchronous search of the LDAP directory and returns a 
requested set of attributes for each entry matched.

Implemented as a macro:

#define ldap_search_s(ld, base, scope, filter, attrs, attrsonly, res) 
ND_ldap_search_s((ld), (base), (scope), (filter), (attrs), (attrsonly), (res))

**Parameters :**
Input :
ld  -  The LDAP session handle.

base  -  The distinguished name of the entry at which to start the search.

scope  -  The search scope.  See LDAP_SCOPE_xxx.

filter  -  A character string representing the search filter (e.g. "( |(cn=bob)(sn=bob))" ).  NULL can be passed to represent the filter "(objectclass=*)" which will match all entries.

attrs  -  A NULL-terminated array of strings indicating which attributes to return for each matching entry.  Passing NULL for this parameter causes all available user attributes to be retrieved.  See LDAP_xxx_ATTRS for additional attribute return requests.

attrsonly  -  A boolean value that MUST be zero if both attribute types and values are to be returned, and non-zero if only types are wanted.

Output :
(routine)  -  LDAP_SUCCESS  - If the request was successfully sent, or another LDAP result code if not.


res  -  The results of the search upon completion of the call.  The results opaque to the caller.  Entries, attributes, values, etc., can be extracted by calling the parsing routines. The results contained in res SHOULD be freed when no longer in use by calling ldap_msgfree.  

If an API error occurs or no results are returned, *res is set to NULL.


**Sample Usage :**
```
   
    /* Perform search */
    printf("\n  Search results:\n\n");

    if ( ldap_search_s( ld, SEARCHBASE, LDAP_SCOPE_SUBTREE,
                        FILTER, NULL, 0, &result ) != LDAP_SUCCESS )
    {
         ldap_perror( ld, "ldap_search_s" );
         if ( result == NULL )
         {
             ldap_unbind_s( ld );
             NotesTerm();
             return( 1 );
         }
    }

```
**See Also :**
[LDAP_SCOPE_xxx](/reference/Symb/LDAP_SCOPE_xxx)
[LDAP_xxx_ATTRS](/reference/Symb/LDAP_xxx_ATTRS)
---
