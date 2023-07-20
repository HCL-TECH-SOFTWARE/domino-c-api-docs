##### Data Type : LDAP
##### LDAPControl - Structure for holding ldapv3 controls.
---
```
#include <ldap.h>
```

**Definition :**
```
typedef struct ldapcontrol {
	char            *ldctl_oid;
	struct berval   ldctl_value;
	char            ldctl_iscritical;
}  LDAPControl;


```

**Description :**

LDAPv3 operations can be extended through the use of controls.  Controls can be sent to a server or returned to the client with any LDAP message. These controls are referred to as server controls.
<ul><br>
<br>
The LDAP API also supports a client-side extension mechanism through the use of client controls. These controls affect the behavior of the LDAP API only and are never sent to a server.  The LDAPControl data structure is used to represent both types of controls<br>
<br>
The fields in the LDAPControl structure are:<br>
<br>
ldctl_oid		- The control type, represented as a string.  See LDAP_CONTROL_xxx.<br>
<br>
ldctl_value		- The data associated with the control (if any).  To  specify a zero-length value, set ldctl_value.bv_len to zero and ldctl_value.bv_val to a zero-length string.  To indicate that no data is associated with the con trol, set ldctl_value.bv_val to NULL.  Alternatively, when the ldctl_oid is set to LDAP_CONTROL_REFERRALS, the flags value can be set to the value LDAP_CHASE_SUBORDINATE_REFERRALS or to the value LDAP_CHASE_EXTERNAL_REFERRALS, or the logical OR of the two flag values.  To create a referrals client control with &quot;automatic chasing&quot;.  See LDAP_CHASE_xxx.<br>
<br>
ldctl_iscritical	- Indicates whether the control is critical of not. If this field is non-zero, the operation will only be carried out if the control is recognized by the server and/or client.  Note that the LDAP unbind and abandon operations have no server response, so clients SHOULD NOT mark server controls critical when used with these two operations.<br>
</ul>



**See Also :**
[LDAP_CHASE_xxx](/domino-c-api-docs/reference/Symb/LDAP_CHASE_xxx)
[LDAP_CONTROL_xxx](/domino-c-api-docs/reference/Symb/LDAP_CONTROL_xxx)
---
