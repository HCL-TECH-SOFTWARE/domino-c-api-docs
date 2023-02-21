##### Function : LDAP
##### ldap_sasl_bind_s - Initiate a synchronous SASL bind operation
---
```
#include <ldap.h>
int LNPUBLIC ldap_sasl_bind_s(

	LDAP *ld,
	const char *who,
	const char *mechanism,
	struct berval *cred,
	LDAPControl **serverctrls,
	LDAPControl **clientctrls,
	struct berval **servercredp);
```
**Description :**

This function initiates a synchronous bind operation to bind to the ldap 
server  using SASL authentication.

Implemented as a macro:

#define ldap_sasl_bind_s(ld, who, mechanism, cred, serverctrls, clientctrls, 
servercredp) \ 
         ND_ldap_sasl_bind_s((ld), (who), (mechanism), (cred), (serverctrls), 
(clientctrls), (servercredp))

**Parameters :**
Input :
ld  -  The LDAP session handle.

who  -  The distinguished name of the entry to bind as.

mechanism  -  The method to use for authentication.  Either LDAP_SASL_SIMPLE (NULL) to get simple authentication, or a text string identifying the SASL method.  See LDAP_SASL_xxx.

cred  -  The credentials with which to authenticate. Arbitrary credentials can be passed using this parameter. The format and content of the credentials depends on the setting of the mechanism parameter.  If the cred parameter is NULL and the mechanism is LDAP_SASL_SIMPLE, a zero-length octet string is sent to the server in the simple credentials field of the bind request.  If the cred parameter is NULL and the mechanism is anything else, no credentials are sent to the server in the bind request.

serverctrls  -  Pointer to a list of LDAP server controls.  NULL if no server controls are to be used.

clientctrls  -  Pointer to a list of LDAP client controls.  NULL if no client controls are to be used.

Output :
(routine)  -  LDAP_SUCCESS  - If the request was successfully sent, or another LDAP result code if not.


servercredp  -  Points to the credentials passed back by the server for mutual authentication. The berval structure must be freed by calling the ber_bvfree function. To ignore this parameter, set it to NULL. 


**See Also :**
[ldap_sasl_bind_s](/domino-c-api-docs/reference/Func/ldap_sasl_bind_s)
[LDAP_SASL_xxx](/domino-c-api-docs/reference/Symb/LDAP_SASL_xxx)
---
