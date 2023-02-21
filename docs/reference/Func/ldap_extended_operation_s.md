##### Function : LDAP
##### ldap_extended_operation_s - Allow sychronous extended LDAP operations to be passed to the server.
---
```
#include <ldap.h>
int LNPUBLIC ldap_extended_operation_s(

	LDAP *ld,
	const char *exoid,
	const struct berval *exdata,
	LDAPControl **serverctrls,
	LDAPControl **clientctrls,
	char **retoidp,
	struct berval **retdatap);
```
**Description :**

This function will allow sychronous extended LDAP operations to be passed to 
the server, providing a general protocol extensibility mechanism.

Implemented as a macro:

#define ldap_extended_operation_s(ld, exoid, exdata, serverctrls, clientctrls, 
retoidp, retdatap) \
         ND_ldap_extended_operation_s((ld), (exoid), (exdata), (serverctrls), 
(clientctrls), (retoidp), (retdatap))

**Parameters :**
Input :
ld  -  The LDAP session handle.

exoid  -  The dotted-OID text string naming the request.

exdata  -  The arbitrary data needed by the operation (if NULL, no data is sent to the server).

serverctrls  -  Pointer to a list of LDAP server controls.  NULL if no server controls are to be used.

clientctrls  -  Pointer to a list of LDAP client controls.  NULL if no server controls are to be used.

Output :
(routine)  -  LDAP_SUCCESS  - If the request was successfully sent, or another LDAP result code if not.


retoidp  -  Pointer to a character string that will be set to an allocated, dotted-OID text string returned by the server.  This string SHOULD be disposed of using the ldap_memfree function.  If an API error occurs or no OID is returned by the server, *retoidp is set to NULL.

retdatap  -  Pointer to a berval structure pointer that will be set to an allocated copy of the data returned by the server.  This struct berval SHOULD be disposed of using ber_bvfree.  If an API error occurs or no data is returned by the server, *retdatap is set to NULL.


**See Also :**
[ber_bvfree](/domino-c-api-docs/reference/Func/ber_bvfree)
[ldap_memfree](/domino-c-api-docs/reference/Func/ldap_memfree)
---
