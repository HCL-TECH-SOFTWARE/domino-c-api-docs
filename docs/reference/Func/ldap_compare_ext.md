##### Function : LDAP
##### ldap_compare_ext - Asynchronous compare attribute value assertion with controls.
---
```
#include <ldap.h>
int LNPUBLIC ldap_compare_ext(

	LDAP *ld,
	const char *dn,
	const char *attr,
	const struct berval *bvalue,
	LDAPControl **sctrls,
	LDAPControl **cctrls,
	int *msgidp);
```
**Description :**

This function will do an asynchronous compare attribute value assertion, with 
controls, against an LDAP entry.

Implemented as a macro:

#define ldap_compare_ext(ld, dn, attr, bvalue, sctrls, cctrls, msgidp)\
          ND_ldap_ompare_ext((ld), (dn), (attr), (bvalue), (sctrls), (cctrls), 
(msgidp))

**Parameters :**
Input :
ld  -  The LDAP session handle.

dn  -  The distinguished name of the entry to compare against.

attr  -  The attribute to compare against.

bvalue  -  The attribute value to compare against those found in the given entry. This is a pointer to a struct berval so it is possible to compare binary values.

sctrls  -  Pointer to a list of LDAP server controls.  NULL if no server controls are to be used.

cctrls  -  Pointer to a list of LDAP client controls.  NULL if no client controls are to be used.

Output :
(routine)  -  LDAP_SUCCESS  - If the request was successfully sent, or another LDAP result code if not.


msgidp  -  Pointer to the message id of the request if the ldap_compare_ext call succeeds. The value is undefined if a value other than LDAP_SUCCESS is returned.   This ID can be used in subsequent calls to ldap_result to obtain the result(s) of the operation.


**Sample Usage :**
```
struct berval bvalue = { "secret", strlen("secret") };
rc = ldap_compare_ext( ld, "CN = John Q Public, O = API", "userPassword", 
&bvalue, sctrl, cctrl, &msgid );
```
**See Also :**
---
