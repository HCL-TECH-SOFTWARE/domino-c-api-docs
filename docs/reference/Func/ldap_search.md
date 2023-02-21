##### Function : LDAP
##### ldap_search - Asynchronous search of the LDAP directory.
---
```
#include <ldap.h>
int LNPUBLIC ldap_search(

	LDAP *ld,
	const char *base,
	int  scope,
	const char *filter,
	char **attrs,
	int  attrsonly);
```
**Description :**

This function performs an asynchronous search of the LDAP directory and returns 
a requested set of attributes for each entry matched.

Implemented as a macro:

#define ldap_search(ld, base, scope, filter, attrs, attrsonly) 
ND_ldap_search((ld), (base), (scope), (filter), (attrs), (attrsonly))

**Parameters :**
Input :
ld  -  The LDAP session handle.

base  -  The distinguished name of the entry at which to start the search.

scope  -  The search scope.  See LDAP_SCOPE_xxx.

filter  -  A character string representing the search filter (e.g. "( |(cn=bob)(sn=bob))" ).  NULL can be passed to represent the filter "(objectclass=*)" which will match all entries.

attrs  -  A NULL-terminated array of strings indicating which attributes to return for each matching entry.  Passing NULL for this parameter causes all available user attributes to be retrieved.  See LDAP_xxx_ATTRS for additional attribute return requests.

attrsonly  -  A boolean value that MUST be zero if both attribute types and values are to be returned, and non-zero if only types are wanted.

Output :
(routine)  -  Message ID - This ID can be used in subsequent calls to ldap_result to obtain the result(s) of the operation.

-1 - If an error occurs.



**Sample Usage :**
```
char *attrs[] = { "mail", "title", 0 };
msgid = ldap_search( ld, "c=us@o=UM", LDAP_SCOPE_SUBTREE, "cn~=bob", attrs, 
attrsonly );
```
**See Also :**
[LDAP_SCOPE_xxx](/domino-c-api-docs/reference/Symb/LDAP_SCOPE_xxx)
[LDAP_xxx_ATTRS](/domino-c-api-docs/reference/Symb/LDAP_xxx_ATTRS)
---
