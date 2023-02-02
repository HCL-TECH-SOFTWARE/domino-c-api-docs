##### Function : LDAP
##### ldap_extended_operation - Allow asychronous extended LDAP operations to be passed to the server.
---
##### #include <ldap.h>
int LNPUBLIC **ldap_extended_operation(**

	LDAP *ld,
	const char *exoid,
	const struct berval *exdata,
	LDAPControl **serverctrls,
	LDAPControl **clientctrls,
	int *msgidp);
**Description :**
This function will allow asychronous extended LDAP operations to be passed to 
the server, providing a general protocol extensibility mechanism.

Implemented as a macro:

#define ldap_extended_operation(ld, exoid, exdata, serverctrls, clientctrls, 
msgidp) \
         ND_ldap_extended_operation((ld), (exoid), (exdata), (serverctrls), 
(clientctrls), (msgidp)) 
**Parameters :**
Input :
ld  -  The LDAP session handle.

exoid  -  The dotted-OID text string naming the request.

exdata  -  The arbitrary data needed by the operation (if NULL, no data is sent to the server).

serverctrls  -  Pointer to a list of LDAP server controls. NULL if no server controls are to be used.

clientctrls  -  Pointer to a list of LDAP client controls.  NULL if no server controls are to be used.

Output :
(routine)  -  LDAP_SUCCESS  - If the request was successfully sent, or another LDAP result code if not.


msgidp  -  Pointer to the message id of the request if the ldap_extended_operation call succeeds. The value is undefined if a value other than LDAP_SUCCESS is returned.   This ID can be used in subsequent calls to ldap_result to obtain the result(s) of the operation.

**See Also :**
[](D:/md_files/.md)
---
