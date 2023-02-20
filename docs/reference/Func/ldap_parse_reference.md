##### Function : LDAP
##### ldap_parse_reference - Extract referrals and controls.
---
```
#include <ldap.h>
int LNPUBLIC ldap_parse_reference(

	LDAP *ld,
	LDAPMessage *ref,
	char ***referralsp,
	LDAPControl ***serverctrls,
	int  freeit);
```
**Description :**

This function is used to extract referrals and controls from a 
SearchResultReference message.

Implemented as a macro:

#define ldap_parse_reference(ld, ref, referralsp, serverctrls, freeit)\
	        ND_ldap_parse_reference((ld), (ref), (referralsp), 
(serverctrls), (freeit))

**Parameters :**
Input :
ld  -  The LDAP session handle.

ref  -  The reference to parse, as returned by ldap_result, ldap_first_reference, or ldap_next_reference.

freeit  -  A boolean that determines whether the ref parameter is disposed of or not.  Any non-zero value will free ref after extracting the requested information.  A zero will not free ref and ldap_msgfree can be used to free the result later.

Output :
(routine)  -  LDAP_SUCCESS  - If the reference was successfully parsed, or another LDAP result code if the value of the referrals and controls are undefined.


referralsp  -  An allocated array of character strings.  The elements of the array are  the referrals (typically LDAP URLs).  The array SHOULD be freed when no longer in used by calling ldap_value_free.  NULL, if the referral URLs are not returned.

serverctrls  -  An allocated array of controls copied out of the entry. The control array  SHOULD be freed by calling ldap_controls_free.  NULL, if no controls were returned.


**See Also :**
[ldap_controls_free](/reference/Func/ldap_controls_free)
[ldap_first_reference](/reference/Func/ldap_first_reference)
[ldap_msgfree](/reference/Func/ldap_msgfree)
[ldap_next_reference](/reference/Func/ldap_next_reference)
[ldap_result](/reference/Func/ldap_result)
[ldap_value_free](/reference/Func/ldap_value_free)
---
