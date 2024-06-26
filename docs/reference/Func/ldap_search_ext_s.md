##### Function : LDAP
##### ldap_search_ext_s - Synchronous search of the LDAP directory with controls.
---
```
#include <ldap.h>
int LNPUBLIC ldap_search_ext_s(

	LDAP *ld,
	const char *base,
	int  scope,
	const char *filter,
	char **attrs,
	int  attrsonly,
	LDAPControl **serverctrls,
	LDAPControl **clientctrls,
	timeval  *timeout,
	int  sizelimit,
	LDAPMessage **res);
```
**Description :**

This function performs a synchronous search, with controls, of the LDAP 
directory and returns a requested set of attributes for each entry matched.

Implemented as a macro:

#define ldap_search_ext_s(ld, base, scope, filter, attrs, attrsonly, 
serverctrls, clientctrls, timeoutp, sizelimit, res) \ 
         ND_ldap_search_ext_s((ld), (base), (scope), (filter), (attrs), 
(attrsonly), (serverctrls), (clientctrls), (timeoutp), (sizelimit), (res))

**Parameters :**
Input :
ld  -  The LDAP session handle.

base  -  The distinguished name of the entry at which to start the search.

scope  -  The search scope.  See LDAP_SCOPE_xxx.

filter  -  A character string representing the search filter (e.g. "( |(cn=bob)(sn=bob))" ).  NULL can be passed to represent the filter "(objectclass=*)" which will match all entries.

attrs  -  A NULL-terminated array of strings indicating which attributes to return for each matching entry.  Passing NULL for this parameter causes all available user attributes to be retrieved.  See LDAP_xxx_ATTRS for additional attribute return requests.

attrsonly  -  A boolean value that MUST be zero if both attribute types and values are to be returned, and non-zero if only types are wanted.

serverctrls  -  Pointer to a list of LDAP server controls.  NULL if no server controls are to be used.

clientctrls  -  Pointer to a list of LDAP client controls.  NULL if no client controls are to be used.

*timeout  -  Specifies both the local search timeout value and the operation time limit that is sent to the server within the search request.  Passing a NULL value for timeout causes the default timeout stored in the LDAP session handle (set by using ldap_set_option() with the LDAP_OPT_TIMELIMIT parameter) to be sent to the server with the request but an infinite local search timeout to be used.  If a zero timeout (where tv_sec and tv_usec are both zero - see timeval) is passed in, API implementations SHOULD return LDAP_PARAM_ERROR.  If a zero value for tv_sec is used but tv_usec is non-zero, an operation time limit of 1 SHOULD be passed to the LDAP server as the operation time limit.  For other values of tv_sec, the tv_sec value itself SHOULD be passed to the LDAP server.

sizelimit  -  A limit on the number of entries to return from the search.  A value of LDAP_NO_LIMIT means no limit.

Output :
(routine)  -  LDAP_SUCCESS  - If the request was successfully sent, or another LDAP result code if not.


res  -  The results of the search upon completion of the call.  The results opaque to the caller.  Entries, attributes, values, etc., can be extracted by calling the parsing routines. The results contained in res SHOULD be freed when no longer in use by calling ldap_msgfree.  

If an API error occurs or no results are returned, *res is set to NULL.


**See Also :**
[LDAP_NO_LIMIT](/domino-c-api-docs/reference/Symb/LDAP_NO_LIMIT)
[LDAP_OPT_xxx](/domino-c-api-docs/reference/Symb/LDAP_OPT_xxx)
[LDAP_SCOPE_xxx](/domino-c-api-docs/reference/Symb/LDAP_SCOPE_xxx)
[LDAP_xxx_ATTRS](/domino-c-api-docs/reference/Symb/LDAP_xxx_ATTRS)
---
